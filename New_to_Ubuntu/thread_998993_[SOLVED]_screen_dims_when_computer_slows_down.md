---
title: "[SOLVED] screen dims when computer slows down"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by sa-mejia on 2008-12-01
Whenever my computer (a thinkpad R61i) slows down or temporarily freezes (presumably because I am demanding too much RAM from it) the screen dims. 

I think that this is not a bug, but some sort of feature of Ubuntu 8.04.  

I am wondering how can I turn this feature off (I could not find any post where this was discussed).

Thanks in advance.

Santiago

---

### Post by RookieUbuntuUser58 on 2008-12-01
Yeah I have this problem too. The screen starts going grey and you can't do anything. Im running Ubuntu 8.10 btw. So yeah if anyone has a solution to this problem post up.

---

### Post by jenkinbr on 2008-12-01
Are either of you running compiz?  If so, it is a setting in compizconfig settings manager that automatically dims the window when it stops resonding to window-manager activities. I don't remember for sure the path to the setting, but search for 'window dim' and it should be in the results.

---

### Post by metallicamike on 2008-12-01
its just something ubuntu does to let you know that it is vigorously loading and will either finish eventually or has crashed, and as far as i know, you can't turn it off, but i would imagine that you can somewhere in configuration editor. Hope that helps.

---

### Post by Unixilandia0110 on 2008-12-01
Hi Santiago. I too have this problem and I find it extremely annoying. It makes me want to go back to Ubuntu V.8.04. I LOVE Linux Ubuntu and have used V.7.10, V.8.4, and now V.8.10, but am not crazy about this new distro. I also don't like the way the screen can easily be "accidently" switched to a different screen. it's most annoying. I hope it's possible to shut off that "dimming" feature, and also the desktop window shifts. Thanking in advance anyone who can assist us.

---

### Post by RookieUbuntuUser58 on 2008-12-01
> **jenkinbr said:**
> Are either of you running compiz?  If so, it is a setting in compizconfig settings manager that automatically dims the window when it stops resonding to window-manager activities. I don't remember for sure the path to the setting, but search for 'window dim' and it should be in the results.


Yeah I'm running compiz and that option was checked. Just unchecked it. Thanks, that feature was getting annoying. Makes you think your computer is gonna crash.

---

### Post by sa-mejia on 2008-12-01
> **jenkinbr said:**
> Are either of you running compiz?  If so, it is a setting in compizconfig settings manager that automatically dims the window when it stops resonding to window-manager activities. I don't remember for sure the path to the setting, but search for 'window dim' and it should be in the results.

Jenkinbr... could you be a little bit more specific about how could I go around searching for this feature?  I mean, I am quite of a novice, and although willing to explore Ubuntu, need some help to get off the ground.

Santiago.

---

### Post by sa-mejia on 2008-12-01
> **boost3d23 said:**
> Yeah I'm running compiz and that option was checked. Just unchecked it. Thanks, that feature was getting annoying. Makes you think your computer is gonna crash.

Boost... could you please tell all of us novices, how did you find it and turned it off?

S.

---

### Post by RookieUbuntuUser58 on 2008-12-01
> **sa-mejia said:**
> Jenkinbr... could you be a little bit more specific about how could I go around searching for this feature?  I mean, I am quite of a novice, and although willing to explore Ubuntu, need some help to get off the ground.

Santiago.

Go to system>preferences>CompizConfig Settings Manager. Click on Effects and it should have a Fading Windows option uncheck it.

---

### Post by jenkinbr on 2008-12-01
> **sa-mejia said:**
> Jenkinbr... could you be a little bit more specific about how could I go around searching for this feature?  I mean, I am quite of a novice, and although willing to explore Ubuntu, need some help to get off the ground.

Santiago.

First, make sure you have compizconfig-settings-manager installed:
```

sudo apt-get install compizconfig-settings-manager

```
Once this is installed, press alt+f2 and type 'ccsm' into the box that appears.  This will start the settings manager.

> **boost3d23 said:**
> Yeah I'm running compiz and that option was checked. Just unchecked it. Thanks, that feature was getting annoying. Makes you think your computer is gonna crash.

boost3d23: would you mind posting where that setting was located?  I'm not on my ubuntu box, and don't know for sure where the setting is located.  A quick borwse of compiz-fusion.org didn't help me either. 

Edit: nevermind, you already did. :)

---

### Post by sa-mejia on 2008-12-01
> **boost3d23 said:**
> Go to system>preferences>CompizConfig Settings Manager. Click on Effects and it should have a Fading Windows option uncheck it.

Boost,

There is no such thing as a CompizConfig Setting Manager under system>preferences.  Does that mean that I am not using Compiz?  (I have a fresh install of Hardy if that makes the question more intelligible)

Santiago.

---

### Post by jenkinbr on 2008-12-01
> **sa-mejia said:**
> Boost,

There is no such thing as a CompizConfig Setting Manager under system>preferences.  Does that mean that I am not using Compiz?  (I have a fresh install of Hardy if that makes the question more intelligible)

Santiago.
Try following my instructions I posted on the previous page to install compizconfig settings manager.  Then boost3d's instructions should work for you.

---

### Post by RookieUbuntuUser58 on 2008-12-01
> **sa-mejia said:**
> Boost,

There is no such thing as a CompizConfig Setting Manager under system>preferences.  Does that mean that I am not using Compiz?  (I have a fresh install of Hardy if that makes the question more intelligible)

Santiago.



Hmm check add/remove and search for Compiz and see if advanced desktop effects setting is checked. If it is you have it. Or let me know what is checked when you search for it. I have a different version 8.10 but it should be the same, I would think.

---

### Post by sa-mejia on 2008-12-01
> **jenkinbr said:**
> Try following my instructions I posted on the previous page to install compizconfig settings manager.  Then boost3d's instructions should work for you.

Jenkinbr,

I followed the combination of your instructions and those of boost3d (thanks to both by the way).  Nevertheless... the screen is still fading out when the computer's demands are high.  

Any other suggestion?  Did anyone else had any luck by following the procedure thta Jenkinbr and boost3d outlined?

S.

---

### Post by Kellemora on 2008-12-01
Hi SM

We do some pretty heavy graphics work here on Ubuntu machines, both with and without Compiz and have the same issues, so I don't think Compiz by itself is the fault here.

Basically, a dimmed out screen simply means I'm too busy right now to handle anything else, hold on a minute or two or three, hi hi........

I also don't think it has to do with the amount of RAM you have either, within reason of course.

Doing the exact same tasks on two different computers, one with 512megs of RAM and the other with 1024 megs of RAM, both showing 100% CPU usage while the program is running and doing it's thing.  The computer with 512megs consistently finishes the task and the screen brightens back up long before the machine with the 1024megs of RAM.
The machine finishing first with only 512meg of RAM does not have Compiz on it, the one with 1024megs does.  So Compiz could be slowing down that machine a little more.  But in both cases, the CPU usage is 100% and the smaller machine does some file swapping the larger machine don't.

The fade control in Compiz is for HOW it changes screens, has nothing to do with what is ON the screen.  If you play with the controls for Effects and then change back and forth from one window to another you'll see what I mean.  I have mine just set to roll like the cube turning.  If I set it to FADE I no longer see the roll, one screen fades out as the other takes it's place.

TTUL
Gary

---

### Post by Unixilandia0110 on 2008-12-01
I'd like to thank Boost3d23, and Jenkinbr for their kind and good assistance here. This forum rulz! :)

---

### Post by jenkinbr on 2008-12-02
You're very welcome.

@sa-mejia: 
Be sure to mark this thread as solved.  (at the top of the page, click 'thread tools' and then 'mark thread as solved'.)  This will help others know your problem has a solution (at least for a few), should they find it through a search.

---

### Post by sa-mejia on 2008-12-02
Thanks a lot to everybody.

I had no idea that you could set a thread as solved, so I must again thank  jenkinbr for teaching me this new thing.  And I should also thank Kellemora for his extensive explanation that, unfortunately, seems to suggest that there is not too much that can be done to avoid having the screen dimed.

The whole reason why I wanted this feature to be turned off was that I was trying to use PDFedit to read and underline articles.  The program slows a lot the machine, and while the machine thinks, I wanted to be able to keep on reading and not to have the system preclude me from doing it by dimming the screen.

Anyhow thanks a lot again.

S.

---

### Post by Otto-C on 2008-12-13
I do not feel comfortable with marking this thread as solved.

I too have the dim/fade problem. I also use Compiz and have
disabled both 'Fade To Desktop' and 'Fading Windows'.

This is a single user machine and the dim/fade occurs when
first booted and a terminal is opened and the cursor leaves
that work space.

As I recall the problem appeared following one of the updates
about 4-5 weeks ago.

hth
otto-c

---

### Post by Otto-C on 2008-12-16
Last night I deleted (maybe foolishly) the icon on the top task bar.
I have an icon on the desktop. After opening a terminal I found that
the terminal stayed.

My question now is how to restore an icon to the task bar?

Found it Accessories>Applications>Terminal click add to panel.

After renewing the icon brought up a terminal and it did not 
dim as before. Other applications such as the update screen
still dim.
hth

tia
otto-c

---

