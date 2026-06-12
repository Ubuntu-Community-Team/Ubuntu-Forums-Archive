---
title: "How-To: PS3 HDD native installation (playstation 3)"
date: 2007-01-11
forum: Outdated Tutorials &amp; Tips
---

### Post by inee on 2007-01-11
okay i finally got ubuntu installed on my ps3 NATIVELY on its HDD (compared to [the guide by candell ]("http://louiscandell.com/ps3")with an external usb hdd). 


i sort of followed the guide above but omitted and changed some steps mainly: 


1. downloaded all required files and burned on cd/dvd 
2. installed fedora 
3. skipped the disk partitioning step 
4. debootstrap debian on ps3 hdd on a folder named /mnt/ubuntu 
5. copied fedora's kernel and stuff 
6. edited system files like kboot to add /mnt/ubuntu 
7. installed xubuntu desktop (ubuntu would not resolve dependencies) 

and voila! 


i think im the first who has done it (been a around several linux forums for the past week and none have done it yet). 


[IMG]http://i26.photobucket.com/albums/c110/inee666/01-10-07_1015.jpg[/IMG]
**[COLOR="Red"] love those sweet 2 PPC thread penguins and 6 SPE penguin support. [/COLOR]**


all i need now is a hdmi cable to display on my 1080i hdtv so i can get into gnome desktop (gdm doesnt load on 480i). 


------------------------------------- 

ubuntu on PS3 HDD 

------------------------------------- 


1. install fedora minimum
2. mount /dev/cdrom /mnt/cdrom
3. yum install dhclient
4. yum install wget and nano
5. copy debootstrap to /tmp
6. zcat debootstrap
7. mkdir /mnt/ubuntu and /mnt/ubuntu/boot
8. debootstrap edgy to /mnt/ubuntu
9. copy fedora's kernel and initrd stuff then chroot into /mnt/ubuntu
10. yum install dhclient, wget and nano in new ubuntu root; mkdir /proc/net/dev
11. wget [http://www.louiscandell.com/ps3/files/cell-linux-cl_20061110-addon/ps3pf-utils_1.0.9-3_powerpc.deb](http://www.louiscandell.com/ps3/files/cell-linux-cl_20061110-addon/ps3pf-utils_1.0.9-3_powerpc.deb) and vsync-sample_1.0.1-5_powerpc.deb
12. dpkg -i ps3pf-utils_1.0.9-3_powerpc.deb
13  dpkg -i vsync-sample_1.0.1-5_powerpc.deb
14. install xbuntu desktop (ubuntu had a lot of dependency resolving)
15. install ps3videomode
16. wget from [http://louiscandell.com/ps3/files/xorg.conf](http://louiscandell.com/ps3/files/xorg.conf) into /etc/X11/xorg.conf or configure current xorg  
17. edit fstab and kboot configurations


NOTE: ubuntu will not let you log in as root. so before restarting you may want to edit your passwd, grp, and/or use passwd root to enable it if you want.

---

### Post by Ciego on 2007-01-17
> 
14. install xbuntu desktop (ubuntu had a lot of dependency resolving)


I noticed this too.  Did you ever get the Ubuntu desktop install to finish?  I would run out of memory every time after a few hours and it would just stop.  

I am wondering which is the best desktop for the PS3 with Ubuntu.

---

### Post by Ciego on 2007-01-19
> **inee said:**
> 
all i need now is a hdmi cable to display on my 1080i hdtv so i can get into gnome desktop (gdm doesnt load on 480i). 


Do you have any more info about this?  I thought that I just did something wrong until I saw this ... seems to be the only place I even found it mentioned.

---

### Post by juanzone on 2007-01-20
> **inee said:**
> okay i finally got ubuntu installed on my ps3 NATIVELY on its HDD (compared to [the guide by candell ]("http://louiscandell.com/ps3")with an external usb hdd). 


i sort of followed the guide above but omitted and changed some steps mainly: 


1. downloaded all required files and burned on cd/dvd 
2. installed fedora 
3. skipped the disk partitioning step 
4. debootstrap debian on ps3 hdd on a folder named /mnt/ubuntu 
5. copied fedora's kernel and stuff 
6. edited system files like kboot to add /mnt/ubuntu 
7. installed xubuntu desktop (ubuntu would not resolve dependencies) 

and voila! 


i think im the first who has done it (been a around several linux forums for the past week and none have done it yet). 


[IMG]http://i26.photobucket.com/albums/c110/inee666/01-10-07_1015.jpg[/IMG]
**[COLOR="Red"] love those sweet 2 PPC thread penguins and 6 SPE penguin support. [/COLOR]**


all i need now is a hdmi cable to display on my 1080i hdtv so i can get into gnome desktop (gdm doesnt load on 480i). 


------------------------------------- 

ubuntu on PS3 HDD 

------------------------------------- 


1. install fedora minimum
2. mount /dev/cdrom /mnt/cdrom
3. yum install dhclient
4. yum install wget and nano
5. copy debootstrap to /tmp
6. zcat debootstrap
7. mkdir /mnt/ubuntu and /mnt/ubuntu/boot
8. debootstrap edgy to /mnt/ubuntu
9. copy fedora's kernel and initrd stuff then chroot into /mnt/ubuntu
10. yum install dhclient, wget and nano in new ubuntu root; mkdir /proc/net/dev
11. wget [http://www.louiscandell.com/ps3/files/cell-linux-cl_20061110-addon/ps3pf-utils_1.0.9-3_powerpc.deb](http://www.louiscandell.com/ps3/files/cell-linux-cl_20061110-addon/ps3pf-utils_1.0.9-3_powerpc.deb) and vsync-sample_1.0.1-5_powerpc.deb
12. dpkg -i ps3pf-utils_1.0.9-3_powerpc.deb
13  dpkg -i vsync-sample_1.0.1-5_powerpc.deb
14. install xbuntu desktop (ubuntu had a lot of dependency resolving)
15. install ps3videomode
16. wget from [http://louiscandell.com/ps3/files/xorg.conf](http://louiscandell.com/ps3/files/xorg.conf) into /etc/X11/xorg.conf or configure current xorg  
17. edit fstab and kboot configurations


NOTE: ubuntu will not let you log in as root. so before restarting you may want to edit your passwd, grp, and/or use passwd root to enable it if you want.

Inee, I'm very new to linux and I am trying to follow your directions. Although it's not detailed enough for me I think I can get it done together with candell's guide (Ihope:biggrin: ). My question is what your kboot and fstab configurations are? Also are there any limitations with your ubuntu install-- the sound for example. Are you able to have sound output? Thanks.

---

### Post by Ciego on 2007-01-21
> **inee said:**
> 
all i need now is a hdmi cable to display on my 1080i hdtv so i can get into gnome desktop (gdm doesnt load on 480i). 



I just confirmed that this is not true.  I just booted up kubuntu on a 480i TV.

---

### Post by Ciego on 2007-01-21
I have posted another HOWTO for installing Ubuntu on the PS3 with a live CD.  

[http://ubuntuforums.org/showthread.php?p=2042834#post2042834](http://ubuntuforums.org/showthread.php?p=2042834#post2042834)

---

