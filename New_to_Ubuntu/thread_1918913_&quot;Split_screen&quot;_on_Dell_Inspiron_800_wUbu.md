---
title: "&quot;Split screen&quot; on Dell Inspiron 800 w/Ubuntu11.10"
date: 2012-02-01
forum: New to Ubuntu
---

### Post by pjmahar on 2012-02-01
I am a complete newbie so bear w/me.
I put this on Launchpad but have not resolved the problem.
 
I installed 11.10 (alternate iso) on a dell inspiron 8000 w/the ATI graphics card.
The install went fine except that the screen is "split" - like two tiles overlapping one another. 
I can see that the open source ATI/radeon driver is installed and it recognizes the video card. 
On the lauchpad they suggested updating the Bios - done, but no change.
I have a screen shot of the display but I am not sure how to put it up.
 
I have googled this problem and checked on these forums. Seems I am not the only one with this problem, but most of the posts are old and refer to older versions of ubuntu. They also refer to changing Xorg. config but I don't see that i have that file.
 
Unfortunately I blew away windows when I installed Ubuntu, because of the garbled display. 
 
I have tried the live CD and got the same display problem. I tried 10.04 LTS and that was garbled too.
 
I think I need to change the settings for the graphics card.... just not sure how!

---

### Post by pjmahar on 2012-02-02
I figured it out. 
How to I list this as solved?

---

### Post by audiomick on 2012-02-02
> **pjmahar said:**
> 
How to I list this as solved?
-at the top of the thread there is a drop down list of options called "thread tools". One of the options is "mark as solved".

---

### Post by notiones on 2012-03-22
> **pjmahar said:**
> I figured it out. 
How to I list this as solved?

It would have been nice if you had linked to the solution or provided some idea of what you did to fix it.

---

### Post by tarocc on 2013-01-27
Hello,

I recently had some fun with a Dell Inspiron 8000 and I found out that on some distros that don't use xvesa when X starts the screen gets garbled / splitted / teared / fuzzy or just plain black,
I solved this problem just by pressing FN+F7 (in my keyboard there's a little text "Font" just after the F7 text)
it makes the screen zoom in and out if you press multiple times,
by doing this usually the screen fixes itself.
can't really say what this FN+F7 was meant for as I didn't run any windows version on this laptop ;)
Hope this helps all Inspiron 8000 owners!

---

### Post by tgalati4 on 2013-01-27
Some of these older machines use "shared" video RAM.  You can change the value in BIOS.  If video RAM is too low, the screen will get repainted and sometimes become garbled.  Check the BIOS for a video RAM setting.

---

