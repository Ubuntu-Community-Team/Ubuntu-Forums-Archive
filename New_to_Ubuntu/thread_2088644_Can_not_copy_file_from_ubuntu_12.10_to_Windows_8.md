---
title: "Can not copy file from ubuntu 12.10 to Windows 8"
date: 2012-11-27
forum: New to Ubuntu
---

### Post by nabid107 on 2012-11-27
Hi.

I am dual booting ubuntu 12.10 and windows 8. When I copy a file from ubuntu 12.10 to windows 8 and then shut down ubuntu and start windows 8, I can not find that file.

Please help.

---

### Post by Stuie675 on 2012-11-27
Have you tried ext2explore?

---

### Post by westie457 on 2012-11-27
Welcome to the Fora

You have run straight into the Windows8 hybrid sleep. That is Windows8 does not completely shutdown so it does not and will not recognise any files written to the partition in that state. So to copy files from Ubuntu to Windows either force Windows to completely shutdown or use a tool such as has already been suggested.
You could also try ext2fsd from here. [http://sourceforge.net/projects/ext2fsd/](http://sourceforge.net/projects/ext2fsd/)
I know this works in Windows7, no idea if it works in Windows8

---

### Post by AstroLlama on 2012-11-27
this is because default windows shut down mode is hibernate. what's happening is that in Hibernation mode any changes to file system get wiped to original (prehibernate) state.

If you want to access the windows partition read/write and have your changed be written to the disk you must power-down windows 8 completely. I dual boot my system windows 8 / ubuntu studio and I created a windows 8 "tile" from directions i found on CNET: [http://howto.cnet.com/8301-11310_39-57392988-285/how-to-create-a-shutdown-and-reboot-tile-in-windows-8/](http://howto.cnet.com/8301-11310_39-57392988-285/how-to-create-a-shutdown-and-reboot-tile-in-windows-8/)

except the command should be "shutdown.ext /s /t 0"

or you could use the /r flag for reboot, but i haven't tested it.

---

### Post by audiomick on 2012-11-27
> **westie457 said:**
> You could also try ext2fsd from here. [http://sourceforge.net/projects/ext2fsd/](http://sourceforge.net/projects/ext2fsd/)
I know this works in Windows7, no idea if it works in Windows8

Also, this does not (yet?) have complete support for ext4.

> ext4 extent read-only, no  size truncating and expanding support

from
[http://www.ext2fsd.com/?page_id=25]("http://www.ext2fsd.com/?page_id=25")

It think that if that does work cleanly on Win8 and you seriously wanted to use it as a matter of course, you should set up a data partition in addition to your Linux install with ext2 or ext3 as the format, not ext 4 as the Ubuntu install uses as standard.

---

### Post by nabid107 on 2012-11-27
> **AstroLlama said:**
> this is because default windows shut down mode is hibernate. what's happening is that in Hibernation mode any changes to file system get wiped to original (prehibernate) state.

If you want to access the windows partition read/write and have your changed be written to the disk you must power-down windows 8 completely. I dual boot my system windows 8 / ubuntu studio and I created a windows 8 "tile" from directions i found on CNET: [http://howto.cnet.com/8301-11310_39-57392988-285/how-to-create-a-shutdown-and-reboot-tile-in-windows-8/](http://howto.cnet.com/8301-11310_39-57392988-285/how-to-create-a-shutdown-and-reboot-tile-in-windows-8/)

except the command should be "shutdown.ext /s /t 0"

or you could use the /r flag for reboot, but i haven't tested it.

thanks.
i will try this.

---

### Post by oldfred on 2012-11-27
Even with Windows 7 and XP users who wrote a lot into the Windows system partition often developed issues. The Linux NTFS driver exposes all the hidden files & folders that Windows hides to avoid accidents, so that is another reason to set the Windows system partition as read only. 
Then create another NTFS data partition for any data you want to share. With my NTFS shared partition I had all photos, Firefox profile, & Thunderbird profile. Then I could use the same data with my Picasa, Firefox & Thunderbird in both systems.
       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

