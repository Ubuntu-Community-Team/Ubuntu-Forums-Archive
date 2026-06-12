---
title: "ATI Catalyst Control Centre not working"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by PranaNZ on 2008-09-01
I have Catalyst 8.8 loaded on 8.04-64, just upgraded it from 8.7. The problem is I can not get the ATI  Control Centre to work again.  It was working OK under Catalyst 8.7.  I have unloaded it from the Add/Remove section in the Applications section, re installed it and rebooted.  The icon shows up ( in Other )but when I click on it nothing happens. I also tried running it from Run Application (Alt F2 ) with no luck.  Any ideas would be most welcome.

---

### Post by porchrat on 2008-09-02
Use this in terminal:

```
amdcccle
```

I had a similar problem once and I used that command to run it from terminal

may need "sudo" in front of it

---

### Post by PranaNZ on 2008-09-02
Thanks for that, unfortunately no luck.  This is what I got

chris@chris-desktop:~$ sudo amdcccle
[sudo] password for chris: 
amdcccle: ../../src/xcb_io.c:350: _XReply: Assertion `!dpy->xcb->reply_data' failed.
Aborted

Any one have any ideas?

---

### Post by chalewa on 2008-09-03
> **PranaNZ said:**
> Thanks for that, unfortunately no luck.  This is what I got

chris@chris-desktop:~$ sudo amdcccle
[sudo] password for chris: 
amdcccle: ../../src/xcb_io.c:350: _XReply: Assertion `!dpy->xcb->reply_data' failed.
Aborted

Any one have any ideas?

which set of instructions did you use to install?

---

### Post by porchrat on 2008-09-03
Found this thread...guy gets the same error as you, hopefully it will help.

[http://ubuntuforums.org/showthread.php?p=5406920]("http://ubuntuforums.org/showthread.php?p=5406920")

Seems as though there is a solution

---

### Post by PranaNZ on 2008-09-03
Thanks for the help guys, I used the method 2 from the wiki to install the drivers.  I'm not getting any error messages when I try running the Catalyst control, I just click on the icon ( or when running it from the terminal) and nothing happens.  The driver itself appears to be working fine with the graphics card HD4850, it's just the control centre interface not playing.  
I'll have a go at uninstalling and deleting all old files as suggested in that other post and let you know how I got on...

---

### Post by porchrat on 2008-09-03
awesome...good luck PranaNZ

---

### Post by PranaNZ on 2008-09-03
The joys of knowing enough to be dangerous!!  Managed to completely mess up the graphics.  Back to resolution that wouldn't allow me to click on the continue button on the Ati loading page.  Great thing about this forum is someone has usually had the same problems, so all back and running now BUT still no Catalyst control centre working.  Wondering if it has anything to do with 8.8, I was on 8.7 previously.  I also had problems with trying to load the Ubuntu Ati controller.  On the Ati install program it gives you the option to load a generic edition or a platform specific.  I tried both the Ubuntu/8.04 and Ubuntu/hardy versions without much luch.  Might give it another go later.  Thanks for all your help, the video is working again and I'll just have to do without the bells and whistles for a little longer.
Also going to contact Ati and see if they can move the continue buttons on their installer to the middle of the page (is empty anyway) noticed allot of threads on not being able to access the buttons due to messed up resolutions.

---

### Post by porchrat on 2008-09-04
I'm running 8.5 and it works like a charm...I did have problems launching control centre with GUI icon but the console command shown previously worked for me.

I then did a reinstall and everything was roses.  I hope you find an answer, I know how frustrating these things can be

---

