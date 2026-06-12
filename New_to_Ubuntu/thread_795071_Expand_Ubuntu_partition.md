---
title: "Expand Ubuntu partition"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by NaF on 2008-05-15
Hi:)
I switched to Linux, cuz I actually HAD to, Windows made my screen flicker when I was inside games and/or saw some flash animation. hm. 
I installed with Wubi (got a weird busybox error the first time I installed, so the uninstall feature is not totally useless^^). Onto a 50gig partition, the problem is, I have 600gb of data on the NTFS partition. I can access it and all. But tbh, I'd much rather have it all on the same partition, or at least in ext3 (?). On windows there's a command to convert from fat32 to ntfs, is anything like this possible in Ubuntu also? Or what would you suggest I do - don't really have to option of storing the data somewhere else, while I reinstall or whatever to convert it to one partition. 

Thanks in advance :)

---

### Post by shifty_powers on 2008-05-15
[http://www.linuxforums.org/forum/linux-newbie/52309-changing-ntfs-ext3-without-losing-any-data.html](http://www.linuxforums.org/forum/linux-newbie/52309-changing-ntfs-ext3-without-losing-any-data.html)

[http://www.linuxquestions.org/questions/slackware-14/converting-from-ntfs-to-ext3-231740/](http://www.linuxquestions.org/questions/slackware-14/converting-from-ntfs-to-ext3-231740/)

[http://www.aeonity.com/frost/converting-from-windows-linux-hard-drives-ntfs-ext3](http://www.aeonity.com/frost/converting-from-windows-linux-hard-drives-ntfs-ext3)

[http://ubuntuforums.org/showthread.php?t=389058](http://ubuntuforums.org/showthread.php?t=389058)

[http://ubuntuforums.org/showthread.php?t=58472](http://ubuntuforums.org/showthread.php?t=58472)

---

### Post by shifty_powers on 2008-05-15
it's amazing what a google search can find ;)

---

### Post by NaF on 2008-05-15
it's not really that I'm too lazy to use google. I've found those too, but the first three are from 2003-2005, and this is like my 24th hour with ubuntu, so i'm not really in a position where I can judge out-dated from working. and the last two ones, I just plain simply do not understand :oops:

---

### Post by NaF on 2008-05-16
oh well, let's hope someone else asks this question, so i can follow that thread :(

---

### Post by laffinet on 2008-05-16
You can change partitions using gparted, it's available in the repos, so just go to Administration->Synaptic Package Manager search for gparted and install it.

You have to boot into a live CD though, as your partition will be locked when you boot normally.

I don't think there is a way to convert from ntfs to ext3. So you either have to copy bit by bit, change partition sizes, copy more, change partition sizes, etc. Quite a lengthy process. 

Or you keep it as ntfs and mount the drive in Ubuntu. I think there are drivers available to read ntfs in Ubuntu, but I haven't done that myself.

---

### Post by shifty_powers on 2008-05-16
the ntfs3g drivers are supplied as standard in 8.04. Tbh, i've used them plenty and never had a problem...

---

### Post by hyper_ch on 2008-05-16
you can't convert ntfs to ext3...

But as you surely have another computer or external drive or something where you make backups to (at least I hope you make backups)... you just temporarily save all the data on there, format the ntfs drive to ext3 and copy it all back.

If you do not make any backups I urgently recommend you to start doing so ;)

---

