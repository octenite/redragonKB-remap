Remap any key , including FN ,modifying and adding keys to  FN layer

Read instructons to determine if your keyboard supports this method

Instuctions explain how to use the K-MAP and Hex Output files for
making your very own custom remap of keys by modifying the cfg.ini file
(cfg.ini is located in the installation directroy of your keyboard software)

The modifications are applied through the software provided
by the manufacturer (check out 'how to' in instructions )

Personally tested on Redragon k617!
I have provided modified cfg file for K617 adding
media keys and remappig FN

# Compatible keyboards

 -HK gaming GK61

 -Eyooso Z-11(redragon k617 clone , cross compatible  cfg files and software)

 -cosmic  byte themis

 -(any keyboard with software using described cfg.ini file below)

 **NOTE:**
 Most of these keyboards use BYK916/SH68F90A MCU , the provided OEM softwares are all almost similar with a changed Skin on top. Although few of them I belive use a totally different firmware (like RD K630?) and are not compatable with this approach. There is the [SMK](https://github.com/carlossless/smk) Project for such Keyboards and the boards using BYK916 / BYK901 / SH68F90A MCU in general. It aims to add much greater functionality by flashing a custom firmware. Do take a backup of the MCU Flash contents before proceeding using [sinowealth-kb-tool](https://github.com/carlossless/sinowealth-kb-tool).

# Instructions

<details>
    <summary><b><h3>REQUIREMENTS</b></h3></summary>
    <br>
1. A 'supported' keyboard<br>
2. A pc<br>
3. a regular human Brain<br>
4. lots Patience
<details>
     <summary><h5>supported keyboards</h5></summary>

As far as I have discovered and know , all the budget keyboards that come with a software have a high
probability of working with the method described in the 'How to' . you willneed to check if your keyboard
has the similar working method and cfg.ini file or any other similar filewiththe described structure of mapping
in the installation folder of the software.
I have looked through few keyboard softwares including-

1. Redragon fizz k617 ( personally tested on , has a MCU "BYK916" on the PCB)
2. eyooso Z-11 ( clone of k617, uses the same board, cross compatible cgf files and software with the redragon k617)
3. HK gaming GK61 ( optical one , has same cfg.ini file with same structure , imported the media keys & vol up/dn/mute hex codes from this KBs cfg file)
4. CosmicByte themis (probaly some generic chinese clone board , with their modified software) <br>

all these keyboard software uses the described cfg.ini structure and mapping format
My guess would be that this method should work with any GK6X and SK6X keyboard , only way to fnd out is to modify,try and test further.

</details>

</details>

<details>
    <summary><h3>HOW TO</h3></summary>

To remap the keyboard keys we will require

1. To know which physical key on keyboard to remap</br>
    the physical key Number is denoted by the "Kxx" in the K-MAP file

2. To provide the desired output/action for the key using its corresponding Hex code</br>
    The hex codes for output/action is listed in the hex output file
3. Locate the "cfg.ini" file and edit it </br>
    its located in the install directory of the keyboard software
4. Apply the new mapping configs of the cfg.ini using the OEMs provided software

First we take the keys K value and equal it to the hex value for the desired action by editing the cfg.ini file.A specific format must be followed for the mapping to be valid and recognised by the software in the config file.

<details>
<summary><h4>BASIC FORMAT/STRUCTURE OF "cfg.ini" FILE</h4></summary>
<br>

the 'cfg.ini' is found in installation directory of KB software <br>

##### cfg.ini file FORMAT example:-

<pre>

##START OF FILE

[OPT]       || these are some vendor specific configs listing KB name , model , firmware version
            || rgb modes, speed , ect ect . none of our business . DO NOT MODIFY these.
            || These are vendor specific , and mosty not cross compatible configs(eyooso z11 & redragon fizz are cross compatible)
            || SO...when making a cfg.ini file always use the stock [OPT] data

[FN]               ||lists the mappings of the FN layer
;Esc               || this line is for indicative purpose and does not influence mapping
K1=0x02,0xC0,0x00  || this is the main mapping data,  format "{K value}={hex value}"
;1                 ||
K2=0x02,0x70,0x00  ||mappings must be in serial order ie. K1,K2,K3,K4......K61
;2
K3=0x02,0x71,0x00
;3
K4=0x02,0x72,0x00
;4
K5=0x02,0x73,0x00
;XXXX
KXXX=0xXX,0xXX,0xXX
.................. continues (you can add/modify as many FN keys as you like )

[KEY]                                   || Lists the mappings of the main layer
;Esc                                    || it is for indicative purpose and does not influence mapping
K1=17,10,41,38, 0x02,0x1B,0x00,1,21     || this is the mapping format "{K value}={hex value}"
;1                                      ||
K2=55,10,79,38, 0x02,0x31,0x00,7,22     || mappings must be in serial order ie. K1,K2,K3,K4......K61
;2                                      ||
K3=92,10,116,38, 0x02,0x32,0x00,13,23   || we are only concerned about the middle hex codes DO NOT modify/remove the other numbers before and after the hex codes
;3                                      ||
K4=129,10,153,38, 0x02,0x33,0x00,19,24  || the numbers 4 numbers before hex and 2 after hex , idk wahat they do, my guess is they are mostly specific to each vendor/model so do not change
;4                                      || them , these are only found in the [KEY] main layer mappings . so your KB already has these for all the 61 keys
K5=167,10,191,38, 0x02,0x34,0x00,25,25
;XXXX
KXXX=0xXX,0xXX,0xXX
..................
K61=0xXX,0xXX,0xXX
## END OF FILE
--------------------------
</pre>
</details>

<details>
    <summary><h4>EDITING THE cfg.ini</h4></summary>
Go to your keyboard softwares installation directory and look for the cfg.ini file.
If the file has the above format then you can proceed to modifying the file.Save a backup copy of the file before editng.
Modify it according to the instuctions above as per your choice of keys and desired output
after edidting the mappings in the cgf.ini file we will apply it using the software provided
do take a backup of your stock cgf.ini in case u need to reset back to stock<br>
<br>
<b>Example:</b>
    If you need to remap CAPSLOCK as FN. You find K no. of capslock (which is K29) , edit the K29 in the main layer to the Hex values of FN (which is 0x02,0xFA,0x00) <br>
    In the file it looks like this

        ;CAPSLOCK_FN
        K29=0x02,0xFA,0x00
</details>

<details>
    <summary><h4>APPLYING THE CONFIGS</h4></summary>

These softwares are very generic and are mostly copy pasta of one another with few modifications across models
In these software we are looking for buttons "RESTORE" & "APPLY"

pressing 'APPLY'   will NOT apply the configs already made into the cgf.ini
pressing 'RESTORE' WILL restore the keyboard mappings using the cfg.ini mapping data
So,after editing the cfg file we will open the app and press the restore button
after using RESTORE , you should have your mappings applied to your keyboard.

</details>

</details>

<details>
<summary><h3>KNOWN ISSUES</h3></summary>

FN REMAPPING EXCEPTION -

While FN can be remapped to any key , we need to make sure that the key we are remapping FN to (in the main layer to activate FN layer) does not have a corresponding action on the FN layer itself.
If it does,keyboard will fail to switch to FN, as pointed out in Issue [#3](https://github.com/octenite/redragonKB-remap/issues/3).
So make sure that the FN key does not have any mappings in the FN layer,if it does remove it.

SOME KEYS NOT WORKING - 

I came across an issue where the K60(default APP key on Redragon K617) was not working .The issue is in buggy mapping numbers in  cfg ini. Using the latest available software fixed the issue.
The change that fixed it - 

From
<pre>
;App
K60=468,160,501,188, 0x02,0x5D,0x00,65,115

</pre>
To
<pre>
;App
K60=468,160,501,188, 0x02,0x5D,0x00,77,117
</pre>
SOMETHING WENT WRONG? - Restore back to Stock settings

If the mappings are not edited correctly or conflicts , sometimes for some weird reasons some keys may have null output ( as if its dead)
if such things happen , restore the stock cfg.ini (well if you didn't take a backup before hand dont worry , just reinstall the software , it comes with the stock cfg.ini).
After replacing your frankenstein cfg.ini with the stock one and RESTORE using the software.
Using reset key combo(specific to each keyboard) will also restore the keyboard to stock condition (hold FN+ESC in case of redragon fizz k617).

</details>

#

### 60% keyboard K-map

<img src=K-MAP.png>

<details>
    <summary><h3><b>Key Hex Codes</b></h3></summary>
Similar Hex codes as in Win32 api <a href="https://learn.microsoft.com/en-us/windows/win32/inputdev/virtual-key-codes" target="_blank"> Virtual-Key Codes </a>
    <div style="max-height: 600px; overflow-y: auto; margin-top: 10px;">
format:-
{key action/output}={hex code}  

<a href= "Hex outputs.txt"> Key Wise Sorting of the below Codes </a>

<pre>
>0x02 PREFIX HID FUNCTIONS

>0x10------

shift=0x02,0x10,0x00

CTRL=0x02,0x11,0x00

ALT=0x02,0x12,0x00

PAUSE/BREAK=0x02,0x13,0x00

CapsLock=0x02,0x14,0x00

Esc=0x02,0x1B,0x00

>0x20------

Space=0x02,0x20,0x00

PGUP=0x02,0x21,0x00

PGDN=0x02,0x22,0x00

END=0x02,0x23,0x00

HOME=0x02,0x24,0x00

LEFT ARROW=0x02,0x25,0x00

UP ARROW=0x02,0x26,0x00

RIGHT ARROW=0x02,0x27,0x00

DOWN ARROW=0x02,0x28,0x00

PRINTSCREEN=0x02,0x2C,0x00

INSERT=0x02,0x2D,0x00

DELETE=0x02,0x2E,0x00

>0x30------

0=0x02,0x30,0x00

1=0x02,0x31,0x00

2=0x02,0x32,0x00

3=0x02,0x33,0x00

4=0x02,0x34,0x00

5=0x02,0x35,0x00

6=0x02,0x36,0x00

7=0x02,0x37,0x00

8=0x02,0x38,0x00

9=0x02,0x39,0x00

>0x40------

A=0x02,0x41,0x00

B=0x02,0x42,0x00

C=0x02,0x43,0x00

D=0x02,0x44,0x00

E=0x02,0x45,0x00

F=0x02,0x46,0x00

G=0x02,0x47,0x00

H=0x02,0x48,0x00

I=0x02,0x49,0x00

J=0x02,0x4A,0x00

K=0x02,0x4B,0x00

L=0x02,0x4C,0x00

M=0x02,0x4D,0x00

N=0x02,0x4E,0x00

O=0x02,0x4F,0x00

>0x50------

P=0x02,0x50,0x00

Q=0x02,0x51,0x00

R=0x02,0x52,0x00

S=0x02,0x53,0x00

T=0x02,0x54,0x00

U=0x02,0x55,0x00

V=0x02,0x56,0x00

W=0x02,0x57,0x00

X=0x02,0x58,0x00

Y=0x02,0x59,0x00

Z=0x02,0x5A,0x00

LWin=0x02,0x5B,0x00

WIN=0x02,0x5C,0x00

MENU/APP KEY=0x02,0x5D,0x00

>0x60-------

NUM 0 =0x02,0x60,0x00

NUM 1 =0x02,0x61,0x00

NUM 2 =0x02,0x62,0x00

NUM 3 =0x02,0x63,0x00

NUM 4 =0x02,0x64,0x00

NUM 5 =0x02,0x65,0x00

NUM 6 =0x02,0x66,0x00

NUM 7 =0x02,0x67,0x00

NUM 8 =0x02,0x68,0x00

NUM 9 =0x02,0x69,0x00

NUM * =0x02,0x6A,0x00

NUM + =0x02,0x6B,0x00

NUM - =0x02,0x6D,0x00

NUM . =0x02,0x6E,0x00

NUM / =0x02,0x6F,0x00

>0x70------

F1=0x02,0x70,0x00

F2=0x02,0x71,0x00

F3=0x02,0x72,0x00

F4=0x02,0x73,0x00

F5=0x02,0x74,0x00

F6=0x02,0x75,0x00

F7=0x02,0x76,0x00

F8=0x02,0x77,0x00

F9=0x02,0x78,0x00

F0=0x02,0x79,0x00

F11=0x02,0x7A,0x00

F12=0x02,0x7B,0x00

>0x80------

BACKSPACE=0x02,0x8,0x00 / 0x02,0x08,0x00

>0x90------

NUMLOCK = 0x90

SCROLL LOCK =0x91

TAB=0x02,0x9,0x00 / 0x02,0x09,0x00

>0xA0------

LSHIFT = 0x02,0xA0,0x00

RSHIFT = 0x02,0xA1,0x00

RCTRL = 0x02,0xA3,0x00

LCTRL = 0x02,0xA2,0x00

LALT = 0x02,0xA4,0x00

RALT = 0x02,0xA5,0x00

>0xB0------

; = 0x02,0xBA,0x00

= = 0x02,0xBB,0x00

, = 0x02,0xBC,0x00

-= 0x02,0xBD,0x00

. = 0x02,0xBE,0x00

/ = 0x02,0xBF,0x00

>0xC0------

` = 0x02,0xC0,0x00

>0xD0------

ENTER = 0x02,0xD,0x00 / 0x02,0x0D,0x00

[ = 0x02,0xDB,0x00

] = 0x02,0xDD,0x00

\ = 0x02,0xDC,0x00

' = 0x02,0xDE,0x00

>0xE0------

\ = 0x02,0xE2,0x00

>0xF0------

FN=0x02,0xFA,0x00

NUM ENTER = 0x02,0xFD,0x00

>0x04 PREFIX AND OTHER OEM/VENDOR FUNCTIONS----------------------

{Will be mapped to FN layer , but can be mapped to main layer too}

MEDIA = 0x04,0x21,0x00

PAUSE MEDIA = 0x04,0x22,0x00

STOP MEDIA = 0x04,0x23,0x00

PREVIOUS MEDIA = 0x04,0x24,0x00

NEXT MEDIA = 0x04,0x25,0x00

VOLUME UP = 0x04,0x26,0x00

VOLUME DOWN = 0x04,0x27,0x00

MUTE MEDIA = 0x04,0x28,0x00

>0x09 PREFIX OEM/VENDOR SPECIFIC KEYBOARD LOCAL SETTINGS FUNCTIONS

WHITE BACKLIT [CUSTOM FUNCTION of k617] = 0x09,0x00,0x0e000006

LOCK WINDOWS KEY = 0x09,0x00,0x0e000001

RESET KEYBOARD [CUSTOM FUNCTION] = 0x09,0x00,0x0b000300

CHANGE BACKLIT BRIGHTNESS[CUSTOM FUNCTION] = 0x09,0x00,0x0c000300

CHANGE BACKLIT COLOR[CUSTOM FUNCTION] = 0x09,0x00,0x0e000007

CHANGE BACKLIT RGB MODE[CUSTOM FUNCTION] = 0x09,0x00,0x0d000300  
</pre>
</div> </details>
