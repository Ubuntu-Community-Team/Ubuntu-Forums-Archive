---
title: "HELP with my wifi card !!"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by B34ST1Y on 2008-11-18
help! I installed ndiswrapper to get my Dynex wireless G usb adapter (wifi) working...but I cant seem to activate it. It's the official driver from the website, but when I use ndisgtk, it says the hardware was not found. 

Any help at ALL would be greatly appreciated :)

---

### Post by bumanie on 2008-11-18
I think you just need to get the **.inf** file for ndiswrapper to work - if that's what you have already done, I don't have any other suggestion.

---

### Post by ja660k on 2008-11-18
as the earlier post said, you need the .inf file,
if you dont like to use the cmd line 

try 
```

sudo apt-get install ndisgtk

```

thats a gui that is a little easier to work with

---

### Post by B34ST1Y on 2008-11-18
ja660k, i've installed that...and used it to install my official driver. However, it says that the hardware is not present, even after I install the correct .inf file.

---

### Post by ja660k on 2008-11-18
hrmm... this is strange

can you reboot and right after run this cmd
```
sudo dmesg
```
and
```
 ndiswrapper -l 
```
and pst results?

---

