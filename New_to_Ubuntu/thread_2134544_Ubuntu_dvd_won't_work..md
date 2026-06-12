---
title: "Ubuntu dvd won't work."
date: 2013-04-11
forum: New to Ubuntu
---

### Post by Smidthmador on 2013-04-11
I followed the instructions on ubuntu.org to burn and install the os.  I put the dvd in, rebooted and it kinda started to load windows I didn't even see an Ubuntu logo, it just did the normal Windows loading screen with the loading bar that goes around and around.  Then I got a black screen.  I had to restart and when I did it failed to do so, so I restarted again and I got the Windows repair screen, I did the repair and had to do restore to a save point.  

Why did this happen?


I wanted to do the live cd since I've never tried Linux before.

I asked on the IRC but I'm not sure if the answer applies to me as I don't even know if the commands from the article I was reffered to are for Windows or Linux...

All help appreciated! Thanks :D

---

### Post by arochester on 2013-04-11
Did you change the BIOS/Boot Order so it would boot from the CD-Rom first and before the Hard Drive?

---

### Post by Smidthmador on 2013-04-11
I did not, but what I am wondering is why it froze and had to recover.  My pc isn't hooked up n this one is my 'ma's.  I'm scared of messing things up.  Will this not happen if I change the boot order?

Thank you for your help

---

### Post by grahammechanical on 2013-04-11
May I explain? The Basic Input/Output System (BIOS) tells the computer about itself and where to find an operating system. We can change the setting so that the BIOS first looks for an operating system on a CD/DVD drive and then if it does not find one there it will next look on a hard disk. To speed up the loading of the operating system the BIOS is usually set to look first to the hard disk. But this will not allow us to load the Ubuntu live session. So we must change the boot order or priority in the BIOS.

By the way, what set of instructions on Ubuntu.com did you follow? Did you follow these instructions?

[http://www.ubuntu.com/download/help/install-ubuntu-with-windows](http://www.ubuntu.com/download/help/install-ubuntu-with-windows)

And what version of Windows is on this machine? Windows 8? Did you see this?

> [h=4]Windows installer is not compatible with Windows 8 or UEFI firmware.[/h]

We need to check to find out what we are dealing with. What are the specifcations of the machine and what version of Ubuntu are you trying to install?

Regards.

---

### Post by Smidthmador on 2013-04-11
I did not use those instructions as I do not yet know if I want to actually install this, I wanted to try a live cd.  This machine is a Vista home premium.  Also I did see that message, about 20x.. ;D

That worked.  Thank you! :D
..Now I just need to figure out how to change the resolution...

---

