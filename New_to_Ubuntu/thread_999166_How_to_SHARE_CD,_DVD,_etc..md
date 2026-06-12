---
title: "How to SHARE CD, DVD, etc."
date: 2008-12-01
forum: New to Ubuntu
---

### Post by Kellemora on 2008-12-01
Hi Gang

In Windows I could SHARE the CD, CD-RW, DVD, etc. with all the machines, even the Ubuntu machines.  They appear in the network folder, but won't mount until I put something in them, then they mount automatically.  If they didn't I would probably be lost there too, hi hi.....

I bought some new hardware and put it into my Ubuntu machine and would like to share those devices with the other users of the LAN and cannot find any way of doing this in Ubuntu.

You can't MOUNT and empty drive either, as far as I can tell.

I really wanted to keep the NEW STUFF in this computer since it's my main one now!  But I can't if others can't use it!

Any ideas or do I need to get yet another WinDOZE machine in order to keep using Ubuntu?  (Sorry for the sarcasm!  I'm trying to get AWAY from the DOZE, not keep adding more DOZE machines in order to use Ubuntu).

TTUL
Gary

---

### Post by scott_g on 2008-12-01
Have you tried installing system-config-samba?

```
sudo apt-get install system-config-samba
```

It should let you choose individual folders (no matter where on your machine) to share.  To share the cd-rom drive, you could either enter /media/cdrom as a location, or create a symbolic link to the cdrom drive in your home partition, and share that:

```
cd ~
ln -s /media/cdrom
```

Not entirely sure if it will work, but its worth a try.

Scott

---

### Post by Kellemora on 2008-12-02
Hi Scott

Thanks for the stab at this!

I'm running several computers here, most of which are running Unbuntu and Samba is what's keeping my LAN up most of the time.

As I replace or upgrade hardware, I'm looking only for products known to work well with Ubuntu.  Figured this would save lots of headaches in the long run!

But so far, each thing I took for granted in Windows because it always just worked with no hassles, has become a total nightmare in Ubuntu.  I have numerous issues that have not been resolved in over 3 months now.  One major issue is I still have to perform a full backup manually each evening because I cannot get the machines to see remote hard drives.  And ironically, my primary reason for switching to Linux was that a hard drive anywhere on the LAN was supposed to be seen as being on the local machine.  Seems that only works in Edubuntu with all thin clients!

Thanks

TTUL
Gary

---

