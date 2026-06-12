---
title: "MTP fails whjen transferring large files ..."
date: 2015-01-14
forum: New to Ubuntu
---

### Post by cwmoser on 2015-01-14
I use MTP protocol when I attach my Tablet using a USB cable to my Ubuntu 14.04 desktop PC to transfer files.
I have noted repeated failures transferring large amounts of information.
When I say large, files grouped together a 1GB or so in total size.
I have a programming background and my suspicion is that its a handshaking and/or timeout issue.

Is there a fix for this?  How about some other method than MTP?

---

### Post by DuckHook on 2015-01-14
This happens with me too. MTP support in Ubuntu (and Linux in general) is primitive. Even smaller mp3 files will sometimes fail with corrupted metadata. 1 GB files would be especially bad. Try FTP instead, which recovers from failure more elegantly. You don't say what tablet you have, but with MTP, I suspect android. I'm only familiar with Android, which has too many FTP clients to count. I suspect iOS is same. If Windows Surface, I'm afraid I know nothing about them.

---

### Post by cwmoser on 2015-01-14
I have an Android -- Samsung Galaxy Tab 4 7".  Great buy at Costco - $139.00.
Neat little Tablet.

I'll check out FTP.  I did note that ES File Manager had a built in Samba capability.
Its slow though.

---

### Post by efflandt on 2015-01-14
Some Android apps that are handy to have on your phone or tablet. This was essential when using Ubuntu 12.04 where I could not get MTP to work at all by any method. I usually have sshd on Linux configured to use keys only (no passwords) and my openssh keys work either way for Android too. This assumes that your phone or tablet is connected to same LAN as your PC (my Linux PC has static LAN IP). I have not had an trouble transfering large groups of images or videos from my S3 using AndFTP to sftp.

ConnectBot - ssh client
AndFTP - sftp client
SSHServer - what it says, so I can ssh or sftp to my phone from Linux

If your Ubuntu does not have a static IP you can use **ZeroConf Browser** Android app to find its IP, since by default Ubuntu has avahi-daemon installed which works like Apple Zeroconfig. I don't know if there an avahi-daemon for Android, which would avahi-browse in Ubuntu to find your phone.

---

