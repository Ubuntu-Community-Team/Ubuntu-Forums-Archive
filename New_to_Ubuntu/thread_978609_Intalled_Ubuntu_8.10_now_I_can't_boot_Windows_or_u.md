---
title: "Intalled Ubuntu 8.10 now I can't boot Windows or ubuntu"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by LinuxDeadRaji on 2008-11-11
I installed Ubuntu 8.10 on a hard drive with Windows XP installed on a different partition.  After installation, I was no longer able to boot into Ubuntu or Windows XP, the options were there in GRUB but when I selected either one I got an error (unfortunately I don't remember the error).  I've reformatted the hard drive and installed 8.10.  I got GRUB error 17 upon booting the system.  I used the live CD to run the included partition manager to scan the disk to make sure there were no problems with the actual disk, the application reported no errors.  However, now when I boot I get a bootable media not found message.  Help would be very appreciated as I don't want to go through the trouble of re-installing windows if 8.10 is going to mess up the booting process.
-Ryan

---

### Post by eternalnewbee on 2008-11-11
You might have to go through the trouble again. But the trouble of reinstalling shouldn't beat you down. Ibex is really fast when it comes down to installation time. My guess is you messed up somewhere, during the installation (probably with the partitioning).
I found a link with screenshots that might be able to help you with your predicament.
Hope it helps.
[http://news.softpedia.com/news/Installing-Ubuntu-8-10-97417.shtml](http://news.softpedia.com/news/Installing-Ubuntu-8-10-97417.shtml)

---

### Post by LinuxDeadRaji on 2008-11-11
I don't want to use the entire disk, I set up a 20G partition with a 16M swap file.  When I was using 8.04 I had no problem.  I've installed 8.10 twice and it doesn't work where 8.04 works fine.  But thanks for the feedback ^_^.
-R

---

### Post by caljohnsmith on 2008-11-11
Do you get the Grub error before seeing a Grub menu, or before seeing "Press ESC to see menu", or after you get the Grub menu and select Ubuntu to boot? From your Live CD, please open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```
And we can work from there if you want.

---

### Post by bscbrit on 2008-11-11
I understand your concern but you are far, far better off installing windows first and then linux.  If you install windows second it will simply overwrite your grub loader anyway and you will have to recover it again using the Live Disk.

I would recommend:

1. Partition your drive at least into 2 partitions. Leave them both unformatted for the time being.  You should have a feel for how much space you want to dedicate to windows and how much to linux.

1. Install windows and get it working into the first unformatted partition.  Windows will format it itself.  Make sure that your drive is fully functional because some of the problems that you are having might indicate that it is on the way out.

2.  Install Ubuntu again, this time in the second unformatted partition.  Select the option 'Install Ubuntu in unused portion of the drive' - or something similar. 

It should just work but, if you have problems again, come back here.

---

### Post by bscbrit on 2008-11-11
> .... with a 16M swap file

I suspect that this is a typo.  The old rule of thumb used to be a swap partition of twice the installed memory, but no bigger that 512MB.  A 16MB doesn't seem terribly useful to me.

---

### Post by glotz on 2008-11-11
See [http://ubuntuforums.org/showthread.php?t=442945#post3518911](http://ubuntuforums.org/showthread.php?t=442945#post3518911)

---

### Post by bscbrit on 2008-11-11
[http://www.3till7.net/2007/10/25/grub-error-17/](http://www.3till7.net/2007/10/25/grub-error-17/)

Useful explanation.

---

### Post by eternalnewbee on 2008-11-11
> I installed Ubuntu 8.10 on a hard drive with Windows XP installed on a different partition
> I understand your concern but you are far, far better off installing windows first and then linux. If you install windows second it will simply overwrite your grub loader anyway and you will have to recover it again using the Live Disk
**Stick with caljohnsmith**

---

### Post by bscbrit on 2008-11-11
eternalnewbee

> 
I've reformatted the hard drive and installed 8.10


I'm curious as to why you disagree with my advice.  LinuxDeadRaji might be able to recover his Ubuntu but he wants to install Windows again.  When he does so it will overwrite his current grub menu.  I know that he can then recover his grub using a Live Disk but installing windows now and then installing Ubuntu again (which you acknowledge to be quite a quick procedure nowadays) will solve both problems.

---

### Post by caljohnsmith on 2008-11-11
> **bscbrit said:**
> 
I'm curious as to why you disagree with my advice.  LinuxDeadRaji might be able to recover his Ubuntu but he wants to install Windows again.  When he does so it will overwrite his current grub menu.  I know that he can then recover his grub using a Live Disk but installing windows now and then installing Ubuntu again (which you acknowledge to be quite a quick procedure nowadays) will solve both problems.
I think you might have missed what LinuxDeadRaji said in his original post:
[QUOTE=LinuxDeadRaji]...Help would be very appreciated as [COLOR="Red"]I don't want to go through the trouble of re-installing windows[/COLOR] if 8.10 is going to mess up the booting process.
-Ryan[/QUOTE]

---

### Post by bscbrit on 2008-11-11
eternalnewbie/caljohnsmith

> I don't want to go through the trouble of re-installing windows if 8.10 is going to mess up the booting process.

No, I didn't. He **is** going to install windows again but he doesn't want Ubuntu to spoil it.  Windows will definitely spoil 8.10's boot, but 8.10 shouldn't affect his Windows boot.  Now, I know that it looks like it did, but by fixing the problem he has now and then installing Windows he will have to fix Grub again anyway. I would say install Windows again now, and Ubuntu if necessary, and then just fix Grub once.

Thanks for taking the time to explain your thought process though, it seems we just approach the same problem from different directions.

---

### Post by eternalnewbee on 2008-11-11
> **He is going to install windows again but he doesn't want Ubuntu to spoil it**> I installed Ubuntu 8.10 on a hard drive with Windows XP installed on a different partition. After installation, I was no longer able to boot into Ubuntu or Windows XP, the options were there in GRUB but when I selected either one I got an error (unfortunately I don't remember the error). I've reformatted the hard drive and installed 8.10. I got GRUB error 17 upon booting the system. I used the live CD to run the included partition manager to scan the disk to make sure there were no problems with the actual disk, the application reported no errors. However, now when I boot I get a bootable media not found message. Help would be very appreciated as I don't want to go through the trouble of re-installing windows if 8.10 is going to mess up the booting process.
**Where does he say that?**

---

### Post by eternalnewbee on 2008-11-11
This is turning out in to being a contest about whose right and who's wrong! Why don't we combine forces to try and help the starter of this thread?[-o<

---

### Post by bscbrit on 2008-11-11
> **eternalnewbee said:**
> This is turning out in to being a contest about whose right and who's wrong! Why don't we combine forces to try and help the starter of this thread?[-o<

eternalnewbie

This isn't a contest - I am trying to understand why the advice that is being given is what it is.  I cannot help if I don't understand why you are doing what you are doing. :-)

Please look at the quote in my post #12. I can see a 'IF' which implies that he WILL re-install providing that Ubuntu doesn't make a mess of it.

---

### Post by waffleturd on 2008-11-11
I got the same error
but i got it fixed
get linux on a cd (make sure on the cd there is more than one file if there is only one there's something that happened during burn)
when the computer starts push the delete button and the bios should pop up. Then change your boot order by making boot from cd first then hard drive the rest doesn't matter. Then insert the cd in your computer and then it should install linux. Then install your windows.

ps make sure you install linux first, and then windows, because installing linux after the windows sometimes erases the windows.

---

