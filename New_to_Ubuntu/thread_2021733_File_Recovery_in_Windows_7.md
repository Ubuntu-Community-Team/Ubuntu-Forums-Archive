---
title: "File Recovery in Windows 7"
date: 2012-07-09
forum: New to Ubuntu
---

### Post by TopographicOceans on 2012-07-09
TopographicOceans

If ubuntu can boot from a live USB can it access a windows 7 file system and move files from windows 7 to the flash drive or cd/dvd in the event of a crashed windows 7 operating system?

---

### Post by Kopkins on 2012-07-09
Yes, if you boot from a live cd or usb (ubuntu) you can access the windows filesystem. 

If you boot to the desktop on a live cd/usb, go ahead and open up the file manager (the orange folder near the top-left of the screen.)

In the top left of the file manager window that opens, there should be a list of devices. Your windows partition should be there. You can click on it and open the windows hard drive from there. 

If this doesn't work, you will have to mount the partition manually.

Press the windows key, then type 'terminal' and press enter. In the terminal use the following commands to mount your windows partition.

```

mkdir windows

sudo mount /dev/sda1 windows

```

Now, open up the file manager again and navigate to the windows folder.  If you don't find your files there, you have to try another partition. Do the following.
```

sudo umount windows

sudo mount /dev/sda2 windows

```

Open the file manager again and see if your files are there. 

Good luck, and welcome to the forums.

Kopkins

---

### Post by TopographicOceans on 2012-07-10
Thanks for the information. It looks like I have a lot of research to do.

What I am most interested in is Windows 7 recovery tools such as Microsoft Dart 6.5. Here is the URL:

[http://technet.microsoft.com/en-us/library/ee532075.aspx](http://technet.microsoft.com/en-us/library/ee532075.aspx)

I'm wondering if I can run these diagnostics under ubuntu.

---

### Post by Kopkins on 2012-07-10
You may be able to run them under wine. Wine is a compatibility layer for ubuntu that lets you run many windows programs. 

On the other hand, ubuntu has many useful tools available. I have this page bookmarked in case anything every goes awry.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

EDIT: just looked at your link. I'm unfamiliar with DaRT so I could be wrong, but it looks like it is a program that builds a bootable CD which contains those tools. I'm unsure how you would get those tools outside of that program/CD.

Kopkins

---

