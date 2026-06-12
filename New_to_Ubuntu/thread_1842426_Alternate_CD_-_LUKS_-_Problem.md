---
title: "Alternate CD - LUKS - Problem"
date: 2011-09-11
forum: New to Ubuntu
---

### Post by canam101 on 2011-09-11
I have been using clonezilla to back up my 10.10 setup - also to restore it a few times.

My hd is 160gb, but only about 6gb is used and that is all that clonezilla needs to restore.

I wanted to have an encrypted installation and used the alternate installation for 10.04. It worked fine, but when I tried to do a backup, clonezilla came back and said it would have to use dd, which meant that it had to backup the entire 160gb. That would take, I am guessing, around 20 hours to do, which I do not plan on doing.

So if I have it right, I would have to have a hard drive of about 6gb, install the encrypted os on it, and then I could back up and restore the 6gb in a reasonable amount of time.

I don't think it is possible even to buy a 6gb hard drive, so I guess my question is: is the present LUKS encryption scheme for ubuntu impractical? Or is there some simple way I am overlooking that will let me back up the system.

---

### Post by bodhi.zazen on 2011-09-11
My guess is that due to the encryption you can not use gparted to copy just the data, which would make sense.

I have always felt that backup strategies that make an image of the installed OS are suboptimal and excessively large. Just back up your data (your home directory for example) and any customizations you make to system files. No need to back up the 5 Gb of system files, those are in the Ubuntu repositories.

Learn to make and restore your system form a package list.

[http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html](http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html)

---

### Post by canam101 on 2011-09-12
> **bodhi.zazen said:**
> 

Learn to make and restore your system form a package list.

[http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html](http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html)Thanks for that link. If I understand it, I should make a periodic back up of my home directory, which I already do, plus a list of the packages on my system, which I can do by:
dpkg --get-selections > /backup/installed-software.log

I should also make backups of various config files, such as ones in /etc that I have customized.

When the time comes to restore, I boot up with an ubuntu disk and open a terminal. Then I restore my basic system with two commands:

dpkg --set-selections < /backup/installed-software.log

and 

dselect i

Is that correct? It sounds too easy.

At that point I may be starting with a hopelessly screwed-up system or even a blank hard drive. Correct? 

Or is it the assumption that I have re-installed the basic system from the install disk and am now re-adding the basic programs plus others that I had added from the repository?

Once I have the system re-installed, I copy over from my /home backup whatever I need, and also copy any /etc or other config files that I customized?

I am used to just popping in clonezilla and choosing whatever .img file I want to restore, so I want to make sure I have the drill down properly in case a restore of this LUKS-type system is needed.

---

### Post by bodhi.zazen on 2011-09-12
It does not count as a backup strategy until you have tested it.

Make a VM, back it up, and yes it is that easy.

---

### Post by canam101 on 2011-09-12
> **bodhi.zazen said:**
> It does not count as a backup strategy until you have tested it.

Make a VM, back it up, and yes it is that easy.Thanks, but rather than investigate what a VM is, and how to back it up, I'll just stick with the stuff in Linux that is mature enough so that it does not take much investigating to figure out.

Linux has come a long way in the past several years, and Ubuntu is the friendliest distro for the average user that I have tried, but it still has a lot of growing up to do.

Thanks for your replies.

---

### Post by bodhi.zazen on 2011-09-12
VM = Virtual Machine, ie Virtual Box or similar.

Linux runs well on a VM and you can try these things ;)

---

