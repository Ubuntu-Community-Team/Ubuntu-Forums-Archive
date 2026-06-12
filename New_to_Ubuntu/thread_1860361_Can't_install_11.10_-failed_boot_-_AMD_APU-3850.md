---
title: "Can't install 11.10 -failed boot - AMD APU-3850"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by ru2044 on 2011-10-14
Hi,
I've got almost new AMD APU-3850 with Radeon 6550D integrated. The motherboard is Asus F1A75-M.
I was really looking forward to having new distribution downloaded, cause they wrote that new kernel in 11.10 fully supports my hardware (whatever it means ;).

-firstly, I upgraded from 11.04 via upgrade manager. After restarting computer I saw only black screen.
-secondly, I make a bootable USB (I checked the checksum) and tried to install.(I checked boot priority) I saw nothing - just black screen
-thirdly I found out about 'nomodeset' problem. I followed a tutorial from this forum. I installed 11.10 succesfully. I rebooted,edited Grub and wrote 'nomodeset' again, but the system 
stops at 'checking battery state' and 'starting automatic crash 
report generation' is failed.
I tried to install 11.10 using 3 different sources and 3 different pendrives. Nothing helped...
-fourthly, I downloaded 10.10. After installing I got a commend 'incompatible license'...

I hope everything is clear. Is there any solution?

---

### Post by rollerman2006 on 2011-10-14
I had a similar problem after upgrading to 11.10 from 11.4 on an HP Pavilion laptop.

After the initial reboot after the upgrade completed, I got to the new login screen, entered my credentials and then the screen went blank.

After waiting several minutes I hit the power button to turn the machine off.   I then saw on the screen the processes giving the order to shut down.

It looks like it's hanging at the speech synthesizer reference line.

I have it installed (via the WUBI installer) as dual boot with Win7.

How should I go about fixing the problem, by boot up with a Live CD and edit from there?

BTW: I do have the upgrade working on another "lesser" laptop, an Acer5732Z.

Thank you.

---

### Post by ru2044 on 2011-10-15
I found out a moment ago that after installing 11.10 and rebooting - rear USB panel doesn't work,cause I've got a message that my keyboard wasn't detected. When I plug it to a side USB panel - it works.

All problems I 've wriiten in post #1 are still valid...

---

