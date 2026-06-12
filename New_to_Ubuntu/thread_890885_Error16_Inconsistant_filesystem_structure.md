---
title: "Error16: Inconsistant filesystem structure"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by Spoken on 2008-08-15
so.....as my title reads, this is the error that i receive when i try to boot my computer.  i have tried to boot in pre existing kernels and even recovery modes, and...nothing.

so.. tell me what to do :l

---

### Post by Spoken on 2008-08-15
ahh help!

something tells me its not a hard drive failure, but idk.

---

### Post by oldos2er on 2008-08-15
Boot from the Live CD (if you have one), and run fsck on your partition(s).

---

### Post by Spoken on 2008-08-15
ok i have the live cd, but idk how to run any commands with it, please help me.

---

### Post by Herman on 2008-08-15
:) Hello Spoken,
You can use any Live CD, boot your live CD, open a terminal and run  a command to find out what your Linux partition is called in Linux,
```
sudo fdisk -lu
```The output from that command should give you a pretty good clue if your Linux partition is '/dev/sda2', or '/dev/hdb1', or some other hard disk letter and partition number like that.

Make sure you don't mount the partition or let the Live CD Ubuntu mount the hard disk file system, because we can't run a file system check on a mounted partition (while it is being used). Normally with a Live CD we don't need to worry about that but I'm reminding you just to make sure.

You can run a command something like this one, but you might need to modify it slightly before it will work in your particular computer,
```
sudo e2fsck -C0 -p -f -v /dev/sda2
```Where: sda2 is the ext3 partition to be checked. You can copy and paste this command rather than typing it yourself, that helps avoid operator errors, but you may need to alter the '/dev/sda2' part to some other letter and number.

Normally, that will fix your ext3 file system, if it doesn't, it will give you a message telling you why not.
If that happens, you can proceed with another file system check with different options according to the circumstances, as explained here: [Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem").

Regards, Herman :)

---

### Post by Spoken on 2008-08-15
as i recently found out i cant.  i get this error when i try to boot from the live cd.

can't access tty; just control turned off

---

### Post by Gannon8 on 2008-08-15
> **Spoken said:**
> ok i have the live cd, but idk how to run any commands with it, please help me.

> **Spoken said:**
> as i recently found out i cant.  i get this error when i try to boot from the live cd.

can't access tty; just control turned off

Conflicting posts. Can you boot off the Damn Small Linux CD?

Edit: Gah, Spoken is right. I can't tell which one I'm posting in :P

---

### Post by Herman on 2008-08-15
Try some other Live CD then, any Linux live CD will do the same job, try to use one that is fairly new and up to date though. :)

GParted Live CD, System Rescue CD, Parted Magic and so on are all good Live CDs that are not big downloads and are free.
If you use some other Linux Live CD, you don't use the 'sudo' part in fromt of the command(s).

---

### Post by Spoken on 2008-08-15
i havent tried, i dont have a blank cd.  it shouldnt matter though if my computer cant read my own graphical interface.

---

### Post by Herman on 2008-08-15
What about GParted for USB then? If you take a look in GParted's web page there are other ways to run GParted beides just from a CD, [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php")

Or, you may need to go buy a blank CD and make some kind of Linux live CD out of it and then run e2fsck somehow.

You don't have to have a graphical user interface for running e2fsck, it runs from the command line.
[System Rescue CD]("http://www.sysresccd.org/Main_Page") boots to a command line, I think, and GParted Live CD can boot to the command line if booting the GUI fails.

---

