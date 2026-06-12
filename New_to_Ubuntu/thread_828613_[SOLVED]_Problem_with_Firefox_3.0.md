---
title: "[SOLVED] Problem with Firefox 3.0"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by Bix in Austin on 2008-06-13
I am now unable to use Firefox since the last upgrade download earlier this week. I am now getting the following error message:

An Error occured. The following details are provided:
E:/var/cache/apt/archives/sulrunner-1.9_1.9~rc1 +nobinonly-Outbuntu 1~8,04,2_i386.deb: short read inbuffer_copy (backend dpkh-deb during `./user/lib.sulrunner-1.9.libmozijs.so') .
This has happened sinced I downloaded and installed an update earlier this week. I have tried to follow the instructions to find the problem but since I don't know what I am looking for I am not making much progress. I have the 8.04 Ubuntu installed. I the process of trying to find the problem I no longer have Firefox available. Is there any help our there for me?
Bix in Austin.
[email]mcpea65@gmail.com[/email]

---

### Post by spiderbatdad on 2008-06-13
My personal favorite: Go to synaptic package manager. Install:

iceape
iceape-browser
iceape-calander
iceape-dev
iceape-gnome-support

This install the seamonkey browser suite. Then the iceape packages can be removed.

Seamonkey is highly configurable and has same security plugins as firefox...they are sibling browsers.

The interface is slightly different and takes a little more getting used to. First highly recommended plugin is monkey-menu. It lets you configure the tool bars. Also NoScript is a good choice.

If you do install seamonkey, go to about:config in the address bar and find ul_platform file picker...set it to false.

Screenshot of the seamonkey browser tool bars:

---

### Post by Bix in Austin on 2008-06-15
Thanks for your reply. 
Bix in Austin

---

### Post by MasterSander on 2008-06-15
or you can try to uninstall firefox and reinstall

---

### Post by markbuntu on 2008-06-15
Yes, reinstallation is the best idea.
Opera 9.50 is out also if you want to try it.

---

### Post by kansasnoob on 2008-06-15
From what I've seen FF3 RC1 seems pretty good. RC2 is not ready for prime time. Oddly it's hard to tell the difference, but if you receive "Hardy Proposed" updates you're likely to have RC2.

---

### Post by Bix in Austin on 2008-06-16
Thanks to all for your suggestions. I have the problem solved thanks to VOR.

---

