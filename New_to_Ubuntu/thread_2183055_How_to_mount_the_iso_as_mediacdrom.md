---
title: "How to mount the iso as /media/cdrom/ ?"
date: 2013-10-23
forum: New to Ubuntu
---

### Post by Agnishom_Chattopadhyay on 2013-10-23
My laptop keeps overheating. As I read in another thread, I figured that I would have to install an ATI driver to solve the case.  However, to install it I have to enter the CD for Ubuntu 12.04 LTS which is my version.  My problem is that have the standard iso file, and I used an USB to install Ubuntu. So, Is there a way to mount the iso file as /media/cdrom and install the required packages from it without really burning a CD?

---

### Post by dankojoffrey on 2013-10-23
Try Gmount-iso...
[https://apps.ubuntu.com/cat/applications/saucy/gmountiso/](https://apps.ubuntu.com/cat/applications/saucy/gmountiso/)

---

### Post by deadflowr on 2013-10-23
I don't see how mounting a livecd is going to help install the ati drivers.
Ubuntu already installed the open-source ati drivers, called radeon.
AFAIK you need to download the closed-source fglrx drivers.

Since you're in 12.04 go to the dash and type additional drivers and hit enter.
A window will open up and a pop up box with a search scanning bar will run, stating it is looking for drivers.
Then the main window will open with a selection of drivers you can try out.
Select the driver you think would work best.(usually the recommended driver)
Then click on the activate button.
The driver will be downloaded and installed.

After the driver is installed, you'll need to generate an xorg.conf file.
```
sudo amdconfig --initial
```
is usually what you need to run.
Look here on more of what you need to do, and what you need to do if it doesn't work
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Agnishom_Chattopadhyay on 2013-10-23
I have a terribly slow internet connection now. I figured that the package named fglrx which according to apt-get is there in the Ubuntu CD. But I need to insert the cd in /media/cdrom/ to let apt-get install it.

Is there any way to get that package from the iso using apt-get?

---

### Post by deadflowr on 2013-10-23
I searched a livedvd session and could not find the driver on the actual disk.
They are available through the restricted drivers repos, which are enabled on the disk.

---

### Post by Agnishom_Chattopadhyay on 2013-10-24
There are other software I need from the livecd too. E.g, wvdial  I tried to mount the iso as /media/cdrom/ with the mount command. But, every time I run apt-get, apt-get unmounts the iso from that place and tells to enter a disc labelled 'Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)'. I had downloaded the iso named ubuntu-12.04.3-desktop-amd64.iso. Is that the same as that disc?  I have a problem burning the image into a *real* cd due to some hardware problems.  Anyway, how do I make apt-get understand that iso to be the live cd?

---

### Post by mastablasta on 2013-10-24
you can put the image on USB stick instead.

---

### Post by Agnishom_Chattopadhyay on 2013-10-24
How would that help mastablasta?

---

### Post by deadflowr on 2013-10-24
Well, did you try installing gisomount?

It's pretty simple to use.
Open it, select browse, find the iso, click ok then select mount.
The iso will be mounted in media.

I don't think the disk need be mount as /media/cdrom/diskname.
It'll give the disk the proper name.

Here's another place to read through.
[https://help.ubuntu.com/community/MountIso](https://help.ubuntu.com/community/MountIso)

---

