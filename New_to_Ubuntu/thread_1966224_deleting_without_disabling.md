---
title: "deleting without disabling"
date: 2012-04-26
forum: New to Ubuntu
---

### Post by mitsi on 2012-04-26
wanting to safely removing Software like gwibber and I got a message
 "If you Uninstall gwibber social client future updates will not include new items in the Ubuntu desktop set. are you sure you want to continue ?
what I want to know is does that mean I will not get updates for ?  the desktop ? Ubuntu  ? or just for gwibber ?
Am I just a bit tired or paranoid about disabling something that should be left alone . Any help would be good ,Thanks in advance.

---

### Post by dolphin194 on 2012-04-26
This simply means that if you update Ubuntu, Gwibber will not be updated/installed.

---

### Post by mitsi on 2012-04-26
Haa yea that makes sense ,thanks for the reply think I need to take a walk outside ,of course that it wont update  only that particular software , gee mabee I am tired ,I'm treading very lightly ,I have read what other newbies have done   and really thank-you for the speedy reply ,lovin my coffee

---

### Post by Krytarik on 2012-04-27
> **mitsi said:**
> wanting to safely removing Software like gwibber and I got a message
 "If you Uninstall gwibber social client future updates will not include new items in the Ubuntu desktop set. are you sure you want to continue ?"
Actually, this tells me that you are running Oneiric 11.10, where, unfortunately, Gwibber is a 'dependency' of the "[ubuntu-desktop]("http://packages.ubuntu.com/oneiric/ubuntu-desktop")" [metapackage]("https://help.ubuntu.com/community/MetaPackages") - removing that may lead to issues if either the dependencies of the Oneiric version of that metapackage are changed, meaning additional packages would need to be pulled in for the desktop to work properly, though this scenario is rather unlikely; or if you upgrade your installed system to the next version of Ubuntu, in this case it's rather *likely* to break your desktop!

Regards.

---

### Post by mitsi on 2012-05-03
Thanks for the help Krytarik ,don't want to disable or break the desktop Cheers

---

