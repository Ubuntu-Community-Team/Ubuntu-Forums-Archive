---
title: "Green writing when installing Ubuntu Bootable"
date: 2013-06-25
forum: New to Ubuntu
---

### Post by Jacques Steventon on 2013-06-25
Hello,

I am installing Ubuntu on a Satellite Pro I300. When finished downloading I made a bootable dvd and placed the dvd into the optical drive on the laptop. I booted from the dvd drive and everything was running fine. When it started to read the DVD a purple screen came up with a picture at the bottom which looks like a man pointing at a keyboard and then from the top down lots of numbers and lettings in green starting coming onto the screen. You cannot make out the numbers or letters apart from what looks like the word error. 

I thought that maybe parts of the file had been corrupted when downloading so I re-downloaded the file. The same happened again. I went on to thinking this could be down to the dvd speed so I made a bootable USB drive. After making the USB bootable and plugging it in the same thing happened again.

Sadly the laptop I have been given doesn't run windows anymore so I cannot boot from windows and so I will need a bootable disk or USB drive. 

Question: Does anybody know what has happened and/or how to resolve this?

Many Thanks in advance,

Jacques

---

### Post by dino99 on 2013-06-25
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221](http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221)

---

### Post by grahammechanical on 2013-06-25
That purple screen is a splash screen to give the user time to select a different way of running the live session or installing Ubuntu. After a period of time during which the hardware is assessed another purple screen should appear with the word "Ubuntu" and four or five dots that cycle from white to red to indicate that something is working. Then in time a Ubuntu desktop should appear.

That is not happening in your case and the live session is going into a mode that shows all the messages as the operating system is being loaded. Or as the operating system attempts to load.

Without knowing what that error message is, it is hard to determine what the problem is. Also you do not tell us what version of Ubuntu you have. We would also like some specifications of the hardware. It all helps. I can only make a suggestion.

1) At the first purple screen (with keyboard and human icons) press Enter.
2) At the next screen press Enter to select English as the default language or select another language and press Enter.
3) You will now be at a screen that has TRY UBUNTU and INSTALL UBUNTU among the options.
4) Press F6 a small menu will appear. Look to the bottom right. Scroll done the list and select nomodeset and press Enter to put an x against the selection.
5) Press Esc to get back to the TRY - INSTALL screen and make sure that TRY UBUNTU is selected and press Enter.

See what happens. There are other options on that F6 menu sometimes we need to select a combination of the menu options to get a live session running.

Linux distributions have to try to be a "one size fits all" product and that is not possible due to the great variation in hardware. These F6 options are one way to work around these problems.

Regards.

---

