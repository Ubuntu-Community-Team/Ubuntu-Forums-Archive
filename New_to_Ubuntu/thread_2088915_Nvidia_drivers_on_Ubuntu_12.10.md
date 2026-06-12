---
title: "Nvidia drivers on Ubuntu 12.10?"
date: 2012-11-27
forum: New to Ubuntu
---

### Post by PyroDonkey on 2012-11-27
Hi everyone,
I recently installed Ubuntu (12.10) for the first time and I was wondering if there was a set guide for installing the .run file available from Nvidia's website. I've tried several methods through researching on Google, but I have had no success. My graphics card is a 650m for a laptop. My system is also a 64bit if that changes the install procedure at all.

If anyone could provide some insight into how to properly install the drivers, it would be really appreciated.

Thanks

---

### Post by Frogs Hair on 2012-11-27
I would check software sources > additional drivers first. I have not needed to download/install from the Nvidia web site before but I am not familiar with your card .

---

### Post by oldfred on 2012-11-27
Welcome to the forums.

Either the Ubuntu offered or the nVidia will need the linux headers installed first for it to work.

With your newer 650, you may want the experiment version.
This will tell you which versions are available.
apt-cache search nvidia-sett*

Also has instructions for downloading .run nVidia drivers.
       [http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)
# You may need headers - meta package for current version:
sudo apt-get install linux-headers-generic
# only reason to purge is there are several versions, if you know you have different nVidia use that:
# I used nvidia-current-updates & nvidia-settings-updates, example below is just nvidia-current, use version you prefer
sudo apt-get purge nvidia*
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot
May want nvidia-current, nvidia-current-updates or nvidia-current-experimental-XXX for most recent testing version.
apt-cache search nvidia-sett*

       Fix for nVidia with 12.10 missing kernel dpkg reconfigure:
[http://ubuntuforums.org/showthread.php?t=2072862](http://ubuntuforums.org/showthread.php?t=2072862)

---

