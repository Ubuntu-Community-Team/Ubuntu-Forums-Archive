---
title: "Photoshop Elements 6--Major Issues"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by seuzy13 on 2008-06-04
Okay, so I've been trying to get PSE6 to work without having to boot into Windows, b/c it's honestly just about the only reason I can think of that I still have Windows around. I have tried a number of different methods and they have all failed in some form or another, so I figure if I list them all here, someone will know how to fix at least one of them.

1. PSE under Wine
[The Wine AppDb]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=9868") lists PSE6 tests under Ubuntu. I have found that I have the same issue of not being able to pass the registration window. None of the buttons do anything, and you have to kill the process. All the files have been installed, though. When you click on the .exe, nothing happens. It loads for a few seconds then stops.

2. PSE in virtualbox with XP guest
This was a problem, because I do not have an XP install CD (though I do have it installed on this very same laptop in another hard drive partition). I heard that you can generate an install CD from the i386 folder in XP, but I couldn't find any useful information on this. I also have an XP recovery partition. I found the file "BootDisc.iso" on it and burned it to a CD, but when I ran the CD in virtualbox, I was told to insert the first restore CD (which I don't have).

3. PSE in virtualbox with openSUSE guest
If you'll refer back to the AppDB link above, you'll find that openSUSE had some satisfactory tests for PSE6 under Wine. I installed it as a guest on virtualbox, but I am met with problems when it comes to installing Wine.

   a. Download wine from internet while in guest OS
     I enabled wired internet connection for my virtual machine and   plugged it into my router. No go.

   b. Download wine on host and share files with guest
     I enabled file sharing for my Desktop folder, but can't seem to find it anywhere, and I'm under the impression that you have to install "guest additions" on your guest OS in order to share files. I have no idea what guest additions are, and if I have to download them or not, which would lead me straight back to my internet problem.

   c. Put the wine .rpm on a flash drive and plug it in while on the guest OS
     This didn't work for two reasons:
        1. A popup told me "Not permitted to open the USB device, check usbfs options." I was able to boot up with out this problem on my second try, after I used a fix on [this thread]("http://ubuntuforums.org/showthread.php?t=393582"), but it didn't work on my third try when I plugged it in *after* booting.
        2. I'm not positive where the file for the drive is, and where I should mount it. However, I think [this article]("http://www.tuxmachines.org/node/14376") should help if I ever get past the dialog box in #1

What all this adds up to is something's gotta give sooner or later. Any ideas for other methods, or ways to eliminate the problems with the ones listed here? Thanks a bunch!

EDIT--As a side note, I'd really like to get this working before I leave on vacation Friday. I imagine, I'll be wanting to do a lot with the pictures I take in Photoshop, but I've gotten cozy on Linux and don't want to boot into Windows if I can help it.

---

### Post by Xiong Chiamiov on 2008-06-05
I don't know about many of your problems, or of a direct solution, but the guide [here]("http://www.howtohaven.com/system/createwindowssetupdisk.shtml") seems pretty comprehensive in how to create a bootable Windows iso.

---

### Post by Paqman on 2008-06-05
Wine-doors is a pretty reliable way of getting Wine aps installed. You can get it from GetDeb ([wine-doors on GetDeb](http://www.getdeb.net/app/Wine-Doors)) and use it to install Photoshop CS2.

There's always GIMP, too. Installed by default, and can do most things Photoshop does.

---

### Post by seuzy13 on 2008-06-05
Thanks both of you. I will try both of these out and see if I come up with a solution. I will probably post here again later. If anyone else has other ideas feel free to post. Thank you!

---

### Post by timbellomo on 2008-12-17
suezy--

See my posts on the Wine AppDB.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9868](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9868)

You can rename adobe_registration.dll to skip the reg. screen, but there are some other tweaks you still need to do.

All in all, it *works*, and pretty well, but it's not flawless.  Still, though, it runs *about* as good as on Windows (which for me was never very good anyway -- it chokes on my 25K+ photos)

-Tim Bellomo

---

### Post by seuzy13 on 2008-12-17
Thanks. I forgot about this thread, but I did actually get it to work and posted my test results of it on the Wine appDB along with how I got it to work. I *did* have to rename the adobe_registrationg.dll, and that helped tremendously. It works okay for me, but not necessarily "*about* as good as Windows."

Thanks for the tips though! :)

---

