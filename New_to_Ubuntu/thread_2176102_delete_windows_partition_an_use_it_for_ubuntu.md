---
title: "delete windows partition an use it for ubuntu"
date: 2013-09-22
forum: New to Ubuntu
---

### Post by david98 on 2013-09-22
Hi am currently using ubuntu 12.04 precise on a 500gb hard drive with a windows 7 partition and ubuntu partition is there any way of deleting the windows partition and using my full hdd for ubuntu without having to do a full reinstall as i don't really want to have to reinstall all my programs and transfer all my files over any advice would be appreciated

---

### Post by whitesmith on 2013-09-22
You should be able to use gparted to delete the Windows partition and give all available space to Ubuntu. A possible gotcha is the case where Windows controls booting. If GRUB is on the Ubuntu partition, you should be good to go -- but read my sig line before doing anything!

---

### Post by david98 on 2013-09-22
Yeah grub is on the ubuntu partition will look into a little further before i attempt it. Am in the process of backing up most of my files and sending some of them to the cloud also.

Iv'e always been told to use the philosophy if you have not got files saved in 3 different. ways you have not got the file's saved

---

### Post by b6Q8Ats on 2013-09-22
a clean install is always better.
i was running W7  dual partition and decided to custom install (overwrite all partitions using the livecd method), after id backed up my data.
didnt actually take that long. It carried over all my drivers en-mass the only hick-up was from Nvidia. 
remember UBi installs firefox as its browser

Roy

---

### Post by david98 on 2013-09-22
A think am going to go for a complete reinstall within the next couple of day's once iv'e transferred all my file's to a back up hdd and when all current operations and download's are complete. As i had very little problems when i installed ubuntu on a partition i cant envisage having any major problem's when i reinstall. am going to keep this post open in case anyone else has a opinion about deleting partition and extending the ubuntu partition.

---

### Post by oldfred on 2013-09-22
Also backup a list of installed apps, if you have installed much. Data for apps is in /home, but apps will not be auto installed except for standard default list.

       from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

---

### Post by david98 on 2013-09-22
Thank's oldfred the link from loving linux will save me a lot of time and make sure reinstalling wont be an inconvenience. Cheer's for the very helpful post.

ps.... Iv'e been using linux distribution's on and off for a number of year's now i don't know why i never bothered to use the forum's before you couldn't ask for a more helpful group plus it saves me putting my head in an linux book and reading up on it which can be very time consuming knowledgeable though. :guitar:

---

### Post by Impavidus on 2013-09-23
Simply deleting a Windows partition and expanding an Ubuntu partition, or formatting it as an extra Ubuntu partition and mounting it somewhere for storage, is such a safe operation that there's no real need for a clean install, unless of course you want to do some clean-up anyway. Having backups is recommended though. If your internet connection is slow compared to the amount of software and data (not user data, which you keep backed up and can simply copy back to your disk) in your present installation, I wouldn't reinstall.

---

### Post by oldfred on 2013-09-23
I like small system partitions and large data partitions. I even did that back with Windows in most cases.
So you can convert NTFS partition to ext4 and just make it a data partition. Then you can link (what I use) or bind folders into your /home.

Some come back after uninstalling Windows and have one application they just cannot live without. So best to have full backup of Windows. Plus if you sell system, new buyer will more than likely want Windows.

I do clean installs, but have multiple / partitions so I can test new version without changing existing working install or just to mess around to see what happens if I do something.
But then my backup procedure is to make sure I can do a new clean install and restore to as close as possible to my working install.

---

### Post by david98 on 2013-09-23
Am defiantly going to delete window's partition and extend ubuntu partition iv'e backed up all my file's so if anything goes wrong am well prepared for a fresh install. As to selling my machine in the future this laptop came with windows 8 installed got windows 8 disk also got 7 vista and xp and all the drivers for all versions of window's as well but i don't see any need to sell anyway even when i do upgrade will probably give it to the wife to be or my 2 year old son he's already getting use to a tablet so wont be too long until he get's the drift of a laptop for games and cartoon's. Thank's for the advice any way.

ps. Remember play it safe stick to linux

---

