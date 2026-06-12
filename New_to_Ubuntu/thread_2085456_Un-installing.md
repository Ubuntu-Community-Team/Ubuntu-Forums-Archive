---
title: "Un-installing"
date: 2012-11-18
forum: New to Ubuntu
---

### Post by Robert1305 on 2012-11-18
I wish to remove Dropbox from my PC but I can not remove it by the normal method ie..clicking on remove in software, it just gets so far and no further.

Can it be removed in the terminal mode, if so what is the command.

Regards Bob

---

### Post by mlentink on 2012-11-18
I don't know the proper package name, which you can probably find by browsing for it in Synaptic but then
```
sudo apt-get remove {dropbox-packagename}
```
should work

---

### Post by Robert1305 on 2012-11-18
> **mlentink said:**
> I don't know the proper package name, which you can probably find by browsing for it in Synaptic but then
```
sudo apt-get remove {dropbox-packagename}
```
should work



I tried that and this is the message I got. :(

[IMG]http://i229.photobucket.com/albums/ee246/robert1305/Screenshotfrom2012-11-18120707.png[/IMG]

How do I do that. :confused:

---

### Post by Cheesemill on 2012-11-18
Just do what it's asking you to do. Open a terminal and enter the command:
```
sudo dpkg --configure -a
```

---

