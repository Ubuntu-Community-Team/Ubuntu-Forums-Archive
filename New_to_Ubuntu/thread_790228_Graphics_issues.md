---
title: "Graphics issues"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by Itai number 1 on 2008-05-11
Hi

I don't know if this is the right place to ask this question but here goes.

I have installed ubuntu 8.04 (i am a classic newbie). i have been setting up ubuntu for the last few days and cant seem to get my graphics card to work, i.e my screen wants 1920X1200 and my software(ubuntu and ati catalyst) says 1600x1200. Don't know whether i have messed my Xorg.conf file or it is something else. I am currently using the fglrx driver.

I have also been trying to find an answer on how fix the pixelated screen when going to full screen during a movie.

I have a ati radeon x1600 graphics card and a acer x243w (24" wide screen) if that is any help.

thanks in advance

---

### Post by diablo75 on 2008-05-11
Type this into a terminal window:

```
sudo gedit /etc/X11/xorg.conf
```
And then paste the contents of that file in a reply post here.  By the way, welcome to the club!

---

### Post by SunnyRabbiera on 2008-05-11
Your ATI is probably th cause of your bad screen issues, try turning desktop effects off.
ATI support for linux is pretty crappy, its not our fault that they wont co operate with us to make better drivers.

---

### Post by diablo75 on 2008-05-11
> **SunnyRabbiera said:**
> Your ATI is probably th cause of your bad screen issues, try turning desktop effects off.
ATI support for linux is pretty crappy, its not our fault that they wont co operate with us to make better drivers.

I'm betting the resolutions he has stated in his xorg.conf don't go as high as the native resolution his monitor is capable of.  5 bucks.

Then again, there might be a limitation being put upon the video card by the above mentioned crappy drivers...

---

