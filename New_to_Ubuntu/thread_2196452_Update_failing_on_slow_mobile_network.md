---
title: "Update failing on slow mobile network"
date: 2013-12-29
forum: New to Ubuntu
---

### Post by parcdulas on 2013-12-29
Hello,

I have a system in the heart of rural Wales where the only internet I can get is poor GPRS mobile so update is VERY slow. (>24 hours!) Something always interupts the download around 02:00am either the mobile network or Ubuntu. The only way I can recover the connection is to reboot the system as without a reboot there is no mobile available in network manager. Is there any way I can either update with a fast connection on another machine to a CD for use on the system in Wales or update in small chunks of say 10Mb at a time so less is lost when the internet link is lost.

Thanks

---

### Post by plucky on 2013-12-29
> **parcdulas said:**
> Hello,

I have a system in the heart of rural Wales where the only internet I can get is poor GPRS mobile so update is VERY slow. (>24 hours!) Something always interupts the download around 02:00am either the mobile network or Ubuntu. The only way I can recover the connection is to reboot the system as without a reboot there is no mobile available in network manager. Is there any way I can either update with a fast connection on another machine to a CD for use on the system in Wales or update in small chunks of say 10Mb at a time so less is lost when the internet link is lost.

Thanks

Have a look at a program called APtonCD, which will make a copy of all the .deb files on the system with the good connection and you can the transfer the CD onto the one in Wales to update the apt archives. As long as the machine with the good connection is running the same version as the the one in Wales,it will save having to download all the packages again.

Good Luck

---

### Post by parcdulas on 2013-12-29
Thanks, I'll try that.

---

### Post by parcdulas on 2013-12-29
Thanks Plucky, I've installed APtonCD and run it on my recently updated system and it seems to have produced an Iso image to the CD. Do I just boot the machine with the slow internet connection from the CD the next time I go down there ?

---

### Post by plucky on 2013-12-30
> **parcdulas said:**
> Thanks Plucky, I've installed APtonCD and run it on my recently updated system and it seems to have produced an Iso image to the CD. Do I just boot the machine with the slow internet connection from the CD the next time I go down there ?

No, All AptonCd does is create the Iso of all the .deb files that are in /var/cache/apt/archives which are the files that are downloaded during the upgrade phase when it says  e.g."227 updates found".When you run ```
sudo apt-get update
``` it will still download the index files over the slow connection but shouldn't be more than 25Mb to 40Mb  but will use the updated .deb files when you run ```
sudo apt-get upgrade
``` or ```
sudo apt-get dist-upgrade
``` if there is a new kernel.

If you install AptonCd on the rural machine, you can then use the restore option which will copy the files to the correct place.

Then run ```
sudo apt-get update && sudo apt-get upgrade
``` and it should install all the upgrades from the archives, no more downloading large amounts of data over a slow connection.I used this method a while back when I had a remote machine with only a dial up connection and it worked quite well.


Good Luck

---

