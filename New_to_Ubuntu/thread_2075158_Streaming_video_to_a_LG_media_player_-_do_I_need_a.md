---
title: "Streaming video to a LG media player - do I need an NTFS partition?"
date: 2012-10-23
forum: New to Ubuntu
---

### Post by Lorq on 2012-10-23
Hi,
(Almost) absolute linux noob here. After fubaring my Windows partition, I decided to install Ubuntu as my main OS, annoyed as I was that Windows doesn't recognize half my hardware after a clean install.

My question now is this: I use a LG DP1W media player to play videos on my pc over the network (cabled). It sees the share I made in Ubuntu, it sees the files (MKV, M4V, AVI, whatnot), but says that the file format is not supported when I try to play them. (it used to work fine under Windows).

Am I correct in assuming that I need an NTFS partition for this to work? I'm guessing the LG device can't really handle the file system, but I wonder why it does 'see' the files then.

If so: I (foolishly) decided to install Ubuntu on one big partition on my HD. I've done some searching, but there does not seem to be a way to resize it and add a new partition, without having to reinstall the whole thing again. Is that correct?

Thanks for any tips.

Edit: I forgot to mention: it's Ubuntu 11.10, on an Intel Pentium 3.40 Ghz dual, 32-bit.

---

### Post by bart.a on 2012-10-23
You need to use a liveCD or liveUSB and Gparted to change your partition sizes.. You can not do it when your system is active on that partition..

Check [this]("http://www.howtogeek.com/114503/how-to-resize-your-ubuntu-partitions/") link for more info on how to proceed.. 

with your LG.. I don't know how that should work, maybe LG has somthing on it's website about support of linux systems?

Does your LG have read AND write permissions on the share? my media player writes little files on my partitions when I hook it up, maybe your problem is in that region?..

---

### Post by Cheesemill on 2012-10-23
The underlying filesystem doesn't matter, it can be whatever you want. Your LG media player has no way of knowing what the filesystem is, it only knows what Samba is presenting to it.

This sounds like a Samba problem rather than anything to do with filesystems.

---

### Post by Lorq on 2012-10-23
bart.a, thanks for the tip, I'll try that.

Cheesemill, that's what I originally thought as well, so I was surpised when it didn't work. I'll try fiddling with samba some more, although the options presented by the GUI are rather limited. I guess that means I should really learn to use the command line...

---

### Post by Lorq on 2012-10-25
Checking back...this is solved.

I fiddled around some more with Samba, and although I'm not sure what the issue exactly was, I guess it had to do with rights. 

Apparently changing the rights setting to a folder also requires a reboot, because at first it still didn't work. I guess I'm too much of a Windows user still...

---

### Post by bart.a on 2012-10-25
Thanks for reporting back.. Have fun with your system!..

---

