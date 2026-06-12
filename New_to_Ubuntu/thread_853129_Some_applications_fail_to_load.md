---
title: "Some applications fail to load"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by potatan on 2008-07-08
Hi,

I was trying to get my microphone working and at some point lost all sound, so following this guide:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

I removed the sound system and reinstalled it using:
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
and
sudo apt-get install linux-sound-base alsa-base alsa-utils
```

This, as mentioned in the above howto, removed GDM and ubuntu-desktop (why on earth did it do that?), so I followed the instructions and ran
```
sudo apt-get install gdm ubuntu-desktop
```
to recover.

But I don't think it has reinstalled everything that may have been removed.  First of all, my sound still does not work, despite trying all sorts of different settings in alsamixer and sound properties.  Second, some applications fail to load completely.  I get the "Starting xxx" in the bottom panel, which then disappears after about 5 seconds.  Two such applications (which worked previously) are "Simple Backup Config" and "Font Viewer".  My sound still does not work either.

So I'm a little worried that removing 
linux-sound-base 
alsa-base 
alsa-utils
has also removed something else that is now causing me problems.

Any ideas?

Many thanks.

---

### Post by ChameleonDave on 2008-07-08
Try [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting).

---

### Post by potatan on 2008-07-08
Thanks for the link, I've managed to resolve my sound problems now!

But I still have the fault of applications failing to load.  If I load sbackup from the command line I get the following error:

```
paul@antec:~$ sudo simple-backup-config
[sudo] password for paul: 
Segmentation fault
paul@antec:~$ 

```

Any ideas why this is failing to load?  I have reinstalled, and completely removed and reinstalled, the application.  But I still get an error.

Thanks

---

### Post by ChameleonDave on 2008-07-08
> **potatan said:**
> 

Any ideas why this is failing to load?  I have reinstalled, and completely removed and reinstalled, the application.  But I still get an error.


I don't know anything about simple-backup-config.  Do you have any examples of more common software failing?

---

### Post by potatan on 2008-07-10
Simple Backup is, umm, a simple backup tool :) available in Synaptic Package Manager (sbackup).  I've been using it regularly to backup my documents folder.  Another application that does the same thing on loading, is "Font Viewer" (Applications/Other - though you may have to add it using System/Preferences/Main Menu).

I've attached a screenshot of the bottom panel - basically, it starts to load then disappears after about 5 seconds.

Thanks.

---

### Post by ChameleonDave on 2008-07-10
I can't reproduce this problem.

You're not using Wubi, are you?

All I can suggest is purging and reinstalling those apps that malfunction.

---

### Post by potatan on 2008-07-11
*Edit - see the end of the post*

No, I'm not using Wubi, should have said it's plain Ubuntu 8.04.  The thing is that Sbackup was working fine until I started messing with sound etc.

I tied a "sudo apt-get --purge remove sbackup", but when I install it again I get the same problem.

No worries, I'll look for another simple backup tool to use instead of, err, Simple Backup.

Thanks for your help

*Edit*

I may have found the reason for the fault.  I used synaptic to install a different backup tool, "pyBackPack" and tried to run it.  It let me create a backup set for the files I want to back up, but when I try to run the backup it won't let me write to my backup drive.

Further investigation shows that I am no longer able to create files and folders on my backup drive (an internal 60gb IDE drive).  I am wondering if all this odd behaviour is related to me having to reinstall ubuntu-desktop and gdm (see the first post for details of what/why).  I cannot run "gksudo nautilus" either (nothing happens when I try), to correct this problem.

So I have two things going on here

1. How can I retake control of the backup drive/folders?
2. Something may have gone missing when I inadvertently uninstalled GDM etc., which is now giving me weird problems

Any ideas?

Many thanks.

---

### Post by galv on 2008-09-17
> **potatan said:**
> Thanks for the link, I've managed to resolve my sound problems now!

But I still have the fault of applications failing to load.  If I load sbackup from the command line I get the following error:

```
paul@antec:~$ sudo simple-backup-config
[sudo] password for paul: 
Segmentation fault
paul@antec:~$ 

```

Any ideas why this is failing to load?  I have reinstalled, and completely removed and reinstalled, the application.  But I still get an error.

Thanks
I get the same error :( I still haven't found a way to fix it :(

---

### Post by frenzie on 2008-10-10
me too, adding my 2cents to this:
[https://bugs.launchpad.net/ubuntu/+source/sbackup/+bug/271522](https://bugs.launchpad.net/ubuntu/+source/sbackup/+bug/271522)
```
[sudo] password for shanna: 

(simple-backup-config:7532): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed
/usr/sbin/simple-backup-config:1002: Warning: g_error_free: assertion `error != NULL' failed
  gtk.main()

(simple-backup-config:7532): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(simple-backup-config:7532): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)
Segmentation fault

```

---

