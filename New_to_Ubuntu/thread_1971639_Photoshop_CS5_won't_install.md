---
title: "Photoshop CS5 won't install?"
date: 2012-05-02
forum: New to Ubuntu
---

### Post by d4m1r on 2012-05-02
Hey guys, I am new to using Wine (using v1.4) and I am trying to install Adobe Photoshop CS5 within my Ubuntu partition and the installer does launch, but returns an error:

[IMG]http://i.imgur.com/AnEcql.png[/IMG]

-Multiple other people have confirmed it working under Ubuntu on WineHQ
-Have set Wine to XP mode
-Have installed 2 specific DDLs required
-Ran  "winetricks msxml6 gdiplus gecko vcrun2005sp1 vcrun2008 msxml3 atmlib" prior to installing
-Using the official trial .exe from adobe.com
-Used the default directory
-Exe was marked as executable


Am I missing something?

---

### Post by d4m1r on 2012-05-02
Solved!

No idea why, but it appearently can't be installed the traditional method....files, folders, and a registry file have to be copied over from your Windows install. Maybe because of 11.10? Maybe because of 1.4?

Anyway, find the guide on how to do it [HERE]("http://www.thetechrepo.com/main-articles/567-how-to-install-adobe-photoshop-cs5-in-ubuntu-linux-using-wine").

---

