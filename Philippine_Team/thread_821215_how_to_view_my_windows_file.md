---
title: "how to view my windows file?"
date: 2008-06-07
forum: Philippine Team
---

### Post by butchoy on 2008-06-07
I will start from scratch....

First I have windows.. and I have to 2 Partitions, C: and D: My windows xp and other programs are installed in C:, Now I've installed Ubuntu inside windows xp under C:

So I have 2 OS now and Ubuntu as the secondary OS. And now I have 2 bootable OS. 

I run ubuntu and go to My computer. I still have 2 partition but now it is name as: Filesystem and New Volume. I know that "Filesystem" was C: and "New Volume" was D:

Now my problem is this, How can i view my "windows file"? 

When I go to /filesystem/mnt/   windows is not there
even on /filesystem/media/.....
how can I view my windows file?...

and finally how can i merge my windows and my ubuntu? or how can I erase "windows xp OS" and still retain my documents inside it...thanks..

---

### Post by jeffimperial on 2008-06-07
First of all, you would want to make sure that the ntfs-3g package is installed. It's available from the repos, if multiverse is enabled.

**What happens when you right-click then Mount Volume? What error prompt do you get?**

Your disk mounting options are in /etc/fstab. You can edit it as root by doing: sudo gedit /etc/fstab

---

### Post by glenn45 on 2008-06-07
try going to places -- >   my computer.

---

### Post by butchoy on 2008-06-07
thanks for the help!!!!! ntfs-3g saved me!!!!!!

---

### Post by butchoy on 2008-06-07
now how can I merge my ntfs partition to my ubuntu.... Remember that I installed my ubuntu inside windows....how can I merge them?...or how can I finally remove windows and still retain some of my files...

---

### Post by jeffimperial on 2008-06-07
> **butchoy said:**
> now how can I merge my ntfs partition to my ubuntu.... Remember that I installed my ubuntu inside windows....how can I merge them?...or how can I finally remove windows and still retain some of my files...
Buti naman na-solve na 'yung una mong problema. Congrats

Sa tingin ko naman, safest step na ang gumawa ng backup copy ng files mo. Piliin mo lang 'yung files na gusto mong kopyahin. Kapag naipon mo na ang mga files mo sa isang lugar (of course dapat ang backup copy mo ay **WALA** sa Windows partition mo), pwede kang gumawa ng CD image or i-archive mo to save space. Di naman kailangang i-archive or CDimage kung marami kang space sa ibang partition.

To merge volumes, I particularly like gPartEd [Gnome Partition Editor]. Install mo using the command line, do: sudo apt-get install gparted. Then you can access the program from System > Administration > Partition Editor. From that program, pwede mong i-delete 'yung Windows partition mo at i-merge ang blank partition sa isang existing volume.

Sana hindi nakakalito masyado 'to ^ Hehe. Sabi ka kung kailangan mo pang tulong or clarification..

---

