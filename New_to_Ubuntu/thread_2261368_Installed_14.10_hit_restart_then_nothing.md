---
title: "Installed 14.10 hit restart then nothing?"
date: 2015-01-18
forum: New to Ubuntu
---

### Post by hank603 on 2015-01-18
I'm new to ubuntu and I just installed 14.10 again and when I get to needs to restart, I hit restart and end up with a blank screen.

---

### Post by yancek on 2015-01-18
That would be unusual to have an install of Ubuntu as the only operating system if your hardware is up to date.
How old is the hardware?  Can you post some info on it?  Amount of RAM, graphics card for starters.
Did you do an md5 checksum on the downloaded iso?  Instructions are on the download page.
Did you leave the default for Device for bootloader installation on the Installation Type page?

---

### Post by hank603 on 2015-01-18
I have an old Gateway with AMD Athlon 64x2 dual core processors 6000+x2 and Vesa:MCP61=mcp61-80 graphics.  ram? what I did was purchase a CD w/14.10 booted with it and followed the instruction and loaded it as the only OS and when it completed and asked to restart that's when it went blank.  Now when I started it up it the grub menu came up with options.  I eventually got in but it doesn't reboot properly?

---

### Post by grahammechanical on 2015-01-18
At the end of the installation process we are asked to confirm restart. What happens next is that we should get a message saying remove CD from the drive and press Enter. By which time the DVD drive should have opened. This did not happen?

Or is there another problem that when you load Ubuntu and then shut down or restart it does not shutdown or restart? Is the problem with the Ubuntu Install session or with Ubuntu once it is installed? Your posts do not make this clear.

As someone who tests Ubuntu versions before they are released I say from experience that it is not unknown for the Install session not to shutdown as it should. And there have been times when I have failed to see the message on the screen because the colour of the text does not show up clearly against the black screen.

So, what is it? The Ubuntu Installer not shutting down and requiring a power off? Or Ubuntu not shutting down and requiring a power off? Pressing Ctrl+Alt+Del in this situation might bring about a more graceful restart.

Regards.

---

### Post by hank603 on 2015-01-18
the DVD  did open and CD removed then it shutdown but did not restart,

---

### Post by hank603 on 2015-01-20
here's the latest I had a error message sys running in low graphics mode, found a thread with a solution then another error init err broken pipe not resolved yet but when I start up a 
GNU Grub V2.02~beta 2-15 comes up w/options I selected advance options for ubuntu which gave me two more options selected ubuntu w/linux 3-16.0-23 generic recovery mode that let me in.  but when I restart it goes back to the GNU Grub menu I didn't select anything and it brought me to the sign in, signed in then went activities page but it froze

---

### Post by hank603 on 2015-01-20
I just picked up the Official Ubuntu Book w/14.04 disk  I'm still having problems w/14.10  should I install 14.04 and see if the problems are still there or continue on w/14.10.  I have both disks so it shouldn't be much of a problem.  And if I'm successful loading 14.04 the is it difficult to upgrade to 14.10 or should I?  thoughts, suggestions welcome.  tks

---

