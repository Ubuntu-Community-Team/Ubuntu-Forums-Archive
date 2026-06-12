---
title: "Install - OK; Screen - no display"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by Brian001 on 2008-08-21
Hello,
I have installed Ubuntu on a Dell Inspiron 1100.  The install seemed to go good.  No errors.
Now when I boot up, I see the progress screen.  After that, I get a mouse for a few seconds.  Then blank.  Nothing.
Anyone have any ideas?

thanks

---

### Post by Brian001 on 2008-08-21
bump back up.
anyone have any ideas?
thanks

---

### Post by tuxulin on 2008-08-21
please can you do a restart boot 
then during the boot press ctrl + alt and f1
hopefully you should see some text scrolling upwards.

can you see any errors, if so then please state.

Tuxulin

---

### Post by pro003 on 2008-08-21
tell me which graphic card you have and I may help you...

---

### Post by Brian001 on 2008-08-21
that did seem to work

everything was ok.  except there was a red * next to on battery power.  

What does this do different?  Change something in the boot?
do you think I will need the ctrl+alt+f1 every boot?

thanks

---

### Post by tuxulin on 2008-08-21
brian001
i had a look around and it seems like that particular machine brand
has lots of logs reported against the graphic card and or chipset.

i have seen some partial solutions but none thats definitively on point so 
ill hunt around later to see if i can stumble on something. untill then
maybe some else might provide a solution.

Tuxulin

---

### Post by Brian001 on 2008-08-21
Thanks,
I can imagine that dells have problems.  Such weird drivers and such.

---

### Post by Kayma on 2008-08-28
I've installed Ubuntu on and off on my Inspiron 1100 for a few years now, and the xorg configuration is always a pain. While a vanilla 8.04 CD will install no problem, one apt-get upgrade will cause your next boot to blank screen. Lame.

Check out [this post]("http://ubuntuforums.org/showpost.php?p=5621787&postcount=12") to get you going. This tutorial suggests that you start with an earlier release of Ubuntu, but if you'd rather just fix your 8.04, you can either hook up to an external monitor (function key + f8, before ubuntu boots) or try that recovery mode + remove quiet splash thing.

8.04 CAN work on an Inspiron 1100, I can say that much; it just takes a bit of clawing and tooth gnashing.

---

### Post by Crafty Kisses on 2008-08-28
Try reconfiguring X.

If you can, post results of > glxinfo

---

