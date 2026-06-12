---
title: "problems upgrading"
date: 2013-03-04
forum: New to Ubuntu
---

### Post by radeque on 2013-03-04
Hello,
I am currently using the 10.04 version and my update manager offers me to upgrade to the new 12.04.2 release. I tried this but after fetching the files it gives me this message:
Not enough free disk space. The upgrade has aborted. The upgrade needs a total of 3,910 M free space on disk '/'. Please free at least an additional 1,158 M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'."

Don't understand, I have enough space on my disk.. and when I type sudo apt-get clean in terminal, nothing happens.

Thanks,
Radek

---

### Post by fantab on 2013-03-04
Install 12.04 fresh, don't upgrade. 10.04 to 12.04 is a long and time consuming upgrade... also there are no guarantees that even if you upgrade successfully it will be without any issues. There have been some major changes to Ubuntu since 10.04, hence you are better off doing a new and fresh installation. 

Don't forget to BACK UP your important DATA first.

---

### Post by plucky on 2013-03-04
> **radeque said:**
> Hello,

Not enough free disk space. The upgrade has aborted. The upgrade needs a total of 3,910 M free space on disk '/'. Please free at least an additional 1,158 M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'."

Don't understand, I have enough space on my disk.. and when I type sudo apt-get clean in terminal, nothing happens.

Thanks,
Radek

Open a terminal and post output for ```
df -h
```

All "sudo apt-get clean" does is deletes all the .deb files in /var/cache/apt/archives/ directory,so it doesn't printout anything but clears out space in / partition.

Good Luck

---

### Post by radeque on 2013-03-04
ok, thanks for advice.. What is the best way to install it fresh? :-)
R.

---

### Post by zrdc28 on 2013-03-04
It seems that you are out of space on the / partician, bring up "gnome partician editor" or gparted and take an look at it. You will be able to shrink the partician
next to it and the expand the / partician.  It will show you the partician size and the used, if the used is close to the amount needed you need to expand it. 
  Right click on the partician next to / and tell it to re size it smaller then click on the / partician and make it larger.

The best way to do it is to burn you a copy of Gparted live or Partician magic and boot from that. That way the hard drive will not be mounted and you can expand and shrink particians easily. You might want to backup before you do this.

---

### Post by fantab on 2013-03-04
> **radeque said:**
> ok, thanks for advice.. What is the best way to install it fresh? :-)
R.

Follow the instructions **[HERE]("http://www.ubuntu.com/download/help/install-desktop-long-term-support") or [HERE]("https://help.ubuntu.com/community/GraphicalInstall")**

---

### Post by radeque on 2013-03-04
thanks guys,
i did df -h and got this 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              12G  8.0G  2.6G  76% /
none                  493M  300K  493M   1% /dev
none                  497M  328K  497M   1% /dev/shm
none                  497M   84K  497M   1% /var/run
none                  497M     0  497M   0% /var/lock
none                  497M     0  497M   0% /lib/init/rw
/dev/sda2              44G   31G   12G  74% /home
/dev/sda4              56G   50G  6.6G  89% /media/3490AA5B90AA22FA


Now I have no idea where is / on my computer and how to access it.. I'm really bad with computers, as you can see :-)

---

### Post by grahammechanical on 2013-03-04
This is / or root = size 12G Used 8.0G Available 2.6G Used 76% Mounted on /

That should be enough space to upgrade. If you do attempt a Fresh install then you will need to choose the Do Something Else option and tell Ubuntu to install into sda1 by giving it a mount point of /. You will also need to tell it that sda2 should have a mount po8int of /home but DO NOT tell it to format sda2 or you will lose everything that is in sda2 and that is 31G of stuff. 

To create more space in sda1 (or / ) you may wish to remove some programs that you no longer want. That will create space. You can also Empty the Rubbish Bin. Regards.

---

### Post by plucky on 2013-03-04
> Filesystem Size Used Avail Use% Mounted on
/dev/sda1 12G 8.0G 2.6G 76% /

You only have 2.6G available to be used is the reason your upgrade didn't work as you need 3.9G.

Your / partition also seems quite full as my 10.04 / partition never got above 5G.

You could install Bleachbit and clear some space on the / partition.
Also as it is 10.04 there may be a lot of old kernels in /boot partition.


Good Luck

---

