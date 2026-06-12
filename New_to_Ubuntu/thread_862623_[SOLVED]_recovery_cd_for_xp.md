---
title: "[SOLVED] recovery cd for xp"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by Yudraciell on 2008-07-17
:confused: well my friend wantd me to install Ubuntu on his laptop cause he was sick of viruses...now he cant play his game cause wine wont work...it seises up cause of multiple reasons i am not gona get into.

he has an HP pavilion 6000 series and wants his xp back on it...the problem is that the recovery cd for his pavilion wont work...he gets a grub error (21 or 22 cant remember) so it wont install...and then the amount of hdd space seems wrong....it ays he only has 10gig instead of his 80 that he is supposed to have...

ty in advance

---

### Post by bodhi.zazen on 2008-07-17
My guess is either the BIOS is not set to boot from CD or the CD is bad (you should not begetting a grub screen). Try reading the CD from Ubuntu, if you can, set the BIOS to boot the CD.

If the CD is bad you will need to contact the manufacturer of your laptop or Microsoft.

---

### Post by lisati on 2008-07-17
There are three or four kinds of "Recovery Disk" that I'm aware of. My Compaq desktop (Compaq is owned by HP) came with a preformatted partition on its HD that can be 
used, amongst other things, to restore the system to an "out of the box" condition. If this is the kind that your friend's machine came with (the error from Grub, together the apparent problem with available disk space  seems to suggest that this might be the case) it is possible that his recovery disk has been damaged. In this case you might have to talk nicely to the people from whom he purchased the machine.

It is also possible to get hold of Windows disks that you pop in the CD drive, but be careful of downloading disks. Apart from potential legal problems, some sites have copies that have nasty suprises in the form of malware (trojans, viruses etc)

If you are able to do so, posting the output of ```
fsdisk -l
``` might be able to help knowledgable forum users tell if there's a recovery partition abailable on your friend's system.

---

### Post by Yudraciell on 2008-07-17
no built in recovery....it had one a while ago that took up hdd space (like 5 gigs of it) so he had it removed with the hp recovery cd.

The cd does indeed work...as just before we put Ubuntu 8.04 on it we used it...but i told him about Linux and how many viruses it gets and he wanted to try it so we put Ubuntu on it...

it has ubuntu 8.04 (64 bit)
1.8ghz amd 3200+
512 ram
ati radion x200 mobility

he has no external hdd and the only partitions on it is.

---

### Post by carandraug on 2008-07-17
If the game he plays doesn't ask a lot from the computer you may have sucess in convincing him to give Virtualbox a go. It's my last resource when I'm converting someone to Linux and there's something they really really need, has no open source alternative and does not run in Wine.

---

### Post by Frenske on 2008-07-18
Can you actually install a Windows desktop inside virtualbox if you only have a recovery CD? I was wondering this since I have an older version of Matlab 7 that I want use and that's the only reason I use windows.

---

### Post by Oldsoldier2003 on 2008-07-18
> **Frenske said:**
> Can you actually install a Windows desktop inside virtualbox if you only have a recovery CD? I was wondering this since I have an older version of Matlab 7 that I want use and that's the only reason I use windows.
No, you need an actual windows installation cd (or iso). A recovery cd won't work.

---

### Post by Yudraciell on 2008-07-18
> **carandraug said:**
> If the game he plays doesn't ask a lot from the computer you may have sucess in convincing him to give Virtualbox a go. It's my last resource when I'm converting someone to Linux and there's something they really really need, has no open source alternative and does not run in Wine.

well it runs in wine....i am marking this post as solved because it is no longer needed ty for your input people...

He wants Linux....parents want crapdows...his computer he gets what he wants (mainly virus protection hehe) he just told me to make it look like windows so i installed the KDE gui and changed t around a little bit...but it sorta looks like windows.

again tyvm for your time

---

### Post by Yudraciell on 2008-09-02
[http://www.dban.org/](http://www.dban.org/)

thats how to do it :)

---

### Post by mikewhatever on 2008-09-02
> **Yudraciell said:**
> [http://www.dban.org/](http://www.dban.org/)

thats how to do it :)

So, you've deleted everything from the disk and the recovery CD then worked? Why wouldn't it work before?

---

### Post by Yudraciell on 2008-11-03
> **mikewhatever said:**
> So, you've deleted everything from the disk and the recovery CD then worked? Why wouldn't it work before?

it completly wipes the system....

---

