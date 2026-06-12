---
title: "[SOLVED] Problems with windows installer"
date: 2013-12-06
forum: New to Ubuntu
---

### Post by mczonie2 on 2013-12-06
I'm trying to use windows installer, but I'm getting a message that says "Cannot install C:\ubuntu. There is another file or directory with this name. Please remove it before continuing. For more information, see the log file c:\users\michael\appdata\local\temp\wubi-12.04.3-rev279.log. 

Earlier, I was farting around with an old ubuntu cd, trying to install that way, and I think that might be the cause. Can anyone help? I'm running windows 8.1, btw.

---

### Post by bcbc on 2013-12-07
Delete c:\ubuntu (or rename it if there's something in there you want) and then try again

---

### Post by 3rdalbum on 2013-12-07
The Windows-based installer is no longer supported - don't use it, it can cause some problems, especially on Windows 8 computers.

Please just boot the CD and install Ubuntu that way.

---

### Post by fantab on 2013-12-07
The post above makes it abundantly clear that Windows Ubuntu Installer, WUBI is NOT supported anymore.
Install Ubuntu as real dual-boot. 

If you have Win8 pre-installed with EFI booting then read the following before you commit install:
[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by mczonie2 on 2013-12-07
> **3rdalbum said:**
> The Windows-based installer is no longer supported - don't use it, it can cause some problems, especially on Windows 8 computers.


Yeah, I just noticed it sez on the windows installer page that you can't use w/ windows 8.

> **3rdalbum said:**
> Please just boot the CD and install Ubuntu that way.

OK, but how do I boot from the CD on Windows 8.1? Doing the F12 thing isn't working. Also, the CD I have is several years old. Will it still work?

---

### Post by fantab on 2013-12-07
How old? Older CD will probably NOT work.

You must first download (preferably via bittorrent) the latest version of Ubuntu from **[HERE]("http://www.ubuntu.com/download/desktop")**, and the Torrent is [**HERE**]("http://www.ubuntu.com/download/alternative-downloads"), then Burn it to DVD or USB 'pendrive' ('How to Burn' instructions are on the same page).. and proceed with install. 
Also go through the LINKS I had shared in my earlier post.

I suggest you install Ubuntu 13.10, as it is the latest and deals better with UEFI and Win8.

---

### Post by Resistent on 2013-12-07
Windows 7 Starter killed my WUBI folder.. I could not start it any more.. A more GB file was only 0 KB big..
 another time Windows Vista, compressed the WUBI folder, so it did not work any more, till I decompressed the folder..

Really really better to have it on a separate Partition and not as Windows Program (what now don't work any more).
Dont let Windows work on Ubuntu ! :-)

---

