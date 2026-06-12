---
title: "format, partition &amp; installing 13.04!"
date: 2013-05-25
forum: New to Ubuntu
---

### Post by gokulsurendiran on 2013-05-25
I had installed Ubuntu 10.04 when it was launched in my samsung netbook N150 in a single drive & I always upgraded the OS never formatted the drive & installed. currently it is running in 12.04.

Now the system has become little slow, planning to format, partition the drive & install the new version of ubuntu.

My hardrive capacity is 250 GB, how much space is needed for OS.

Where should I start with, please help. (I dont have a CD drive, will be using USB drive)

Thanks in Advance,
Gokul.

---

### Post by fantab on 2013-05-25
First of all, 13.04 has only 9 months support, where as the 12.04 LTS has support for 5 years. Since your only problem is that "system has become little slow" with 12.04 we can try a few things and see if we can optimize the speed. 

I some times use "bleachbit' to clean up my system. It is however a bit risky but since your want to do fresh install anyway, its worth a try.

sudo apt-get install bleachbit
gksudo bleachbit

clean up everything. You may get a warning that you don't have any disk space, just 'ignore'. Reboot. It may require a bit more cleaning, if you are interested then we can do so.

Regarding your original question: "My hardrive capacity is 250 GB, how much space is needed for OS."
Ubuntu '/' partition should be 20-25GB
Swap of about 2-4GB
If you want to use a /home partition then its upto you how big you want it as you will be saving your DATA on it.

---

### Post by gokulsurendiran on 2013-05-26
let me try this bleachbit, depending on the performace let me decide.

but apart from this my wfi stopped working after 12.04 update, I got lots os suggestions here but still couldn't make it work.

A friend suggested to go in for a format & neat installation so that it might improve!

---

### Post by sudo san on 2013-05-26
> **gokulsurendiran said:**
> let me try this bleachbit, depending on the performace let me decide.

but apart from this my wfi stopped working after 12.04 update, I got lots os suggestions here but still couldn't make it work.

A friend suggested to go in for a format & neat installation so that it might improve!

If you can, try inserting the Ethernet cable from your router (if that is what you are using) and the installer might pull in some drivers from any repositories it has. After the install, you will want to go  into the update manager and open up your settings and enable the backports repository. Then to update and reboot.

Also, a mistake I always do is forget to enable to wireless option. Just right-click on the little applet in the top corner and make sure that networking is enabled then wireless is enabled. (I make silly little mistakes sometimes :p)

As for your clean-up tool, I would suggest Ubuntu Tweak. Not only does it let you tweak your system to your liking (As suggested in the name), it also has a janitor function. If you have been upgrading since 10.04, then this will clean gigabytes! It cleans up all the unnecessary kernels, cache (There will be A LOT of that) and files no longer needed by programs you un-installed.

To install:
```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak
```

Hope this helps.

---

### Post by zeljkojagust on 2013-05-26
Hello,

If you want you can try my tutorial and install a clean generic Ubuntu 13.04 installation. My tutorial is based on 12.04 LTS edition, but procedure is the same with 13.04. First check this out:
[Ubuntu - generic installation]("http://www.zacks.eu/ubuntu-generic-installation/")

When you come to the part related to partitioning, you will notice I did a manual partitioning using parted. I don't know did they fix automatic partitioner in 13.04 version but with previous versions using one made partitions miss-aligned which has a negative impact on performace of the disk. So for your 250 GB disk you can do it like this:

parted /dev/sda
unit MiB
mklabel gpt
mkpart bios_grub 1MiB 2MiB
mkpart boot 2MiB 130MiB
mkpart swap 130MiB 2178MiB
mkpart system 2178MiB 18562MiB
mkpart home 18562MiB 100%
set 1 bios_grub on
set 2 boot on
q

After you're done with first tutorial, check this one:
[Ubuntu - initial setup]("http://www.zacks.eu/ubuntu-initial-setup/")

After completing that one, and before adding a desktop meta package you have to add a normal user. You can do it like this:
useradd -m -s /bin/bash yourusername
usermod -a -G adm,cdrom,sudo,dip,plugdev,lpadmin,sambashare yourusername (dont worry if you get error that some group does not exist, you can add them after installing desktop package)
passwd yourusername

After you're done with that, add a desktop package of your choice like this:
aptitude install -y -R ubuntu-desktop (Unity)
aptitude install -y -R xubuntu-desktop (XFCE - suitable for older computers)
aptitude install -y -R lubuntu-desktop (LXDE - suitable for older computers)
aptitude install -y -R kubuntu-desktop (KDE)

After you're done, you will have a nice clean desktop environment. To install additional software, you can check Falko's site at [HowToForge]("http://www.howtoforge.com").

Enjoy!

---

