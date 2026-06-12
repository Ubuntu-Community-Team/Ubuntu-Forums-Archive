---
title: "[SOLVED] rsync failed - should I repartition ext. drive?"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-11-13
What has gone wrong? How do I fix this?

I am copying (backing up) my /home to an external 80 gig drive. That drive's filename is marks80.

mark@Lexington-19:/home$ sudo rsync -vvr /home/mark/ /media/marks80
sending incremental file list
rsync: readlink "/home/mark/.gvfs" failed: Permission denied (13)
delta-transmission disabled for local transfer or --whole-file
.ICEauthority
.Xauthority
.bash_history
.bash_logout
.bashrc
.dmrc
.dmrc.bck
.esd_auth

quite a few lines redacted

.adobe/Acrobat/8.0/UserCache.bin
rsync: writefd_unbuffered failed to write 4 bytes [sender]: Broken pipe (32)
skipping non-regular file ".adobe/Acrobat/8.0/Cert/curl-ca-bundle.crt"
skipping non-regular file ".config/transmission/gtk/socket"
skipping non-regular file ".gcjwebplugin/gcj-instance-10260-2-appletviewer-to-plugin"
skipping non-regular file ".gcjwebplugin/gcj-instance-10260-2-plugin-to-appletviewer"
skipping non-regular file ".gcjwebplugin/gcj-instance-12919-0-appletviewer-to-plugin"
skipping non-regular file ".gcjwebplugin/gcj-instance-12919-0-plugin-to-appletviewer"
skipping non-regular file ".gcjwebplugin/gcj-instance-14274-0-appletviewer-to-plugin"
skipping non-regular file ".gcjwebplugin/gcj-instance-14274-0-plugin-to-appletviewer"
skipping non-regular file ".gcjwebplugin/gcj-instance-6443-7-appletviewer-to-plugin"
skipping non-regular file ".gcjwebplugin/gcj-instance-6443-7-plugin-to-appletviewer"
skipping non-regular file ".gcjwebplugin/gcj-instance-7375-1-appletviewer-to-plugin"
skipping non-regular file ".gcjwebplugin/gcj-instance-7375-1-plugin-to-appletviewer"
rsync: write failed on "/media/marks80/winetricks.1": No space left on device (28)
rsync error: error in file IO (code 11) at receiver.c(298) [receiver=3.0.3]
rsync: connection unexpectedly closed (1511 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(635) [sender=3.0.3]

---

### Post by bscbrit on 2008-11-15
> rsync: write failed on "/media/marks80/winetricks.1": No space left on device (2

Well, one problem appears to be that your 80Gb hard drive is full, or hasn't got enough space for the amount of data that you want to copy, but I would have expected rsync to tell you that before it started.  In fact, it probably isn't and the fault is caused by the second error....:

Secondly, the command should be```
sudo rsync -vvr /home/mark/* /media/marks80/
```

You were trying to copy your data to a FILE called marks80 in the /media directory.  The trailing '/' is important to indicated that you are looking for the marks80 directory (which is your external drive) rather than a file of the same name.

---

