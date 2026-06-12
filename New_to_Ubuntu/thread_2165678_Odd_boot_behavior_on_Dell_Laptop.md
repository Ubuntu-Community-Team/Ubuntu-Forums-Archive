---
title: "Odd boot behavior on Dell Laptop"
date: 2013-08-05
forum: New to Ubuntu
---

### Post by Doomspark on 2013-08-05
I have a Dell Vostro 1000 laptop currently running Precise.  I ran Jaunty on it with no problems, and then put Mint on it - again with no problems.  Now I've got Precise on it, and I've got an odd boot sequence that I've never seen before.

Starting from the laptop powered off, when I turn it on the laptop POSTs and then the background goes purple - the same as the Ubuntu splash screen / grub.  But the splash screen never displays and grub doesn't load.  I left it in this state for a couple of hours, so I'm pretty sure it isn't just a matter of waiting.

At this point, if I press CTRL-ALT-DEL,  the laptop POSTS again and this time the splash screen displays and grub loads. I press ENTER to start Precise, and get the following:

[https://www.dropbox.com/s/1j2050yuqnywawp/ubuntuerror.jpg](https://www.dropbox.com/s/1j2050yuqnywawp/ubuntuerror.jpg)

Followed in a minute or two by:

[https://www.dropbox.com/s/5sgj87fcma0xnqw/error2.jpg](https://www.dropbox.com/s/5sgj87fcma0xnqw/error2.jpg)

At this point, if I type in "exit" (without the quote marks) and press ENTER, Precise loads and the laptop behaves properly.  I'm using it right now to type this.

The laptop did NOT do this under Mint or under Jaunty. While it's usable, I'd really like to get it to boot properly.

---

### Post by Doomspark on 2013-08-05
In case it is helpful, I installed and ran boot-repair:
[http://paste.ubuntu.com/5953258/](http://paste.ubuntu.com/5953258/)

---

### Post by Doomspark on 2013-08-06
A few other things:
1.  I have installed Precise two or three times on this laptop, using different media, with the same result. 
2.  I haven't tried reinstalling Jaunty.  I don't know if I still have my Live CD for it, and I'd rather not get stuck in "your OS is no longer supported"
3.  I'm not averse to installing an older version of Ubuntu as long as its one that is still supported. If I go this route, it would be with the intention of upgrading to Precise.
4.  I'm also not averse to trying one of the newer versions of Ubuntu - although I really prefer the LTS editions. If y'all think Q or R (don't know the names, sorry) will fix this, I'll install it and report back.

---

### Post by Doomspark on 2013-08-07
Anyone?

I don't know what other information I can provide to help resolve this.

---

### Post by Rob Sayer on 2013-08-07
You may have installed it several times from different media, but did you use the same downloaded .iso?  And did you do an md5sum check on that after downloading?  You may have a bad install iso.  If you try downloading another install iso, use the torrent method (it's more reliable) and always do the checksum.

Did you try boot repair?

---

### Post by oldfred on 2013-08-07
The first error seems to be saying it is having issues with your / (root) partition as that is the UUID given.

I might check in Disks or Disk Utility, click on drive and see what smartctl says about drive. It may be getting errors.

I might also run a full fsck from a liveCD.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

