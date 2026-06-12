---
title: "Least pain Gutsy to Hardy upgrade"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by movrshakr on 2008-05-01
OK, here is the question/problem.  I want to upgrade my Gutsy to the LTS release, Hardy.  My concern  is this.  When I installed Gutsy last year, I spent MANY hours getting it to work and to perform like I wanted...

-Getting the display "right"
-Getting cups and my Samsung SCX-4725FN network printer to print
-Getting a samba share onto the network that network Windows machines could use as a network file server--with no one logged in (a MAJOR effort).
-Getting ntp and ntpdate and eth0 to come up in the right order, and to actually work (a MAJOR effort). See here:
[http://ubuntuforums.org/showthread.php?t=647559&highlight=movrshakr](http://ubuntuforums.org/showthread.php?t=647559&highlight=movrshakr)
(six pages)
-Getting about 25 aliases defined (minor issue here)
-Getting the screen to show the boot process (minor issue here)
-Getting an ssh login ability from Windows network machines

Foolishly, I did not document how all of this was done.  The question is, is there a way to move into Hardy that will not "erase" all those things I did--making me have to repeat it all?

---

### Post by brownknight on 2008-05-01
> **movrshakr said:**
> OK, here is the question/problem.  I want to upgrade my Gutsy to the LTS release, Hardy.  My concern  is this.  When I installed Gutsy last year, I spent MANY hours getting it to work and to perform like I wanted...

-Getting the display "right"
-Getting cups and my Samsung SCX-4725FN network printer to print
-Getting a samba share onto the network that network Windows machines could use as a network file server--with no one logged in (a MAJOR effort).
-Getting ntp and ntpdate and eth0 to come up in the right order, and to actually work (a MAJOR effort). See here:
[http://ubuntuforums.org/showthread.php?t=647559&highlight=movrshakr](http://ubuntuforums.org/showthread.php?t=647559&highlight=movrshakr)
(six pages)
-Getting about 25 aliases defined (minor issue here)
-Getting the screen to show the boot process (minor issue here)
-Getting an ssh login ability from Windows network machines

Foolishly, I did not document how all of this was done.  The question is, is there a way to move into Hardy that will not "erase" all those things I did--making me have to repeat it all?

Just do a dist-upgrade (not fresh install). That will certainly keep your configurations. That always work for me.

On another note, what I did on another laptop was to make a separate partition for root (/) and home (/home). This way, when I do a fresh install, all my configurations and files are untouched.

One last thing, I did a fresh install of Hardy Heron and this is the first time that I didnt have to mess around with display. It just configured it correctly to 1280X800 widescreen. Great!

---

### Post by Myglaren on 2008-05-01
[img]http://forums.mystery-axiom.com/images/smilies/whs0be.gif[/img]

---

### Post by nowshining on 2008-05-01
I suggest keeping Gutsy for now if you got everything set-up the way u want it. I'm going to do the same @ least for now.

or

Backup first incase everything goes wrong, backup your /etc/Xll/xorg.conf file, custom configs, etc.. and try to rem. whre they were, or take a note in a text editor of the paths you last had them, once done with all that, fresh install for the best and return all configs, etc.. or try to to the way you had them or try the upgrade.

Always backup when doing a dist-upgrade unless you plan on taking the risk and have a recovery plan ahead of time incase something does goes wrong.

---

### Post by phoenix_abhi on 2008-05-01
> **movrshakr said:**
> OK, here is the question/problem.  I want to upgrade my Gutsy to the LTS release, Hardy.  My concern  is this.  When I installed Gutsy last year, I spent MANY hours getting it to work and to perform like I wanted...

-Getting the display "right"
-Getting cups and my Samsung SCX-4725FN network printer to print
-Getting a samba share onto the network that network Windows machines could use as a network file server--with no one logged in (a MAJOR effort).
-Getting ntp and ntpdate and eth0 to come up in the right order, and to actually work (a MAJOR effort). See here:
[http://ubuntuforums.org/showthread.php?t=647559&highlight=movrshakr](http://ubuntuforums.org/showthread.php?t=647559&highlight=movrshakr)
(six pages)
-Getting about 25 aliases defined (minor issue here)
-Getting the screen to show the boot process (minor issue here)
-Getting an ssh login ability from Windows network machines

Foolishly, I did not document how all of this was done.  The question is, is there a way to move into Hardy that will not "erase" all those things I did--making me have to repeat it all?

In my experience, you do not have to worry about any drivers previously installed. Hardy have not made any change in my hardware configurations,when I upgraded from Gutsy, further the sound and display are awesome.

---

