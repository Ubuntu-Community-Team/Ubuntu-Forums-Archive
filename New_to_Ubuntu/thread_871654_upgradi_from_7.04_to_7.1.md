---
title: "upgradi from 7.04 to 7.1"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by pkj on 2008-07-27
Trying to update to 7.1 using update manager...

However geeting the following error

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz) Sub-process gzip returned an error code (1)

This happens after the upgrade manager reaches the step "Modifying the Software Channels"

Already tried thrice...
Network Connection is working fine

pkj

---

### Post by sharks on 2008-07-27
type in terminal:
sudo apt-get dist-upgrade

---

### Post by pkj on 2008-07-27
The command does the following
pradeep@pradeep-desktop:~$ sudo apt-get dist-upgrade
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

What next!!!!!!!

pkj

---

### Post by rockerphil on 2008-07-27
have you considered going with a clean install? or even upgrading to Hardy? might be easier on ya, least you'll know the install disk will work, less headaches dealing with the update manager



edit: you may want to check your /etc/apt/sources.list file if you can't seem to retrieve a particular package

---

### Post by pkj on 2008-07-27
How do i update to hardy...
and i hope i will not loose the data...

pkj

---

### Post by Elfy on 2008-07-27
> **rockerphil said:**
> edit: you may want to check your /etc/apt/sources.list file if you can't seem to retrieve a particular package

+1

Make sure you have no 3rd part repos enable d- not any other lists in etc/apt/ other than sources.list - make sure that there is nothing in sources.list.d particularly.

---

### Post by rockerphil on 2008-07-27
first off be sure to back up any personal files to some type of external storage media, i.e. CDs, usb drive, external hard drive, something to keep your personal files. then just download the Ubuntu 8.04 Hardy Haron ISO image here

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

and do the basic Ubuntu deal, burn the ISO to a bootable CD, and i'm sure you know the rest, hope this helps,

Phil

----------------
Now playing: [Travis Tritt - Here's A Quarter](http://www.foxytunes.com/artist/travis+tritt/track/heres+a+quarter)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

### Post by Elfy on 2008-07-27
You need the alternate rather than livecd to update with I believe, alos to upgrade to hardy you'd need to updtae to gutsy first - thus 2 upgrades - although it can apparently be done I wouldn't recommend it.

If you try to upgrade 2 versions then you might be better off with a cleanm install as rockerphil suggests.

---

### Post by rockerphil on 2008-07-27
well my computer is so ancient that the only thing that works efficiently on it (at least for me) is to install a Command Line Interface with the minimal ISO then building the DE from the command prompt, so i've always gone with a clean install, just had to get use to backing up my personal file, which is always a good practice in the first place

---

