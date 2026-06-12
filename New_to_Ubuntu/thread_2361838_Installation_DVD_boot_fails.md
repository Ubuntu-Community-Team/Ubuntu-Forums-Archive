---
title: "Installation DVD boot fails"
date: 2017-05-21
forum: New to Ubuntu
---

### Post by magiwanders on 2017-05-21
Good day everyone. I encountered some troubles during the installation of Ubuntu Gnome 17.04 alongside Windows on my Laptop: here are the details:

Dell Inspiron 15 7559 (2015)
 - Intel i7 6700hq
 - Nvidia 960m
 - 8gb RAM
 - 250gb Intel SSD of which more than 120GB free.

 - I burnt the 64bit .iso on a re-writable dvd
 - I checked BIOS settings as suggested on the installation guide
 - I booted from the DVD and whether I select "try Ubuntu Gnome" or "Install" the following things happen:

[ATTACH=CONFIG]275199[/ATTACH]

Is anyone able to help me? I have tried many possible bios setting but it just gives me the same error all the times. Can't really understand if the processor thing is a hardware or software problem. 

I am new to ubuntu but something in the universe is even preventing me from installing it!

Thanks in advance, Magi

---

### Post by RobGoss on 2017-05-21
Hello and welcome to the forums, I don't think it's hardware problem Dells handle Linux quite well, I run a number of machines and they are all Dells with out any problems

Is this a dual boot setup you're trying to install?

Have you tried accessing your BIOS and set your DVD drive to be first boot?

Question? is it possible to try a USB drive for your installation it seems to work the best

---

### Post by oldfred on 2017-05-21
Is drive set for AHCI in UEFI?
Are you booting in UEFI mode?

With nVidia you need nomodeset for both installer and first boot after install or until you install proprietary driver from repository. 
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by magiwanders on 2017-05-27
I thank both of you for advice. Actually the problem was in the dvd. I used a USB stick and the installation went just fine. 

Actually installing Nvidia driver solved everithing, no need of nomodeset. When I set it i am not able to log in at all, so I deleted nomodeset boot parameter. The only problem I have right now is that the OS does not shut off. It just stays on black-screened forever. Anyone has idea why? 

Now the difficult part. Is there any chance I can Transfer my windows licence into a Virtual Machine so that I can access it in Ubuntu when I need it without having to use dual boot?

Magi

---

### Post by oldfred on 2017-05-27
When shutting down does this fully shut it down?
 Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key) 
   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is, and S can be before E, but others should be in order
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274) 

Do not know about Windows licensing. With UEFI the OEM version only license is inside the UEFI.

---

### Post by RobGoss on 2017-05-27
>  Now the difficult part. Is there any chance I can Transfer my windows licence into a Virtual Machine so that I can access it in Ubuntu when I need it without having to use dual boot?     

That might be a whole new thread

---

### Post by yancek on 2017-05-27
> Now the difficult part. Is there any chance I can Transfer my windows  licence into a Virtual Machine so that I can access it in Ubuntu when I  need it without having to use dual boot? 			 		

I expect you could do that under the licensing terms but best to check the specific license for whichever version of windows you are using as there are differences between them.   Generally, that is available from the windows 'run' command, just type in license.rtf.  If that doesn't do it, try an online search to find how to access the license on your particular windows release.


> Instead of using the software directly on the licensed computer, you may install and use the software within only one virtual 
(or otherwise emulated) hardware system on the licensed computer

From what I have read on this subject,  if you put your windows in a virtual machine, you would need to remove the install on the actual hardware.  You would probably be better off asking that question at a windows forum or reading the license on your system.

---

