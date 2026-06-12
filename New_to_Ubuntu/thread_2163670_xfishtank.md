---
title: "xfishtank"
date: 2013-07-19
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2013-07-19
Hi Folks,

I've got 5 year old twins who are _*really*_ into fish.
I found xfishtank and have it working except for one flag I can't get to work.
The documentation says that the flag ```
-p <file>
```
should let you change the background of the fish tank.

I've tried:

```
xfishtank -root -p /home/grouchygaijin/Tanks/My_Tank.png
```

as well as several variation of the above and I still get the default background.

Has anyone else used xfishtank? If so, how do you change the background of the aquarium?

(My kids are bummed that they can't change the background and feed the fish like they can on my phone ;))

---

### Post by GrouchyGaijin on 2013-08-14
[COLOR=#ff0000][B]UPDATE:


[/B][/COLOR]The maintainer emailed me and said that in the version I had, the version in the Ubuntu repository, the -p flag didn't work.
Since then he has released a new version on [https://github.com/jim-rees/xfishtank](https://github.com/jim-rees/xfishtank) that has a patch which fixes the issue.

---

### Post by bluesimage on 2013-09-08
I'm on 12.04 LTS and the version of xfishtank does nothing when I execute it. What version of Ubuntu are you running and how are you invoking it?

---

### Post by GrouchyGaijin on 2013-09-09
I also have 12.04.  I needed to add xfishtank to the .xscreensaver file in my home.  Once I did that xfishtank was available as one of the choices in xscreensaver.  I added this to the file:
```
 any:                 xfishtank -root -p                  \
                  /home/john/Tanks/black-mesh.jpg        \n\


```

---

### Post by bluesimage on 2013-09-10
> **GrouchyGaijin said:**
> I also have 12.04.  I needed to add xfishtank to the .xscreensaver file in my home.  Once I did that xfishtank was available as one of the choices in xscreensaver.  I added this to the file:
```
 any:                 xfishtank -root -p                  \
                  /home/john/Tanks/black-mesh.jpg        \n\


```

Thanks for that. For some reason xfishtank just does nothing - not from command prompt and after updating xscreensaver. Probably something to do with video card (amd ATI radeon 6570) using the latest proprietary driver. xscreensaver does funky stuff as well - screen saver doesnt cover up the left hand dock and top control panel on each monitor - that and the login prompt for xscreensaver isn't visible (behind screensaver).

I think I've got a long journey ahead of me to figure this all out, likely will involve experimenting with multiple drivers/cards :)

---

### Post by GrouchyGaijin on 2013-09-10
Is xfishtank a choice in your xscreensaver list of available screensavers? Screenshot at [http://screencloud.net/v/a1PU](http://screencloud.net/v/a1PU)

---

### Post by bluesimage on 2013-09-10
I took another look and I added it incorrectly. It now works through xscreensaver. Now I need to figure out why the sidebar on the left and top don't get covered by the screensaver, but thats for another thread. Thanks!

---

