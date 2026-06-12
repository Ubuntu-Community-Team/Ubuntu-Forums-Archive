---
title: "Just a few Ubuntu woes!"
date: 2012-09-04
forum: New to Ubuntu
---

### Post by Pharaoh1 on 2012-09-04
[SIZE=2]Hi, I don't know if anyone has had this problem or not because I cannot find any documentation on the subject here or elsewhere. At least after a weeks worth of browsing anyway.  I would like to know why I can't seem to get Ubuntu 12.04.1 LTS to recognize my legacy ATI All-in-wonder 7500 series graphic card.  I understand there have been some problems with ATI graphics cards but there doesn't seem to be any fixes for it. That being said I have a fresh install of the above OS on a WD 20gb hard drive running as master and a 1TB Seagate USB drive and also a 40gb WD drive running WinXP as a slave for the moment.  Upon trying to install to another drive I had the install bombed and I lost my access to my windows drive which is my other problem I need to desperately fix. I downloaded and ran Boot-Repair which gained me access to the boot loader but when I click on my XP drive it says that I need to replace or fix a hal.dll file which I am also at a loss for doing. You would think that after 17 years of building computers and messing with different operating systems I would have learned simple file replacement commands but I would just choose to reinstall the OS usually if I had a backup which this time I do not. Sorry, I know this is a lot to address but those are my issues at this time. Any help would be appreciated in the form of a walk-through if terminal is used. Thanks[/SIZE]

---

### Post by BBQdave on 2012-09-04
> **Pharaoh1 said:**
> [SIZE=2]I can't seem to get Ubuntu 12.04.1 LTS to recognize my legacy ATI All-in-wonder 7500 series graphic card... and also a 40gb WD drive running WinXP as a slave for the moment.[/SIZE]

First off, the Windows XP recovery disk might be your best shot for salvaging XP.

Second, it appears you are on older hardware, so I would recommend Debian 6 (Gnome 2 with backports).

Debian 6 is rock solid on older hardware (and memory friendly). Another option is Fedora 16 Xfce, I have F16 running smoothly on old and new hardware. Directly put, Unity and Gnome 3 to not play well with older hardware. Xfce or Gnome 2 (Debian 6) is a good match for older hardware (running WIndows XP).

---

### Post by DogMatix on 2012-09-04
I don't know if you have already found this but this may help you with the hal.dll troubles [>>link<<]("http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm")

It sounds similar to your situation.

---

