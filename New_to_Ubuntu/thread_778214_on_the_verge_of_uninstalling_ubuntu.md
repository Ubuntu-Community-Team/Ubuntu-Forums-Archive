---
title: "on the verge of uninstalling ubuntu"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by Rifts on 2008-05-01
alright I have a Geforce Go 7600 in my laptop. After I first installed Ubuntu 8.04 last week it was fine UNTILL I tried to turn my 3D effects on through system>pref>appearance>visual effects well after it told me to restart and I did it rebooted with "low graphics" and now the only resolution i can put it in is 800x600 i have read so many things and nothing will fix it. yes i have gone into hardware drivers and enabled and disabled the driver there 50 times.

---

### Post by SunnyRabbiera on 2008-05-01
well there are some cards that just wont co operate with us, and that might be one of them.
but have you tried the screens and graphics app?
its hidden for some odd bizarre reason but you can unhide it by right clicking your menu, then selecting "edit menu's"
then go to the "other" category and click on the box next to "screens and graphics"
this may help you out on your card, I am unsure as I dont have that card...
but keep experimenting and if needed you can install envy that sometimes does proprietary drivers better then the default restricted drivers app.

---

### Post by axor1337 on 2008-05-01
have you tried envy ?

---

### Post by vexorian on 2008-05-01
Hi.

Ubuntu hardy currently has some serious issues with nvidia compatibility I got to say. So, you should probably wait for an update to this issue in the repos and then install from scratch again.

Alternatively, you should try getting the graphics driver from nvidia's site, be warned that it is difficult to install it and it adds complications to later kernel upgrades.

I have not tried envy but it is supposedly a way to install that driver easily.

BTW: This thread works : [http://ubuntuforums.org/showthread.php?t=763236](http://ubuntuforums.org/showthread.php?t=763236) If you follow it with care you should get everything fixed.

---

### Post by Rifts on 2008-05-02
yah ive tried evny three times no good =[ill check that link out now thanks

---

### Post by amirman on 2008-05-02
hey i had a similar problem where all my 3D and everything worked great until it just randomly reset and my wobbly windows were working but not the desktop cube and my resolution was 640x480.

some guy in #compiz helped me out a lot, he wrote a custom xorg.conf file for me.

the solution was to basically put all the relevant info in my xorg.conf file

i'm a noob so i couldn't help much on the details but maybe this will steer you in the right direction.

also as a linux and more specifically ubuntu noob i can tell you one thing i've learned. if you expect everything to always work perfectly without any work linux is not for you  I run into problems now and then and since i love this OS so much already i've decided that if anything messes up i will try not to get frustrated too much and i'll never give up.  these experiences can be used as learning experiences, linux is fun to learn. the more stuff that messes up, the more you learn about why it messed up , the more you learn to fix things, the more you can help others, and the better the whole project gets overall. also don't give up, if you ever use IRC #compiz on irc.ubuntu.com is a good place to find people who are very knowledgeable with graphics issues.

---

