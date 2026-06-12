---
title: "[SOLVED] Kernel Panic After Upgrade to 8.10...Help"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by sillyboy on 2008-11-08
I got this message when I rebooted after upgrade to 8.10.


"Starting up...
[ 0.708121] Kernel Panic - Not Syncing:VFS: Unable to mount root FS on unknown -Block(0,0)".  Also the cap and scroll locks were flashing. 

Ubuntu is the only OS on my other computer, and every thing was great till the upgrade. 

I'm using my windows machine to access this forum.


I need easy and clear directions to solve this problem, after all I am in the Absolute Beginner Talk forum.

A thousand thanks...

---

### Post by baruch60610 on 2008-11-08
You might consider burning a CD for 8.10, and then booting from it as a 'live CD' (that is, don't install from the CD, just use it to snoop around on your hard drive).

There is a helpful article here:

[http://www.linuxforums.org/forum/redhat-fedora-linux-help/68597-kernel-pannic-not-syncing-vfs-cannot-open-root-device.html](http://www.linuxforums.org/forum/redhat-fedora-linux-help/68597-kernel-pannic-not-syncing-vfs-cannot-open-root-device.html)

You may be able to get a better idea of what the problem is by observing any messages that come up as the computer starts up.  There could be some error messages or something that shows the system is behaving in an unexpected manner.  For example, it might tell you it can't find a hard drive, or that a file or program is missing, clues such as this.

Without more information, I don't know what else to look for.

As for snooping around, this is a bit complicated.  If you're familiar with the command line, you can try to view (and possibly edit) the file at /boot/grup/menu.lst.  Don't play around with this file unless you know what you're doing.  A mistake here could render your computer unbootable.

If you don't have any precious, unsaved files on this computer, consider using the 8.10 CD to just install Linux from scratch.  You'll lose everything on the disk if you do it that way, however.

---

### Post by sillyboy on 2008-11-08
> **baruch60610 said:**
> You might consider burning a CD for 8.10, and then booting from it as a 'live CD' (that is, don't install from the CD, just use it to snoop around on your hard drive).

There is a helpful article here:

[http://www.linuxforums.org/forum/redhat-fedora-linux-help/68597-kernel-pannic-not-syncing-vfs-cannot-open-root-device.html](http://www.linuxforums.org/forum/redhat-fedora-linux-help/68597-kernel-pannic-not-syncing-vfs-cannot-open-root-device.html)

You may be able to get a better idea of what the problem is by observing any messages that come up as the computer starts up.  There could be some error messages or something that shows the system is behaving in an unexpected manner.  For example, it might tell you it can't find a hard drive, or that a file or program is missing, clues such as this.

Without more information, I don't know what else to look for.

As for snooping around, this is a bit complicated.  If you're familiar with the command line, you can try to view (and possibly edit) the file at /boot/grup/menu.lst.  Don't play around with this file unless you know what you're doing.  A mistake here could render your computer unbootable.

If you don't have any precious, unsaved files on this computer, consider using the 8.10 CD to just install Linux from scratch.  You'll lose everything on the disk if you do it that way, however.


Is it possible to reinstall 8.04 over top and retain my saved stuff, or doing this is like doing a reinstall of Windows?

Thanks

---

### Post by phidia on 2008-11-08
> **sillyboy said:**
> Is it possible to reinstall 8.04 over top and retain my saved stuff, or doing this is like doing a reinstall of Windows?

Thanks

Yes you can elect not to format the install partition but it may not work correctly. You best bet is to back up your data and in the next install create a separate home partition so that future installs will be easier.

---

