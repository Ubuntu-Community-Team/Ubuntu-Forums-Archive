---
title: "Connecting &amp; Transfering files to Galaxy S3?"
date: 2013-02-05
forum: New to Ubuntu
---

### Post by IdoSC on 2013-02-05
Ubuntu 12.10

I want to connect my Galaxy S3 to my PC and transfer music files and other files to it, what's the easiest way to do that in Ubuntu?

---

### Post by IdoSC on 2013-02-06
Anyone?

---

### Post by 3rdalbum on 2013-02-06
> **IdoSC said:**
> Anyone?

The best method is to connect the phone to your computer via wifi and install an FTP or Samba server on your phone, then on Ubuntu you can connect to the phone's server like any other file server.

There are other ways, but this is the easiest and most reliable until Ubuntu 13.04 comes out.

---

### Post by IdoSC on 2013-02-06
> **3rdalbum said:**
> The best method is to connect the phone to your computer via wifi and install an FTP or Samba server on your phone, then on Ubuntu you can connect to the phone's server like any other file server.

There are other ways, but this is the easiest and most reliable until Ubuntu 13.04 comes out.
I'll try those solutions, so far I've simply connected my external SD card separately with an adapter but it seems quite redundant to open the back of my phone and take it out every time I want to transfer files (plus I'm missing the internal 12GB that way), so I'll try to use your methods instead.

What will 13.04 bring to the table? Would it be accessible via USB?

---

### Post by wlraider70 on 2013-02-06
Can you just connect the USB cord and mount it like a thumb drive?

---

### Post by mastablasta on 2013-02-06
> **IdoSC said:**
>  
What will 13.04 bring to the table? Would it be accessible via USB?
 
i think so. i think it's called MSP or something from what i read, but i also think that for example KDE in 12.10 already has this options in dolphin, but needs to be upgraded first via PPA.

---

### Post by Mark Phelps on 2013-02-06
The problem is not Ubuntu -- so, a new version is not going to help.

The problem is that Google removed USB Mass Storage mode from Android versions starting with ICS.

Thus, when you connect via USB, you no longer get the previous screen that allows you to select "disk"; instead, you have only two choices -- multimedia device (MTP) or camera (PTP).

I've read that there are ways to get MTP to work, but I have the GS3 also, and have NOT been able to get it to connect with Ubuntu.

It connects in MS Windows -- but Samsung supplies special drivers for that to happen.

---

### Post by sandyd on 2013-02-06
I can confirm that it works in 13.04 - just plug it in, and the window appears with an option to access both the internal and external storage.

---

### Post by vanadium on 2013-02-06
The problem *is* ubuntu.

You may upgrade the mtp support in 12.10 as well: [http://www.webupd8.org/2013/01/upgrade-to-gvfs-with-mtp-support-in.html](http://www.webupd8.org/2013/01/upgrade-to-gvfs-with-mtp-support-in.html)
I tried this last week, and it works reasonably well.

---

### Post by vajorie on 2013-02-06
The easiest method I've found was Airdroid (from Google Play market). Next up was to use adb. I didn't need to work on poor MTP support that way.

---

### Post by efflandt on 2013-02-08
**AndFTP** app from your S3 can do sftp, scp, etc. and can use ssh keys.  That can be done over your WiFi network.  Or with **SSH Server** app on the phone you can ssh/scp/sftp from Ubuntu over the network which can also use keys.

I have played around with **mtp** related things on the S3 USB cable from Ubuntu 12.04 setting up udev for it. Although, somewhat strangely, if I connect the phone as an MTP device, it automatically opens the file browser as though it is music, and all I can see is top level directories or files of internal storage and microSD, nothing under that.  If I set the phone to PTD, both file manager windows open and I can see into subdirectories of internal S3 storage, but the microSD window is totally empty (not even top level directories).

I have not figured out how to get a separate directory under /media using **mtpfs** to do anything, but maybe that is because fuse already automatically mounts things under ~/.gvfs. This is with it connected as PTP device:

efflandt@XPS8100-1204:~$ **ls ~/.gvfs**
gphoto2 mount on usb%3A002,011

efflandt@XPS8100-1204:~$ **ls ~/.gvfs/gphoto2\ mount\ on\ usb%3A002\,011/**
store_00010001  store_00020002

efflandt@XPS8100-1204:~$ **ls ~/.gvfs/gphoto2\ mount\ on\ usb%3A002\,011/store_00010001/**
Alarms             DCIM      mobi_drm       Pictures   Ringtones
Android            Download  Movies         Playlists  samsungapps
Application        files     Music          Podcasts   wdh_update
burstlyImageCache  gameloft  Notifications  QrDroid

efflandt@XPS8100-1204:~$ **ls -l ~/.gvfs/gphoto2\ mount\ on\ usb%3A002\,011/store_00010001/Music/Tori\ Amos/**
total 0
drwx------ 1 efflandt efflandt 0 Dec 31  1969 Abnormally Attracted to Sin
drwx------ 1 efflandt efflandt 0 Dec 31  1969 Tales Of A Librarian  A Tori Amos Collection
drwx------ 1 efflandt efflandt 0 Dec 31  1969 The Beekeeper

---

### Post by giuliano1977 on 2013-04-17
I worked this problem out by installing gMTP (I have 1.3.3-1 version). From that installation on I can easily access the internal and external SD card with Nautilus simply conneting the phone by a USB cord.

---

