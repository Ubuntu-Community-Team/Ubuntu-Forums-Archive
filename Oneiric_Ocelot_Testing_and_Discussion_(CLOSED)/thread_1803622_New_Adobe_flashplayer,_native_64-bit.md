---
title: "New Adobe flashplayer, native 64-bit"
date: 2011-07-13
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-07-13
There is a new Adobe flashplayer plugin for download.
This is the native 64-bit version (11.0.1.60 beta1).

> 
Adobe® Flash® Player 11 desktop beta drives innovation for rich, engaging digital experiences with new features for cross-platform browser-based viewing of expressive rich internet applications, content, and videos across devices. Some of the features from the Flash Player Incubator, such as Stage 3D and 64-bit support, have been moved into this beta release.


Here:
[http://labs.adobe.com/downloads/flashplayer11.html](http://labs.adobe.com/downloads/flashplayer11.html)

I use manual installation.
Just copy the libflashplayer.so file into browsers plugin directory:

Chromium
/usr/lib/chromium-browser/plugins/

Firefox
/usr/lib/mozilla/plugins/

---

### Post by jfernyhough on 2011-07-13
Nice. Keeping an eye on the Sevenmachines PPA which has the previous version.

[https://launchpad.net/~sevenmachines/+archive/flash](https://launchpad.net/~sevenmachines/+archive/flash)

---

### Post by jppr on 2011-07-13
Just installed that new flash player in Windows 7 system and works very well :popcorn:
In 11.10 I don´t have test it yet :) I think that haven´t so soon in 11.10 repos...

---

### Post by lovinglinux on 2011-07-13
Just updated [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") to get the new Flash 11 Betas, for both 32bit and 64bit. If you already use Flash-Aid, all you need is to execute the Wizard to install. Hardware acceleration and the performance tweak "Override GPU validation" is working on YouTube again. No more black screen.

If you already use Flash-Aid, you probably will receive an alert tomorrow, since it only checks for updates once a day. But if you run the Wizard today, you can ignore that alert.

---

### Post by mikewhatever on 2011-07-13
Impressive. I wasn't expecting a beta this year.:twisted:

---

### Post by lovinglinux on 2011-07-13
> **mikewhatever said:**
> Impressive. I wasn't expecting a beta this year.:twisted:

Me neither, specially considering the age of the 64bit square preview. This is great news.

---

### Post by cpatrick08 on 2011-07-13
> **jfernyhough said:**
> Nice. Keeping an eye on the Sevenmachines PPA which has the previous version.

[https://launchpad.net/~sevenmachines/+archive/flash](https://launchpad.net/~sevenmachines/+archive/flash)

sevenmachines updated it now

---

### Post by agent8131 on 2011-07-14
sevenmachines ppa seems to be broken:

> install: target `/usr/lib/kde4/' is not a directory: No such file or directory
dpkg: error processing flashplugin64-installer (--configure):
 subprocess installed post-installation script returned error exit status 1

---

### Post by yermet on 2011-07-14
Yes, same here.

---

### Post by SecretCode on 2011-07-14
Same error here. Who has a Launchpad account to report the bug? I don't see any bug report yet.

---

### Post by jeegiz on 2011-07-14
Could not find in launchpad which package to report bug, instead sent email to seven machines on this issue.

---

### Post by jeegiz on 2011-07-14
The issue seems to be caused by following script:

/var/lib/dpkg/info/flashplugin64-installer.postinst

101 line is failing:
install -m 644 usr/lib/kde4/kcm_adobe_flash_player.so /usr/lib/kde4/

My workaround was to comment this line :-)

---

### Post by SevenMachines on 2011-07-14
Sorry, late night effort. should be ok now (~sevenmachines3) for people who are completely free of kde bits ( really, you dont have kcachegrind! :)) Flash itself seems better, it has been several months i suppose

---

### Post by jeegiz on 2011-07-14
That was quick! :-) Thank you for the fix - tested, working smoothly.

---

### Post by SevenMachines on 2011-07-14
> **jeegiz said:**
> That was quick! :-) Thank you for the fix - tested, working smoothly.
No worries, the magic of the first morning coffee

---

### Post by kmustkivi on 2011-07-14
Got the same error in Xubuntu 11.04 (64-bit). Solved by a hack of creating two symlinks: one under the /usr/share/ and another /usr/lib/. In both cases linked kde4 -> xcfe4.

After that sudo apt-get upgrade installed the 64-bit flash player package.

---

### Post by Quackers on 2011-07-14
I used Harry33's manual method. All seems good :-)

---

### Post by SecretCode on 2011-07-15
SevenMachines' ppa now working again

Thanks!

---

