---
title: "My PC can't read my USB booted drive"
date: 2018-02-01
forum: New to Ubuntu
---

### Post by alexakos121 on 2018-02-01
I have windows 7 64 bit and i wanted to install ubuntu alongside windows. I downloaded ubuntu, made my usb bootable but still my pc cant recognize it and i cant install it any help?

---

### Post by yancek on 2018-02-01
Post some info on the hardware you are trying to install to and how did you create the 'bootable' usb which doesn't boot?  Did you set the usb to first boot priority in the BIOS?  More specifics on what you did and what happened if you want help.

---

### Post by C.S.Cameron on 2018-02-01
UNetbootin is probably the easiest way to make a Live USB in Windows for installing Ubuntu.

---

### Post by alexakos121 on 2018-02-02
First of all my USB is an Transcend 3.0 32Gb, I used Rufus to create my 'bootable' USB and my hardware is CPU : AMD Fx- 6000 , Ram : 8GB , Motherboard : Gigabyte GA-78LMT-USB3 6.0 , GPU : AMD Radeon R7 200 , OS : Windows 7 Ultimate 64 bit and the OS i want to install is Ubuntu latest version 17.10 .

---

### Post by yancek on 2018-02-02
Rufus usually works alright to create a bootable usb so what exactly happens?  Doesn't recognize it, does that mean nothing shows on boot, you get a black screen or something else?  Is the usb recognized in the BIOS?  Can you test it on another machine to see if it boots?

---

### Post by alexakos121 on 2018-02-02
So i restart my PC and i press F12 which is the boot menu and this picture appears i've selected all the lines but nothing happens it just goes to windows.
                                                                                                                        [http://i65.tinypic.com/29zyhar.jpg](http://i65.tinypic.com/29zyhar.jpg) (select this if 1st one doesnt work)

---

### Post by C.S.Cameron on 2018-02-03
In BIOS can you make your flash drive the first hard drive?

---

### Post by alexakos121 on 2018-02-03
I can make USB-FDD  or USB-HDD first which i've already tried that but still nothing happened

---

### Post by leunam12 on 2018-02-03
Do you see that plus symbol next to "Hard Disk"? It means that the option to boot from the USB drive is hiding there. Try to select it and see if pressing the "right arrow" on your keyboard expands it and allows you to select the usb drive. If you cannot expand it from that temporary boot menu, you have to go to BIOS to "boot order options" and select hard drive and make the change so the USB drive is first. (the USB drive has to be inserted, of course).

---

### Post by alexakos121 on 2018-02-03
I pressed the plus symbol next to the "Hard Disk" and this appeared i also pressing the right arrow did nothing   [http://i63.tinypic.com/119a5n7.jpg](http://i63.tinypic.com/119a5n7.jpg)






Also i changed the boot order to:     [http://i67.tinypic.com/2dvrkwj.jpg](http://i67.tinypic.com/2dvrkwj.jpg)

---

### Post by wildmanne39 on 2018-02-03
Please use thumbnails or url's when posting images because many people have slow or limited connections.

---

