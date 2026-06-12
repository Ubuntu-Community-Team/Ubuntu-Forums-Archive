---
title: "A new way for F Spot to crash in Hardy"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by Big Foot on 2008-05-04
I did the overnight upgrade from 7,10 to 8.04.

In general things are working except F-spot causes a crash the second time I try to run the slide show or when I exit F-spot.  The crash mode is a return to the sign-on screen (asking for user name), so there is no record of how the crash occurred.

Other graphics apps work OK such as DVD player full screen, Sky rocket screen saver, animations in Fire Fox.  I have a Radeon 9600.  I am not currently using the ATI proprietary driver.

If anyone has any ideas on how to fix this problem, please let me know.

By the way, I have around 3000 photos with tags in F-spot, so I hope if a re-install is indicated, there is a way to preserve the tags.

Thanks for any help.

Big Foot

---

### Post by Big Foot on 2008-05-04
An interesting update.

I tried the proprietary ATI driver.  That fixed the F-Spot crash problem, but now screen updates are running about 1-2 per second.  Screen savers that were smooth motion are now very jerky.

Anyone know how I can recover the speed and still have F-spot not crash?
In 7.10 the ATI driver was faster than the built-in one, now it seems to run at 1/10 or worse.

---

### Post by Big Foot on 2008-05-04
Update #2

All is now right with the world.  F Spot doesn't cause crashes, Google Earth is about 10 times faster (a little slow compared to the windows version, but acceptable) and the screen savers show continuous motion.

What did I do you may ask?  Damn if I know!

Near as I can tell, I am using the proprietary ATI driver.  I ran

dpkg -reconfigure xserver.org

and checked the option to use the frame buffer.

After a re-start, everything seems to work.:confused:

---

