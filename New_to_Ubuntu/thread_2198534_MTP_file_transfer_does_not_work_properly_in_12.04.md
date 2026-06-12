---
title: "MTP file transfer does not work properly in 12.04"
date: 2014-01-09
forum: New to Ubuntu
---

### Post by cwmoser on 2014-01-09
I am trying to get MTP  file transfer to work properly between Ubuntu 12.04 and my Nook HD+ tablet.

I tried the process described below to install MTP ...
[http://bernaerts.dyndns.org/linux/74-ubuntu/247-ubuntu-automount-nexus7-mtp](http://bernaerts.dyndns.org/linux/74-ubuntu/247-ubuntu-automount-nexus7-mtp)
... but I get problems.  My MTP enabled Nook will mount and umount properly but when
I attempt to transfer files, it seems to work OK at first but then just seems to pause and
eventually emits an error.

Anyone know how to properly enable MTP in 12.04?

Carl

---

### Post by 3rdalbum on 2014-01-09
> **cwmoser said:**
> I am trying to get MTP  file transfer to work properly between Ubuntu 12.04 and my Nook HD+ tablet.

I tried the process described below to install MTP ...
[http://bernaerts.dyndns.org/linux/74-ubuntu/247-ubuntu-automount-nexus7-mtp](http://bernaerts.dyndns.org/linux/74-ubuntu/247-ubuntu-automount-nexus7-mtp)
... but I get problems.  My MTP enabled Nook will mount and umount properly but when
I attempt to transfer files, it seems to work OK at first but then just seems to pause and
eventually emits an error.

Anyone know how to properly enable MTP in 12.04?

Carl

MTP has always been horribly broken in Ubuntu and it's only since 13.04 that it has actually been usable.

I suspect your options are:

1. Upgrade to Ubuntu 13.10 or 14.04, or
2. Put files onto your Nook via some other method. FTP server running on the Nook over Wifi; Bluetooth file transfer; or ADB. All of these options will be more likely to work than MTP on Ubuntu 12.04.

---

### Post by TheFu on 2014-01-09
I recall fighting with this a little myself. I have 12.04 (use only LTS here) and a Nexus4.  Tried to get it working following similar instructions, but eventually, it just worked.

Added a PPA - langdalepl-gvfs-mtp-precise.list to get the working versions and that was it. Searched and found found these instructions [http://www.webupd8.org/2013/01/upgrade-to-gvfs-with-mtp-support-in.html](http://www.webupd8.org/2013/01/upgrade-to-gvfs-with-mtp-support-in.html) that reference the PPA.

```
sudo apt-get update
sudo apt-get dist-upgrade 

```and everything started working.

Here are the packages installed (now):
```
$ dpkg -l |grep mtp
ii  libmtp-common                          1.1.6-1ppa1                              Media Transfer Protocol (MTP) common files
ii  libmtp-dev                             1.1.6-1ppa1                              Media Transfer Protocol (MTP) development files
ii  libmtp-runtime                         1.1.6-1ppa1                              Media Transfer Protocol (MTP) runtime tools
ii  libmtp9                                1.1.6-1ppa1                              Media Transfer Protocol (MTP) library
``` that made everything "better".

Because MTP uses gvfs, I'm still not really happy. gvfs appears to be crap to me - disconnects all the time, doesn't show real "mounts" and it is slower than other old-school solutions.  It works good enough, provided too many files are not transferred in a single attempt. Doesn't support renaming or within-device-moves either.  Bleh.

Still this is much easier to setup than the udev methods.

I still wonder why developers don't just use the mount interface and let autofs handle stuff like this? Oh well.

---

### Post by SeijiSensei on 2014-01-09
The other alternative is to transfer files using wifi by installing a client app on your phone.  I have used Acrosync, an rsync client, for bulk transfers, and AndSMB or AndFTP for occasional file retrievals.  The latter two obviously require that the remote machine has either Samba or an FTP server like proftpd installed.  There's also the inexpensive [Wifi File Transfer Pro]("https://play.google.com/store/apps/details?id=com.smarterdroid.wififiletransferpro&hl=en") that turns the phone into a web server and support for file uploads and downloads.

I've since moved to 13.10 so that I can use MTP when I need to.

---

### Post by philinux on 2014-01-09
With my Galaxy S3 I put it in PTP mode. Seems to work without error.

---

