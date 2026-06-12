---
title: "partition full - how to fix"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by hubiedo on 2008-10-21
i am on ubuntu 8.

my / partition is full but the system is working fine for now. how can i fix or repair it. 

i have used find to see if any large files -- none that i can identify. my system is ubuntu 8 and my partitions are / , /boot, /appl, /u, /home, /bulin, & swap on a 500 gb disk. the / partition is 49gb and completely full. 

any suggestions or comments on why so much space is used and how to clean it or add space to it. i have additional space available on /bulin of about 175 gb but gparted won't let me change or move space around. 

do i need to do it with fdisk? or unmount the partitions or something but then how do you run it to make changes etc. to the partitions. should i copy / to /bulin and then resize it somehow? 

any help or suggestions would be appreciated.

hubert

---

### Post by hyper_ch on 2008-10-21
did you emty the (root) trash bin?

---

### Post by Dougie187 on 2008-10-21
If you want to change or move space around you have to do it from a live cd. You can't do it from inside the OS that is installed on your disk.

---

### Post by jemate18 on 2008-10-21
Thats correct, you need a live CD.. You cannot change resize a partition that is mounted.... Also be very careful and you should have a backup

---

### Post by philinux on 2008-10-21
Just for comparison my root partition is 12gig and currently using only 3.1gig.

49gig seems way excessive. As hyper says delete the trash in root first.
You might need

```
gksudo nautilus
```

---

### Post by hubiedo on 2008-10-21
thanks all of u guys/gals

i have the live cd. do i go thru rescue or thru install? when it gets to the partition part do i tell it not to make any changes/overwrite and just resize the partitions? can you give me more of an idea the procedure when using the live cd?

are you telling me to boot from the cd into the ubuntu "test" setup or boot into the install setup?

i also cked the trash -- none. i did the gksudo nautilus and no trash.

thanks,
hubert

---

### Post by handydan918 on 2008-10-21
Just to satisfy everyone's curiosity, try ```
cd /
```
then
```
sudo du -h | head -20
```

Then cut and paste the output back here. This should show the largest files in your root partition.

---

### Post by Elfy on 2008-10-21
> i have the live cd. do i go thru rescue or thru install? when it gets to the partition part do i tell it not to make any changes/overwrite and just resize the partitions?
Boot the livecd but do not start the installer.

There is a partition editor in the system admin menu which you can use, it will likely be using the swap - so before you start to resize anything it can be unmounted by selecting the swap partition - right click - unmount.

To resize / you will need to make some free space next to it - so it depends how the disc is partitioned.

You could screenshot the editor - accessories.

---

### Post by TheSixthPandava on 2008-10-21
Hello everybody,

I have similar if not identical problem. My root [and only] internal partition is 71 GB and all data combined on it takes no more than 40 GB. But, it shows me that I have only 250 MB left. I am a begginer, installed Ubuntu only two months ago, ad I don't know what to do about this problem.

---

### Post by TheSixthPandava on 2008-10-21
Thinking that I have the same problem as initial author of this topic, I did what handydan918 suggested. 

The results are:

> 0       ./root/.gconfd
0       ./root/.gconf
0       ./root/.wapi
3.0K    ./root
4.0K    ./media/disk/proc
4.0K    ./media/disk/lost+found/#8749068
72K     ./media/disk/lost+found
4.7M    ./media/disk/bin
4.0K    ./media/disk/tmp/Tracker-marko.5796/Attachments
664K    ./media/disk/tmp/Tracker-marko.5796
4.0K    ./media/disk/tmp/ssh-gJvpqH5693
4.0K    ./media/disk/tmp/.X11-unix
4.0K    ./media/disk/tmp/keyring-L3zWfM
8.0K    ./media/disk/tmp/gconfd-marko/lock
12K     ./media/disk/tmp/gconfd-marko
4.0K    ./media/disk/tmp/virtual-marko.3NMnkb
4.0K    ./media/disk/tmp/.ICE-unix
8.0K    ./media/disk/tmp/orbit-root
8.0K    ./media/disk/tmp/orbit-marko
4.0K    ./media/disk/tmp/gconfd-root


Don't know if this will help.

---

### Post by Elfy on 2008-10-21
@ TheSixthPandava - please start your own thread - although I would check out your trash first it can get confusing when 2 or more requests are in the same thread

[http://ohioloco.ubuntuforums.org/showthread.php?t=898573](http://ohioloco.ubuntuforums.org/showthread.php?t=898573)

---

### Post by TheSixthPandava on 2008-10-21
I don't have problem with openning new topic, I just thought that it would not be appropriate to duplicate topics of the same problem. 

By the way, thank you, I followed this link and found trash that wasn't visible on default desktop ikon. Now I have 7,8 GB of free space, but it still doesnt explain wehere is my memory. I will now open new topic.

---

### Post by fornix on 2008-10-21
Just check your apt cache for old deb files. You can remove those deb files.
Cache is stored at location **/var/cache/apt/archives**

---

### Post by TheSixthPandava on 2008-10-21
Thank you, I did what you suggested, but it had only two smaller files.

---

### Post by hubiedo on 2008-10-21
thanks you all,

here is the output of sudo du -h

hjk@hjk-linux:~$ cd /
hjk@hjk-linux:/$ sudo du -h|head -20
[sudo] password for hjk: 

4.0K	./srv
252K	./root/.synaptic/log
264K	./root/.synaptic
4.0K	./root/.gnome2_private
16K	./root/.thumbnails/normal
20K	./root/.thumbnails
20K	./root/PDF
4.0K	./root/.qt
4.0K	./root/.kde/share/services
4.0K	./root/.kde/share/mimelnk
8.0K	./root/.kde/share/config/kresources/calendar
8.0K	./root/.kde/share/config/kresources/contact
8.0K	./root/.kde/share/config/kresources/notes
28K	./root/.kde/share/config/kresources
120K	./root/.kde/share/config
4.0K	./root/.kde/share/servicetypes
16K	./root/.kde/share/apps/kconf_update/log
20K	./root/.kde/share/apps/kconf_update
24K	./root/.kde/share/apps
4.0K	./root/.kde/share/applnk

i will also try the live cd tomorrow.

thanks again
hubert

---

### Post by laffinet on 2008-10-21
I had issues with running out of space a while ago although I was certain there should be plenty left. Someone pointed me here:

[http://ubuntuforums.org/showthread.php?t=898573]("http://ubuntuforums.org/showthread.php?t=898573")

After going through all the steps listed I got heaps space back.

---

### Post by hubiedo on 2008-10-22
thanks for all the help u guys--

laffinet -- that is a great article on how to empty trash & regain space. i will go thru the steps tonight and report back.

i started up my live/install dvd but couldn't find anyway to fire up the system w/o going thru install or the test ubuntu setup. did i miss something? do i need to make a "live install cd " of some kind to start the system or w/o mounting the installed ubuntu 8 that is messed up? so that the installed partititons are not mounted? in fc7 you use rescue to do that kind of stuff. or should i go thru the rescue on the grub menu to work on the fix of the / partition to give it more space?

i will try the trash fix first. the article really explained how to do it. and i need all the help i can get.

thanks everyone
hubert

---

