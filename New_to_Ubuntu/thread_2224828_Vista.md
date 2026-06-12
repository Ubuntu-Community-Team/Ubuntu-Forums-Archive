---
title: "Vista"
date: 2014-05-18
forum: New to Ubuntu
---

### Post by dave_moran on 2014-05-18
thinking to install Ubuntu in a laptop using Vista. will this work? i don't find any threads addressing Vista. the laptop hardrive has a separate partition containing a back up for the vista. if i do a swap instead of setting up the dual boot, will  i lose the back up also?

---

### Post by LastDino on 2014-05-18
More than likely yes, but I can't be sure. Why not just use something else and simply format Vista partition and install Ubuntu on it? You seem to be willing to get rid of it so it is quite simple actually. Just break that Vista partition into at least two partitions, namely / and SWAP. If you're willing, go with /, /home and SWAP setup.

---

### Post by pfeiffep on 2014-05-18
I respectfully suggest trying out Ubuntu on a live dvd or usb for a while to insure that you have a clear vision of exactly what Ubuntu provides and that the drivers for your hardware all function correctly.

---

### Post by Impavidus on 2014-05-18
Dual booting Ubuntu with Windows Vista works the same way as dual booting with Windows 7. You should be able to use guides written for that.

---

### Post by tripp98 on 2014-05-18
[ 						 							]("http://ubuntuforums.org/member.php?u=1788249")[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1788249")+1 for pfeiffep 

try running from a live cd.  If you like how ubuntu works before you install it on your hard drive.  I would suggest getting a new hard drive and pull the old one out.  if your laptop has any warranty left on it.  The manufacturer will not help you if it doesnt have the original os.  if you want super fast use an ssd or you can purchase a much larger one.

---

### Post by ibjsb4 on 2014-05-18
Maybe you could first partition your hdd.

Could you use a window partitioner and post your partition layout?

Do you have a restore disk?

---

### Post by stalkingwolf on 2014-05-18
the recovery partition should be very small a few hundred MB. just leave it unless you have a very small hdd. first to be safe make a recovery disk, then defrag at least 2 times.  then use gparted to resize the large vista partition.  you can also use the install alongside vista option at install.
I also agree try the live disk first see how you like it and more importantly to see if there are any issues that need addressing before install.

---

### Post by dave_moran on 2014-05-19
thx for all the input. i recently put the dual boot set up in a Compaq desktop. I cleared available space in multiple partitions and was disillusioned when i wasn't given any option as to where the download was stored. That has me concerned where it will present itself in the laptop. i have the CD tonite. will try it that way 2morro..

---

### Post by lisati on 2014-05-19
The 5-year-old laptop I'm currently using came with Vista preinstalled, and I'm currently dual booting with Ubuntu. Because Vista already had four partitions assigned, it took some careful planning.

In short, what I did went something like this. What I did was to **make a** backup and **recovery disk** using the preinstalled software, delete some of the "extra" partitions to free up some space, and install Ubuntu into the space that was freed up. 

Two caveats:
[LIST]
[*]Make backups and recovery disks BEFORE you begin. This can make recovery easier if something goes wrong.
[*]Initial repartitioning is often best done using Windows partition manager. Although the tools which come with Ubuntu are pretty good, Windows can sometimes throw a hissy fit if things aren't done its way.
[/LIST]

---

### Post by QIII on 2014-05-19
+1 to resizing your Windows partition with the Windows tool.

Windows will know best how to move things around without screwing itself up.

This, IMHO, should always be the standard answer:  Defrag twice, use the Windows partition tool to shrink the Windows partition.  

I do not advocate going all in and obliterating Windows.

---

### Post by MartyBuntu on 2014-05-19
Clean up the Vista install, then do a drive image. Then you can wipe the laptop entirely and install Ubuntu.

You can replace Vista by recovering the image if you ever wanted to return to Windows or re-sell the machine to someone who prefers Windows.

---

