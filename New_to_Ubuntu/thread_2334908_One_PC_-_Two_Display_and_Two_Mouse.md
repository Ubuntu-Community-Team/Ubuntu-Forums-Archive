---
title: "One PC - Two Display and Two Mouse"
date: 2016-08-23
forum: New to Ubuntu
---

### Post by 1uone on 2016-08-23
Hello everybody,
Is there a way to set second mouse and tv display to work only on selected workspace.
I want to use my tv screen as second computer. first workspace for PC, second workspace for tv screen.

---

### Post by TheFu on 2016-08-24
It is possible to have multiple users connected and running on a single linux computer and has been for over a decade (maybe 2) - [http://linuxgazette.net/124/smith.html](http://linuxgazette.net/124/smith.html) - didn't do any more research than that. Don't know if 16.04 (or any systemd-based install) can easily do this.  I've used systems like this in programming classes.  We had 12 students connected to a single machine. Each "head" was running X/Windows.  "head" means keyboard, mouse, video and is usually tied to a different X/server instance.

I don't understand what you mean by the "selected workspace" ... since these will necessarily be different sessions, not the same login xsession.

---

### Post by mook765 on 2016-08-24
Interesting point.
You would need two pointers controlled by different mouses.
I was searching a bit and playing around, here is the output of my terminal ( I added some comments )
```

mook@MookPC:~$ xinput
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; G-Tech Wireless Dongle                    id=11   [slave  pointer  (2)]  <--- mouse #1
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Power Button                              id=8    [slave  keyboard (3)]
    &#8627; USB 2.0 Camera                            id=9    [slave  keyboard (3)]
    &#8627; G-Tech Wireless Dongle                    id=10   [slave  keyboard (3)]  <--- Keyboard #1
    &#8627; Eee PC WMI hotkeys                        id=12   [slave  keyboard (3)]
-----------------------------------------------------------------------------
Now i attache my second mouse to the usb-port
-----------------------------------------------------------------------------
mook@MookPC:~$ xinput
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; G-Tech Wireless Dongle                    id=11   [slave  pointer  (2)]  <--- Mouse #1
&#9116;   &#8627; 2.4G Receiver                             id=14   [slave  pointer  (2)]  <--- Mouse #2
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Power Button                              id=8    [slave  keyboard (3)]
    &#8627; USB 2.0 Camera                            id=9    [slave  keyboard (3)]
    &#8627; G-Tech Wireless Dongle                    id=10   [slave  keyboard (3)]  <--- Keyboard #1
    &#8627; Eee PC WMI hotkeys                        id=12   [slave  keyboard (3)]  <--- Keyboard #2
    &#8627; 2.4G Receiver                             id=13   [slave  keyboard (3)]
-----------------------------------------------------------------------------
At this point we have still one cursor, controlled by both mouses
Now  I create a new master
-----------------------------------------------------------------------------
mook@MookPC:~$ xinput create-master Pointer2
mook@MookPC:~$ xinput
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; G-Tech Wireless Dongle                    id=11   [slave  pointer  (2)]
&#9116;   &#8627; 2.4G Receiver                             id=14   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Power Button                              id=8    [slave  keyboard (3)]
    &#8627; USB 2.0 Camera                            id=9    [slave  keyboard (3)]
    &#8627; G-Tech Wireless Dongle                    id=10   [slave  keyboard (3)]
    &#8627; Eee PC WMI hotkeys                        id=12   [slave  keyboard (3)]
    &#8627; 2.4G Receiver                             id=13   [slave  keyboard (3)]
&#9121; Pointer2 pointer                              id=15   [master pointer  (16)] <---New Cursor
&#9116;   &#8627; Pointer2 XTEST pointer                    id=17   [slave  pointer  (15)]
&#9123; Pointer2 keyboard                             id=16   [master keyboard (15)] <---New Keyboard
    &#8627; Pointer2 XTEST keyboard                   id=18   [slave  keyboard (16)]
------------------------------------------------------------------------------
At this moment we have a second cursor, but only one curser is controlled by both mouses
Now I bind the mouse to the new cursor
------------------------------------------------------------------------------                                         
mook@MookPC:~$ xinput reattach 14 15                                                   
mook@MookPC:~$
------------------------------------------------------------------------------
Now we have each of the two cursors controlled by it's own mouse!!!!
```
Please refer to ```
man xinput
```as well.
That is maybe half the way. 
How to bind the pointers to the different workspaces you may try to find out, make some effort, use Google a lot, there is always a chance to find something useful...
Kind regards...
Edit:
Here is maybe a good place to start:
[https://en.wikipedia.org/wiki/Multiseat_configuration#GNU.2FLinux](https://en.wikipedia.org/wiki/Multiseat_configuration#GNU.2FLinux)

---

### Post by mastablasta on 2016-08-25
it would be a lot easier to just add a second computer. mini PC for example. or one of the cheap ARM boards on intel's computer on a USB stick.

---

### Post by 1uone on 2016-08-25
thanks for the all replies,

I am new to Linux. So what i asked is maybe silly for you sorry.

&#304; have searched for case on the net and found multi-seat but found a bit complicated.
Then  tried automseat with gdm3 but when i restart pc screen starts with  terminal not desktop. it was hard to get back normal start. had to find  find how to install mdm on terminal and luckly succeed :))

gave  up and tried to find other possible options. i asked if possible to set  workspaces an mouses to specific monitor and Tv. i would like to use  monitor and tv independently when mirroring via hdmi.

My system:
Linux Mint 18 Xfce
Ati Radeon HD 4200 (integrated)
AMD Athlon(tm) II X4 640 Processor

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Basic Optical Mouse               id=8    [slave  pointer  (2)]
&#9116;   &#8627; A4TECH USB Device                           id=9    [slave  pointer  (2)]
&#9116;   &#8627; A4TECH USB Device                           id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]

---

