---
title: "Installation process leaves me a black screen and the cursor blinking in the corner"
date: 2012-11-09
forum: New to Ubuntu
---

### Post by leonarwood on 2012-11-09
Hi, everyone.
Recently, I want to have a try the newest Ubuntu 12.10. So I downloaded the 64bit version of it. I burnt it on a CD after checksum the iso. But after I chose the option 
"Install Ubuntu", then the screen goes black for unknown reasons. Until I pressed down the power button, the screen turned back and said it was shutting down.
And I tried the option "LIVE CD", the same thing happened. 
And I tried to set nomodeset on according to the articles online, but my laptop still refused to work normally.
My computer is a laptop, with an integrated card Intel 3000, and a discrete one, GF 610m.
 
I need help from anyone possible. Thanks very much in advance.
Or could anyone tell me how to install in text mode? 
Or I would like to give up the Graphic mode totally. I just need to work in the text
mode, that'll be enough.
 
English is not my mother tongue, I'm not sure whether I have stated clearly 
about my problem that I am having. Hope so. Thanks again.:)

---

### Post by 2F4U on 2012-11-09
Since nomodeset didn't work for you, it may be time to dig deeper. This forum post offers many more suggestions:

[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by Mark Phelps on 2012-11-09
Had a similar situation.  Fixed with adding "rootdelay=90" to the kernel parms.  I started with 90, and was able to get it down to 45, and still boot OK.  Anything less than that, and I got the blinking cursor and black screen.

---

### Post by leonarwood on 2012-11-10
Thanks for replying so fast. I will check that out.

---

### Post by leonarwood on 2012-11-10
> **Mark Phelps said:**
> Had a similar situation. Fixed with adding "rootdelay=90" to the kernel parms. I started with 90, and was able to get it down to 45, and still boot OK. Anything less than that, and I got the blinking cursor and black screen.
 Hi, Mark. I am going to try this right now. Hope it could work. :)

---

### Post by Mr Fat Bat on 2013-01-15
Hey gang,

Any update on if the rootdelay worked?  I've got a similar issue.

cheers! MFB

---

