---
title: "Black Screen on boot from USB with error messages showing and same sound playing loop"
date: 2015-09-29
forum: New to Ubuntu
---

### Post by elliot8 on 2015-09-29
So when booting into a USB with Ubuntu 14.04.3 LTS this happens, same result when clicking try live and install. 
Asus H81M-E motherboard, i5 4690k CPU

[https://youtu.be/RdpscuRJQPA](https://youtu.be/RdpscuRJQPA)

---

### Post by Geoffrey_Arndt on 2015-09-30
Do you  have proprietary video hardware on the pc?   nVidia and ati drivers are not pre-installed in Linux as they are closed, locked binaries and therefore not merged into the Ubuntu kernel like Intel video is.

So, there is a line in the bootloader that the "nomodeset" option has to be added, so pc will not attempt to load generic video drivers which fail.   You want to invoke basic "vesa" video support (which nomodest will do).

Then, after booting - typically you'll get a lower res screen (often 800 x 600) or (1024 x 768) depending on system.    This will now allow you to go to "System Settings>Software & Updates>Additional Drivers (it's a tab in Software Updates).

.............................................................................................................................................

 To enable boot via "nomodeset" grub option" 
   

[LIST]
[*]Boot the machine and at the grub menu highlight the kernel you want to use and click 'e' to edit. 
[/LIST]

Find the line that ends in 'quiet splash' and after a space, add 'nomodeset'.   The end of the line should look like this: 
[LIST] 
[/LIST]
    quiet splash nomodeset 
   

[LIST]
[*]Follow the instructions at the bottom of that screen to save changes and continue
[/LIST]

...................................................................................................................................................

For future reference - - these kind of "fubar's" are completely  avoidable  . . . . if when considering a new PC purchase (laptop,  desktop) . . . 
just avoid the "big-box" stores where Linux devices are not available & instead check out:  [http://linuxpreloaded.com/](http://linuxpreloaded.com/)

---

