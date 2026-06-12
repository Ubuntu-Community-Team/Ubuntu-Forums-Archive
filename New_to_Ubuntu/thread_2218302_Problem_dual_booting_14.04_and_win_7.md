---
title: "Problem dual booting 14.04 and win 7"
date: 2014-04-20
forum: New to Ubuntu
---

### Post by Gerry_Graves on 2014-04-20
I had installed the final beta of 14.04 and was happily dual booting with Win7. After the official release, I decided to try unity 8. After installing this, I got a black screen on Ubuntu startup, and the only thing I could do was to re-install. This went fine except that I could no longer boot into Windows. Tried boot-repair which didn't work, even with all the help about using the saucy version. I then reinstalled Win7 which, of course, screwed up grub again. Used boot-repair again, which now only gives me Ubuntu again. Please help a very frustrated user!

---

### Post by Frogs Hair on 2014-04-20
Unity8 though in the repository is experimental at this point and should only be used on a test machine. Boot-repair has not been updated for 14.04 and one of the moderators here has contacted the developer. Though I dual boot all I haven't installed Windows after Ubuntu and updating grub has always solved any problems.

---

### Post by Gerry_Graves on 2014-04-21
Went to install Gparted and Debconf started up. This asked me to confirm where I wanted Grub so I selected all available drives and after this completed, I now have dual-boot working. No idea why but I'm happy. I can use Ubuntu for all my stuff except games where I still have to use Windoze.

---

