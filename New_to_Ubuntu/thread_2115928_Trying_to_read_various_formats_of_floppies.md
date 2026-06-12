---
title: "Trying to read various formats of floppies"
date: 2013-02-14
forum: New to Ubuntu
---

### Post by larpingWombatL on 2013-02-14
This is a somewhat involved issue but I figured this was a good place to start as I am new to Ubuntu and Linux.

I am working on a project that involves backing up data on old 3.5" floppies (so far dating back to the early 1990s). I am familiar with a number of different formats that floppies come in: IBM 720k and 1.44mb, Mac 800k and 1.8mb, high density, double density, etc.

The project started with using a USB floppy drive on a Mac running OSX and using Parallels to run Windows 7. Some disks are readable and many are not. Original suspicions were that some or many of those disk that were not readable in the Windows environment were Mac formatted disks. However, almost none of them worked in Mac either.

After some troubleshooting and forums browsing, the next option seemed to be trying to access the disks in a Linux distro and I turned to Ubuntu for its wide usage and support base. I have Ubuntu 12.10 running in Parallels and was able to access some of the disks that had not been accessible in either Windows or Mac environments. Unfortunately, there are still many that do not work in Ubuntu. These disks that are not working in Ubuntu will not mount automatically after insertion (like the ones that work do). After several minutes of idling, when I remove the disk, I get an error message that there is no media to mount.

Some further searching led me to try using terminal commands to mount the floppy disk ("disks --mount /dev/sdb"; sdb is the label the USB floppy drive is given). I received the following error message in the terminal window: 

"Mount failed; Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

I know that there is data on the disk. I just need a way to access it. Any suggestions on alternative solutions would be greatly appreciated.

P.S. I have other options (macdrive software and omniflop with an internal floppy) to try but wanted to experiment with Linux as a free option and to save the trouble of trying to find/put together another machine with an internal floppy setup in order to use omniflop.


EDIT: Several disks that will not mount (either automatically or via Terminal commands) give the following message in the Terminal: "Error mounting: mount: block device /dev/sdb is write-protected, mounting read only mount: /dev/sdb: can't read superblock"

---

### Post by schragge on 2013-02-14
You can try it with [mtools]("http://manpages.ubuntu.com/manpages/precise/en/man1/mtools.1.html").

BTW, can you copy raw data from those floppies with [dd(1)]("http://manpages.ubuntu.com/manpages/precise/en/man1/dd.1.html")?

---

### Post by larpingWombatL on 2013-02-14
Wow, such a quick response. I will check out mtools and see how it goes. Thank you.

---

### Post by grahammechanical on 2013-02-14
Are you aware that those floppy disc could be write protected? In case you do not know about this, turn the disc on to its reverse side with the back edge upright. On the left at the top you should see a square hole. If you cannot see daylight through a square hole then the disc is write protected. There is a slider that you can move upwards. Without that square hole the disk drive will not know a floppy is in the drive. Inside the drive there is a microswitch that pops up into the hole and allows the disc to be accessed.

Regards.

---

### Post by Zill on 2013-02-14
> **grahammechanical said:**
> ...If you cannot see daylight through a square hole then the disc is write protected...
Err... I think it is the other way round. ;-)

i.e. If you *can* see daylight through a square hole then the disc is write protected.

See [http://www.computerhope.com/issues/ch000277.htm]("http://www.computerhope.com/issues/ch000277.htm")

---

