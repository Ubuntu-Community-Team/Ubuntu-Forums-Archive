---
title: "Ubuntu &quot;An error occurred while mounting /&quot; &quot;Errno 30 read only file system&quot; HELP!"
date: 2013-08-22
forum: New to Ubuntu
---

### Post by dylan4 on 2013-08-22
Be warned: I have little to no experience with Ubuntu.
Computer Specs:
-HP Pavilion 2000
-320gb HD
-3gb RAM
-AMD A6 Vision 64bit processor
-Pre-installed Windows 7 home premium
I used the windows installer for version 12.something. Installation didn't come up with any problems. When I rebooted the computer I selected Ubuntu and it started doing the "loading for first time start up" or something. Then it said "An error occurred while mounting /" S to skip M to fix manually. Now I've gone through this multiple times trying to skip through all the errors and pressing M, they both eventually lead to a command line area. I've seen Ubuntu boot up before and I'm pretty sure that this isn't supposed to happen. Anyway in the command line I tried a few commands that I found through researching this problem on the internet. They returned with "read only file system" trailing many lines of activity. I need an experienced user to walk me through this as no one else in the forums seems to have the same problem I am having, and the people who have similar problems have too complicated answers for a beginner like me to follow. Please help ! ! If you need any more information just let me know. Thanks !

---

### Post by grahammechanical on 2013-08-22
Sometimes the least complicated method is to re-install, especially if the installation is new. That may be more compluicated in your case because you are using the Windows installer (Wubi). So, you should un-install Ubuntu as you would un-install any other Windows application. And try again.

Have you tried waiting after seeing that message instead of either pressing S or M? The read only file system issue is correct. We get to a command line prompt but the loading process has not progressed far enough to allow us to write to the file system which we would need to do in order to edit configuration files.

First, you need to identify what is causing the error. Running commands in the hope that it may fix the problem is not wise. We might do more damage. Do you see a boot menu? Do you see Recovery Mode? Try running that and selecting Resume at the recovery mode menu. That may get you to a desktop.

There is also a Recovery mode option of fsck = Check all file systems. That may give more information and even offer to fix things.

Regards.

---

### Post by dylan4 on 2013-08-22
Okay so I reinstalled it and nothing changed.
I waited after seeing the message for more than 20 minutes (it's still going now).
I don't know what you mean by boot menu or recovery mode.
Also, I don't know if this will help but right before the purple Ubuntu screen shows up there is a black screen that says something about a "prefix"?

Pressing escape at the loading screen shows this:
-Generating locals. . . 
-    en_US.UTF-8. . . up-to-date
-Generation complete.
-update-initramfs: deferring update (trigger activated)
-/usr/sbin/grub-mkconfig: 250: /usr/sbin/grub-mkconfig: cannot create /boot/grub/grub.cfg.new: Read-only file system
-fsck from util-linux 2.20.1
-/dev/loop0:recovering journal
-/dev/loop0:clean, 147360/2271232 files, 2670541/18169856 blocks
-mount: cannont remount block device /dev/loop0 read-write, is write-protected
-mountall: mount / [849] terminated with status 32
-mountall: Filesystem could not be mounted: /
-Shadow passwords are now on.

This had been looping for about an hour during the loading process. Perhaps whatever the problem is will make itself clear through this log?

---

