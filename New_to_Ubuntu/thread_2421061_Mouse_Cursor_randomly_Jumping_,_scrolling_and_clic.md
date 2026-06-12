---
title: "Mouse Cursor randomly Jumping , scrolling and clicking corners"
date: 2019-06-15
forum: New to Ubuntu
---

### Post by chronic1337 on 2019-06-15
Hello i am using Ubuntu 19.04 since 2 days and cant fix my problem ....

i asked this in other forum but only got stupid answers ..... pls help i trying to fix this  for 2 days non stop

My Mouse (Razor Naga Trinity ) is randomly jumping , scolling and clicking things 80% the left bottm corner.

i tried to disable everything else exept the mouse with "xinput diable" but the error sill appears .

I tried a old cheep mouse and it worked .... so the problem is the mouse or the driver
i want to use the razor naga trinity


    ```
xinput list ::
 
    &#9121; Virtual core pointer                        id=2    [master pointer  (3)]
 
    &#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
 
    &#9116;   &#8627; Razer Razer Naga Trinity                    id=8    [slave  pointer  (2)]
 
    &#9116;   &#8627; Razer Razer Cynosa Chroma                   id=15    [slave  pointer  (2)]
 
    &#9116;   &#8627; Razer Razer Cynosa Chroma                   id=14    [slave  pointer  (2)]
 
    &#9116;   &#8627; Razer Razer Naga Trinity Consumer Control    id=10    [slave  pointer  (2)]
 
    &#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
 
        &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
 
        &#8627; Power Button                                id=6    [slave  keyboard (3)]
 
        &#8627; Power Button                                id=7    [slave  keyboard (3)]
 
        &#8627; Razer Razer Cynosa Chroma                   id=13    [slave  keyboard (3)]
 
        &#8627; Razer Razer Cynosa Chroma                   id=17    [slave  keyboard (3)]
 
        &#8627; Razer Razer Naga Trinity Consumer Control    id=16    [slave  keyboard (3)]
 
        &#8627; Razer Razer Naga Trinity                    id=12    [slave  keyboard (3)]
 
        &#8627; Razer Razer Naga Trinity System Control     id=11    [slave  keyboard (3)]
 
        &#8627; Razer Razer Naga Trinity Keyboard           id=9    [slave  keyboard (3)]


Ev Test ::

    Input driver version is 1.0.1
 
    Input device ID: bus 0x3 vendor 0x1532 product 0x67 version 0x111
 
    Input device name: "Razer Razer Naga Trinity"
 
    Supported events:
 
      Event type 0 (EV_SYN)
      Event type 1 (EV_KEY)
        Event code 272 (BTN_LEFT)
        Event code 273 (BTN_RIGHT)
        Event code 274 (BTN_MIDDLE)
        Event code 275 (BTN_SIDE)
        Event code 276 (BTN_EXTRA)
 
      Event type 2 (EV_REL)
        Event code 0 (REL_X)
        Event code 1 (REL_Y)
        Event code 8 (REL_WHEEL)
        Event code 11 (?)
 
      Event type 4 (EV_MSC)
        Event code 4 (MSC_SCAN)
    Properties:
    Testing ... (interrupt to exit)
 
 
    Event: time 1560615536.365773, -------------- SYN_REPORT ------------
    Event: time 1560615537.776746, type 2 (EV_REL), code 1 (REL_Y), value 1
 
    Event: time 1560615537.776746, -------------- SYN_REPORT ------------
    Event: time 1560615537.792715, type 2 (EV_REL), code 1 (REL_Y), value 1
 
    Event: time 1560615537.792715, -------------- SYN_REPORT ------------
    Event: time 1560615537.798779, type 2 (EV_REL), code 0 (REL_X), value -1
 
    Event: time 1560615537.798779, -------------- SYN_REPORT ------------
    Event: time 1560615537.811681, type 2 (EV_REL), code 1 (REL_Y), value 1
 
    Event: time 1560615537.811681, -------------- SYN_REPORT ------------
    Event: time 1560615537.838691, type 2 (EV_REL), code 1 (REL_Y), value 1
 
    Event: time 1560615537.838691, -------------- SYN_REPORT ------------
    Event: time 1560615538.188732, type 2 (EV_REL), code 0 (REL_X), value -1
 
    Event: time 1560615538.188732, -------------- SYN_REPORT ------------
    Event: time 1560615541.244669, type 2 (EV_REL), code 0 (REL_X), value -1

!!!!!!!!!!!!!!! bug starts here !!!!!!!!!!!!!!!!

    Event: time 1560615541.244669, -------------- SYN_REPORT ------------
    Event: time 1560615541.500577, type 4 (EV_MSC), code 4 (MSC_SCAN), value 90001
    Event: time 1560615541.500577, type 1 (EV_KEY), code 272 (BTN_LEFT), value 1
    Event: time 1560615541.500577, type 2 (EV_REL), code 8 (REL_WHEEL), value 32
    Event: time 1560615541.500577, type 2 (EV_REL), code 11 (?), value 3840
    Event: time 1560615541.500577, type 2 (EV_REL), code 0 (REL_X), value 8195
    Event: time 1560615541.500577, type 2 (EV_REL), code 1 (REL_Y), value 3
 
    Event: time 1560615541.500577, -------------- SYN_REPORT ------------
    Event: time 1560615541.596593, type 4 (EV_MSC), code 4 (MSC_SCAN), value 90001
    Event: time 1560615541.596593, type 1 (EV_KEY), code 272 (BTN_LEFT), value 0
    Event: time 1560615541.596593, type 2 (EV_REL), code 8 (REL_WHEEL), value 8
    Event: time 1560615541.596593, type 2 (EV_REL), code 11 (?), value 960
    Event: time 1560615541.596593, type 2 (EV_REL), code 0 (REL_X), value 7
    Event: time 1560615541.596593, type 2 (EV_REL), code 1 (REL_Y), value -27648
 
    Event: time 1560615541.596593, -------------- SYN_REPORT ------------
    Event: time 1560615541.678661, type 4 (EV_MSC), code 4 (MSC_SCAN), value 90001
    Event: time 1560615541.678661, type 1 (EV_KEY), code 272 (BTN_LEFT), value 1
    Event: time 1560615541.678661, type 4 (EV_MSC), code 4 (MSC_SCAN), value 90005
    Event: time 1560615541.678661, type 1 (EV_KEY), code 276 (BTN_EXTRA), value 1
    Event: time 1560615541.678661, type 2 (EV_REL), code 0 (REL_X), value 10240
    Event: time 1560615541.678661, type 2 (EV_REL), code 1 (REL_Y), value 10275
 
    Event: time 1560615541.678661, -------------- SYN_REPORT ------------
    Event: time 1560615541.720619, type 4 (EV_MSC), code 4 (MSC_SCAN), value 90002
    Event: time 1560615541.720619, type 1 (EV_KEY), code 273 (BTN_RIGHT), value 1
    Event: time 1560615541.720619, type 4 (EV_MSC), code 4 (MSC_SCAN), value 90005
    Event: time 1560615541.720619, type 1 (EV_KEY), code 276 (BTN_EXTRA), value 0
    Event: time 1560615541.720619, type 2 (EV_REL), code 8 (REL_WHEEL), value -128
    Event: time 1560615541.720619, type 2 (EV_REL), code 11 (?), value -15360
    Event: time 1560615541.720619, type 2 (EV_REL), code 0 (REL_X), value -32706
    Event: time 1560615541.720619, type 2 (EV_REL), code 1 (REL_Y), value 62
 
    Event: time 1560615541.720619, -------------- SYN_REPORT ------------
    Event: time 1560615541.958545, type 4 (EV_MSC), code 4 (MSC_SCAN), value 90001
    Event: time 1560615541.958545, type 1 (EV_KEY), code 272 (BTN_LEFT), value 0
    Event: time 1560615541.958545, type 4 (EV_MSC), code 4 (MSC_SCAN), value 90002
    Event: time 1560615541.958545, type 1 (EV_KEY), code 273 (BTN_RIGHT), value 0
```

---

### Post by #&amp;thj^% on 2019-06-15
Give us this also please:
```
lsmod |grep -i razermouse
```
And just a friendly suggestion, please don't use terms like **"but only got stupid answers"** as they will not help your cause.
Users on linux forums are just volunteers and not _paid help_. ;)

---

### Post by chronic1337 on 2019-06-15
1. thx for the fast answer 
and i know ii am rude but you dont know how offensive the people were in the askubuntu forum ... they called me a idiot just becouse i am a new ubuntu user ..... they didnt even try to answer my question  .

2. " lsmod |grep -i razermouse " i dont uderstand what i must du with this ... like i sad i am using ubutu since 2  days before i used windows

---

### Post by wildmanne39 on 2019-06-15
Hello and welcome to the forum, I hope you have better luck here, I do recommend taking a look at the forum rules located at:

[https://ubuntuforums.org/misc.php?do=showrules](https://ubuntuforums.org/misc.php?do=showrules)

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by him610 on 2019-06-16
>  " lsmod |grep -i razermouse " i dont uderstand...
1fallen is asking for you to show the results of *lsmod |grep -i razermouse* when run from the command line in a terminal window (between the code lines.) For example:
```
$ lsmod |grep bluetooth
bluetooth             548864  48 btrtl,hidp,btintel,btbcm,bnep,btusb,rfcomm

```
While you are at it, be sure to include the command itself as well as the results - it helps those who would offer advice.

---

### Post by #&amp;thj^% on 2019-06-16
The Razer Naga 2014 is a great mouse for gaming. Occasionally, it does run into some tracking and pointer jumping problems.
I'm wondering if you have tried to download the right driver for your newish (New to linux) mouse.
Driver found here: [https://openrazer.github.io/](https://openrazer.github.io/)
Front-ends and utilities are also available.
This also allows the drivers to stay up-to-date when new versions are released.(When adding the PPA below)

Stable builds are recommended:
```
sudo add-apt-repository ppa:openrazer/stable
```
After adding the PPA, install the packages:
Run the below one line at a time:
 ```
sudo apt update
```
 ```
sudo apt install openrazer-meta
```

If you get dependency errors when trying to install the driver packages please make sure that you have enabled the "universe" repository in Software & Updates

**_After the drivers are installed, please restart the computer._**

This PPA supports these versions:
[list]
    [*]Ubuntu 16.04 (Xenial) and newer
    [*]Linux Mint 18 and newer[/list]
Good Luck, and also Welcome to UF. :)

---

### Post by #&amp;thj^% on 2019-06-18
Did we lose you?, would like some feed back here.

---

