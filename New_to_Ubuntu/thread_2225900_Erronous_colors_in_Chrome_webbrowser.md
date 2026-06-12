---
title: "Erronous colors in Chrome webbrowser"
date: 2014-05-24
forum: New to Ubuntu
---

### Post by Hankbonk on 2014-05-24
I'm running Ubuntu 12.04 LTS .  Since the last update from the Update Manager, my Chrome browser is displaying incorrect colors :  My unopened tabs are deep blue, in Facebook the top bar is light green in stead of blue and so on... .  Also all displayed characters are almost unreadable .  What can I do to fix this ?

---

### Post by dan107 on 2014-05-24
Does it work normal with a different browser? What graphics card do you have? Do you know how to find which driver you have installed for the graphics driver?

---

### Post by Hankbonk on 2014-06-20
Dear dan107,

I don't have any problems with Firefox, besides the fact that the Adobe Flash Player doesn't run in Firefox .  So I don't know why I should try to find out which graphic card I use and which driver is installed, because all other programs beside Google Chrome display the correct colours .  I have attached a screenshot of Chrome to show how bad it is .

---

### Post by a_s on 2014-06-29
I have this exact same issue: performed update (using update manager), now Chrome shows weird images (like it is only using 256 colors) and blurry fonts.  Firefox looks fine.  I too wonder why graphics card information would be important since one program (Firefox) is working find and other is not (Chrome).

Some other details in my case: I ran update manager as non-root user (was prompted for elevated password during process however), host is Dell Optiplex GX20 (old)

Issue for me was that I had a website that was not behaving correctly with old version of Chrome (nor was Firefox).  After update I have all features I wanted from the website (with Chrome) but also have reduced color set and blurry fonts.:mad:

Anyway, was there any resolution to this?

---

### Post by a_s on 2014-07-02
BTW, it turned out my issue was with my integrated Intel graphics card - everything looks great now when I used step described here to create a xorg.conf file: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1173649](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1173649)

---

