---
title: "Grub Problems"
date: 2014-03-02
forum: New to Ubuntu
---

### Post by doubled2 on 2014-03-02
Hello all...I am totally new to Ubuntu, and recently partitioned my hard drive to dual boot with Ubuntu and Windows. I am running 64 bit Windows 7 and Ubuntu, I have 2 hard drives on my PC (70GB and 500GB). The issue I am having is when I start up my computer and the screen goes to the Grub menu...I am unable to move up and down the list of boot options using the keyboard, therefore I am unable to select the operating system to boot up with. I tried using a different keyboard with negative results, has anyone heard of this or know of a fix for the problem? Thank you

---

### Post by jdeca57 on 2014-03-02
Yes, that is a problem I once had with a usb keyboard. Most PC's only activate a few selected usb ports at startup, the time grub is in effect. The problem is not the keyboard, but the port you use. Try other ports, if you have legacy PS/2 support they should be in vicinity.

---

### Post by doubled2 on 2014-03-02
OK thanks...I am going to try that and will let you know my results :)

---

### Post by Bashing-om on 2014-03-02
doubled2; Hey.

Additionally, one might check in BIOS settings and see what can be readjusted for the usb/keyboard devices.
(BIOS hands off to grub what it has for hardware settings )

[INDENT]my little bit 
[INDENT][INDENT]to try and help
[/INDENT][/INDENT][/INDENT]

---

### Post by doubled2 on 2014-03-02
OK, I tried all the different USB ports and that didn't work :( 

Bashing-om, I will try looking in my BIOS settings...anything in particular I should adjust?

---

### Post by Bashing-om on 2014-03-02
doubled2; Welp.

There are so many different Bios' - each one different, can not directly advise. If ya look "generally" and find nothing of note, ya might google your bios and version for the OEM's manual. See then what ya find.
> 
I can confirm that "some" mother boards don't like a USB keyboard on the install disk. ...and not all BIOS'es will pick up a USB keyboard in post. USB support on the motherboards has layers... So you have more of a chance on picking up USB keyboard through one of the USB root hub ports than through the second layer or an extension...Those root ports are normally on the back of the motherboard, near the keyboard/mouse PS2 ports. Usually ports on the front of a PC are on a higher layer or on an extension. But those same ports do pick up when the kernel boots through the HID drivers.


In any event, let us know how it goes.

[INDENT]we help
[INDENT][INDENT][INDENT]all we can
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by doubled2 on 2014-03-04
Bashing-om...you sir are a life saver!!! I finally sat down and played with the bios and it now works :) I will give a brief description of what I did to fix it, first I will let you know I have a Gigabyte S-Series Motherboard (I know it's old, but it still works). Anywho, I entered the bios and went to "integrated perephials" after that I noticed a selection for USB Keyboard Support was set to "disabled"...I then changed that to "enabled"...saved and exited bios....restarted computer and WALLAAAAAA it is working!!! 

Now I just have to learn how to use Ubuntu for everything else LOL Would you recommend any tweaks, or starter things to do?

Thanks

---

### Post by Bashing-om on 2014-03-04
doubled2; Great !

You are up and doing ! Glad I was able to help.

Please mark this thread solved; 1st post -> thread tools : aids others seeking a similar solution and helps keep the forum tidy.

As to what to do with a wonderful operating system, your system will be as individualistic as there are individuals in the 'buntu world.

It all depends on what you do and how you do it !

Start reading to learn, exploring and follow your curiosity. Start with the stickies within the forum, particularly those in "Absolute Beginners Section" and the greatest asset is the link in my sig - PopularPages - !
[http://files.ubuntu-manual.org/manuals/getting-started-with-ubuntu/12.10/en_US/screen/Getting%20Started%20with%20Ubuntu%2012.10.pdf](http://files.ubuntu-manual.org/manuals/getting-started-with-ubuntu/12.10/en_US/screen/Getting%20Started%20with%20Ubuntu%2012.10.pdf)

[http://ubuntuforums.org/showthread.php?t=2125370](http://ubuntuforums.org/showthread.php?t=2125370) <-ubuntu ain't Windows, DuckHook treatsie.

And foremost is always here on the forum. The only dumb question is the one that is not asked ! There is no one way to do anything. Just do it your way. And ReMbeR -> uncle Google is your friend, but beware, what used to be, used to be. The operating system is constantly evolving - one must learn what is now relevant.

[INDENT]and then
[INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT][/INDENT]

---

### Post by doubled2 on 2014-03-04
Thank you very much for the help and the links...time to do some research!!

---

