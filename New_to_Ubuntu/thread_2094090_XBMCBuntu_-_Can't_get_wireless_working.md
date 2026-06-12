---
title: "XBMCBuntu - Can't get wireless working"
date: 2012-12-12
forum: New to Ubuntu
---

### Post by mwpeck on 2012-12-12
Running XMBCBuntu on a Zotac Zbox ID41, and the wireless is not working. Zotac has drives in the form of a gzip that needs to be compiled but whenever I try the make command I get permission denied (even when running "sudo make").  Any tips on getting wireless working? Let me know what commands you guys need info from to know what I have and what needs to be done.

---

### Post by mwpeck on 2012-12-12
<Delete please>

---

### Post by mwpeck on 2012-12-12
May be of help in resolving my issue. The Zotac Zbox website does offer Ubuntu drivers for Wireless. They can be downloaded from [here]("http://www.zotac.com/components/gpd_download/Download/count.php?var=1614&driverlink=http://downloads.zotac.com/mediadrivers/mb/download/ubuntu-3.4-rc3-1.tar.bz2").

Despite being labeled as a .tar.bz2, I had to uncompress it as a gzip, not a bz2.  That being said, that's about as far as I've gotten, I have no idea how to install them from this point. I have tried running "sudo make", but I get a permission denied error (after successfully logging into the system via the sudo command), therefore I am stuck. If there is an easier way to do this I would love to hear it.

I am not completely new to terminal commands and know quite a bit about Windows systems, but this is my first major venture into the world of Linux.

Any suggestions on how to install the above driver?

---

### Post by squakie on 2012-12-12
After you've decompressed the file with "keep directory structure", you need to:

- open a terminal window

- cd <the path to the folder it decompressed to>

- chmod +x scripts/*.*

- chmod +x scripts/*

This is because when the scripts were unzipped they weren't given execute permission - that's why you're getting the error.

I downloaded all of this and made it as far as the make - it bombed out due to some function name "err" in the USB information.  I haven't looked further yet.  When I get a little bit of time - possibly tomorrow - I'll try to dig into the source and the make file to see what's happening.

---

### Post by mwpeck on 2012-12-13
> **squakie said:**
> After you've decompressed the file with "keep directory structure", you need to:

- open a terminal window

- cd <the path to the folder it decompressed to>

- chmod +x scripts/*.*

- chmod +x scripts/*

This is because when the scripts were unzipped they weren't given execute permission - that's why you're getting the error.

I downloaded all of this and made it as far as the make - it bombed out due to some function name "err" in the USB information.  I haven't looked further yet.  When I get a little bit of time - possibly tomorrow - I'll try to dig into the source and the make file to see what's happening.
Odd, I followed those steps exactly and I got a slightly different error than before, but not as far as you seem to have gotten:

```
/bin/sh: cannot create /home/xbmc/compat-wireless-3.4-rc3-1/.config: Permission denied

make: *** [/home/xbmc/compat-wireless-3.4-rc3-1/.compat_autoconf_compat-wireless-v3.4-rc3-1] Error 2

```If I try running it with sudo, I get the same general message, but Error 126 instead of Error 2.

---

### Post by squakie on 2012-12-13
Did you decompress all of this into a folder you own?

---

### Post by mwpeck on 2012-12-13
> **squakie said:**
> Did you decompress all of this into a folder you own?
I didn't explicitly check permissions of the folder but I decompressed it into my home directory so I would assume I own it.....I'll double check and get back with you.

Checked permissions and my account was owner of the folder and subfolders. I tried running:

```
chown -R xbmc /home/xbmc/compat-wireless-3.4-rc3-1
```and now whenever I try the make command I still get permission denied but now it is Error 126 (whether I run sudo or not)....even after making sure everything in the scripts folder had execute permission.

---

