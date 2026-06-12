---
title: "Adobe no longer supporting Linux?"
date: 2012-09-24
forum: Recurring Discussions
---

### Post by eival on 2012-09-24
ive noticed that Chrome has v11.3.31.232

but Firefox is still at 11.2 r202 which has been the stable release for a while, but now i see this message on the Adobe download site

NOTE: Adobe Flash Player 11.2 will be the last version to target Linux as a supported platform. Adobe will continue to provide security backports to Flash Player 11.2 for Linux.

why is this? and is there anyway to get Firefox to use the updated Chrome pepperflash, or possibly a terminal code to allow us to run the supported Mac version, like other Mac browser plugins

---

### Post by Lars Noodén on 2012-09-24
Flash in general is going away it seems. iPhone, iPad, etc don't support it either.

---

### Post by cwsnyder on 2012-09-24
Check out the method in [http://www.webupd8.org/2011/03/use-google-chrome-built-in-flash-in.html](http://www.webupd8.org/2011/03/use-google-chrome-built-in-flash-in.html)

---

### Post by CharlesA on 2012-09-24
Old news. If you want to continue using Flash on *nix, you are locked to the Pepper API in Google's browser.

---

### Post by eival on 2012-09-24
> **cwsnyder said:**
> Check out the method in [http://www.webupd8.org/2011/03/use-google-chrome-built-in-flash-in.html](http://www.webupd8.org/2011/03/use-google-chrome-built-in-flash-in.html)


that didnt work its still using 11.2

plus that trick was for FF4, the latest stable is 15

i also tried it again cause i notice the directory is different from how he had it, Google created a seperate folder for /PepperFlash/

/opt/google/chrome**_/PepperFlash/_**libpepflashplayer.so

but it still didnt show up, idk if its cause i've already had FF plugins that i manually placed there, for when i use chrome to have multiple flash apps running, i can disable and enable each one, so 1 doesnt effect the other if it crashes, FF doesnt have that ability.


i also could of sworn Flash-Got had the option to use the Chrome flash but that option is no longer an option in its menu, unless perhaps the manual location could be used, does anyone know the direct URL for the pepperflash updates? or what i could put there to have it use the PF version?

[http://i.imgur.com/0z9sJ.jpg](http://i.imgur.com/0z9sJ.jpg)

---

### Post by WinterMadness on 2012-09-24
Adobe is becoming irrelevant anyway. HTML5 > Flash. Soon every video on youtube will be html5 (a lot are now). Adobe has a really crappy way of maintaining software from what im told, they just code quick fixes, and thats why their software is so buggy and has so many security holes.

A few years ago, running flash on linux (especially in firefox) was hell.

What else do you need? We know photoshop is never coming. PDF reader? I really dont think Adobe's reader is very good, Okular serves my purposes better

---

### Post by TenPlus1 on 2012-09-25
I managed to download the latest google-chrome-dev .deb package and extract the libpepflashplayer.so and place it inside my chromium directory and edit a few lines to let chromium know it's there...  So now I am running Adobe's Flash Player 11.4 with no problems at all...

---

### Post by eival on 2012-09-27
> **TenPlus1 said:**
> I managed to download the latest google-chrome-dev .deb package and extract the libpepflashplayer.so and place it inside my chromium directory and edit a few lines to let chromium know it's there...  So now I am running Adobe's Flash Player 11.4 with no problems at all...


thanks for telling us how to do it, helped alot.

---

### Post by linuxvstheworld on 2012-09-27
> **WinterMadness said:**
> Adobe is becoming irrelevant anyway. HTML5 > Flash. Soon every video on youtube will be html5 (a lot are now). Adobe has a really crappy way of maintaining software from what im told, they just code quick fixes, and thats why their software is so buggy and has so many security holes.

A few years ago, running flash on linux (especially in firefox) was hell.

What else do you need? We know photoshop is never coming. PDF reader? I really dont think Adobe's reader is very good, Okular serves my purposes better
+1 to you sir, take this with honor....

---

