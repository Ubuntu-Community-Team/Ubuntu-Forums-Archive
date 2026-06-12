---
title: "Chromium Flash Update?"
date: 2015-12-30
forum: New to Ubuntu
---

### Post by Daveski17 on 2015-12-30
I usually update the Pepper Flash plug-in on Chromium by uninstalling the old version from the Ubuntu Software Centre and reinstalling the new one. 

[IMG]http://i386.photobucket.com/albums/oo307/Davebucket17/flashc2_zpsr0et9nbo.jpg[/IMG]

I checked on the Adobe page and it claims I am running the 20,0,0,228 version. 

[IMG]http://i386.photobucket.com/albums/oo307/Davebucket17/flashc1_zpselny6rdv.jpg[/IMG]

When I uninstalled 20,0,0,228 from the Centre and reinstalled like I usually do, I find I still have version 20,0,0,228 instead of 20,0,0,267. 

Do I just have to wait until the repo is updated?

Thanks, Dave.

---

### Post by Dennis N on 2015-12-30
The package **adobe-flashplugin** is currently providing 20,0,0,267
Advantage to using this package: automatic updates, supplies latest flash for both Firefox and Chromium browsers.
Enable Canonical Partners repository in software sources to install it.


Or you can wait.

---

### Post by Daveski17 on 2015-12-30
OK thanks. I am up to date with Firefox. I can wait for the repo to be updated for Chromium. I just wondered if anything had gone wrong with the repo updates.

---

### Post by Frogs Hair on 2015-12-30
Pepper Flash is maintained by Google and not Adobe. Using Chrome will ensure the latest version is installed because it updates with the browser. You will have to wait for the repository version to update if using Chromium.

---

### Post by Daveski17 on 2015-12-30
Yes I know, thanks. I just wondered if anything had changed in the manual updating process. I ran Chrome on my old laptop on Ubuntu, so I know it can be installed. I tend to prefer Chromium on Linux though.

---

### Post by Frogs Hair on 2015-12-30
There is a PPA , but it appears to be supplying the same version you are using. 

[https://launchpad.net/~skunk/+archive/ubuntu/pepper-flash](https://launchpad.net/~skunk/+archive/ubuntu/pepper-flash)

---

### Post by Daveski17 on 2015-12-30
> **Frogs Hair said:**
> There is a PPA , but it appears to be supplying the same version you are using. 

[https://launchpad.net/~skunk/+archive/ubuntu/pepper-flash](https://launchpad.net/~skunk/+archive/ubuntu/pepper-flash)


OK, thanks. As long as I can update to 20,0,0,267 when the repo is updated I'll be OK. I've been updating Pepper Flash for Chromium the same way for about 18 months. I'm guessing the holiday period is a factor in the repo not being updated yet. I think it will be safe enough to use 20,0,0,228 for now.

---

### Post by Daveski17 on 2016-01-09
Still no update!

---

### Post by Dennis N on 2016-01-10
> **Daveski17 said:**
> Still no update!

I have it updated to 20.0.0.267 (still the most recent) on Dec 30, so the time seems unacceptably long. If you are not using adobe-flashplugin, you might consider switching.

---

### Post by Daveski17 on 2016-01-11
> **Dennis N said:**
> I have it updated to 20.0.0.267 (still the most recent) on Dec 30, so the time seems unacceptably long. If you are not using adobe-flashplugin, you might consider switching.

It does seem like a long time. I don't understand why it hasn't updated in the repo yet.

---

### Post by Daveski17 on 2016-01-11
I've just received a Chromium update but the repo still isn't updating to 20.0.0.267 yet. Is there something I should know?

---

### Post by Daveski17 on 2016-01-13
I installed Chrome.

---

### Post by Dennis N on 2016-01-14
> **Daveski17 said:**
> I've just received a Chromium update but the repo still isn't updating to 20.0.0.267 yet. Is there something I should know?

Your repo does not seem to be offering timely updates on this. Again, I suggest you follow the directions implied in post #2 - add the source repository (Cannonical Partners), run **sudo apt-get update**, followed by **sudo apt-get install adobe-flashplugin**.

Happiness will be your reward.

---

