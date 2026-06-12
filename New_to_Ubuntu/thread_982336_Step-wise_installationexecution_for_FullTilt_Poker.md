---
title: "Step-wise installation/execution for FullTilt Poker client (first-time ubuntu user)"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by tberli on 2008-11-14
Hello, I downloaded Ubuntu today. I think it's great,great potential, forum is very helpful and polite, no matter how stupid my questions are.

I am prepared to do alot of reading the next couple of days getting to know the operation system. But I want to ask someone a favour: Please explain how I can download, install and run the FullTilt Poker client in Ubuntu.
I'm desperate (FTOPS). Please provide a dummy guide from scratch :)

i tried running an .exe file from my externaldrive, like I used to do when having windows, but now I got the error: "An error occurred while loading the archive".

Command line output:
 [/media/IOMEGA_HDD/Ubuntuuorga/Full Tilt Poker/FullTiltPoker.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/IOMEGA_HDD/Ubuntuuorga/Full Tilt Poker/FullTiltPoker.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/IOMEGA_HDD/Ubuntuuorga/Full Tilt Poker/FullTiltPoker.exe or
          /media/IOMEGA_HDD/Ubuntuuorga/Full Tilt Poker/FullTiltPoker.exe.zip, and cannot find /media/IOMEGA_HDD/Ubuntuuorga/Full Tilt Poker/FullTiltPoker.exe.ZIP, period.

---

### Post by DieB on 2008-11-14
for windows programs you need [WINE]("http://www.winehq.org") - it is also in synaptic/paket-manager or "add/remove applications".

don't know if wine supports your app (for more see [appdb]("http://appdb.winehq.org/"))

there are even some [pokergames]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=poker") in ubuntu - all installable via synaptic/package-manager

hope that helps.

p.s.: looked at their homepage and it seems they only support windows - so try WINE or if you want to try use poker-web (if u get it working write a howto - cause i guess poker is pretty popular nowadays)

---

### Post by tberli on 2008-11-14
omg,it worked,thanks!made my day :popcorn:

---

