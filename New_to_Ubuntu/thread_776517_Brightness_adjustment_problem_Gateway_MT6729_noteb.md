---
title: "Brightness adjustment problem Gateway MT6729 notebook"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by Calindae on 2008-04-30
Just started with the Ubuntu 8.04 livecd and i'm trying to turn the brightness on my display down. It pops up with the little gauge telling me that it is all the way down, but the actual brightness never changes...

any thoughts?

---

### Post by Calindae on 2008-04-30
I've seen somewhat hostile replies on other threads when people ask for support on problems such as this. Is there somewhere else I should go to get help? I turn the brightness down (even function+down works) but it just shows it going down on the gauge but the actual brightness of my screen never changes.

---

### Post by Calindae on 2008-04-30
</invisibility>

Ahem...

I've found commands such as this:

# sudo echo "#" > /proc/acpi/sony/brightness_default

is there any way I can do this for a Gateway notebook?

---

### Post by Calindae on 2008-04-30
My graphics card is an Intel GMA X3100, if that helps.

---

### Post by Calindae on 2008-05-01
I would really like to install ubuntu to my hdd, but I can't handle the extreme brightness 24/7 (funny that I've seen so many people with the opposite problem). What do you guys suggest is the "second best" Linux distro after Ubuntu? Just case I can't fix this problem, which is looking quite hopeless...I wonder if the if it would play any nicer once fully installed?

---

### Post by Calindae on 2008-05-01
I've also started to look into kubuntu. Would this problem still exist with KDE?

---

### Post by mc4man on 2008-05-01
there may be an issue with your laptop and the function buttons, whether a real install fixes is hard to say. Possible solutions can be searched and tried. here's one [http://www.ubuntugeek.com/fix-your-laptops-brightness-function-keys-operating-properly-in-hardy.html](http://www.ubuntugeek.com/fix-your-laptops-brightness-function-keys-operating-properly-in-hardy.html)
what you could try is right click on an empty spot in top panel, choose add to panel and add the brightness applet, try it and see if it works

---

### Post by Calindae on 2008-05-01
> **Calindae said:**
> I turn the brightness down (even function+down works) but it just shows it going down on the gauge but the actual brightness of my screen never changes.

The function buttons work, it's just that the brightness won't go down even when the gauge is saying it is down. I even added it to the panel and did it like that (showed a percentage of brightness) and at 0% it was still at full brightness!!

---

### Post by MindFork on 2008-05-02
I have a similar problem, in that when I use the brightness adjuster on the side bar, NOTHING changes.  My function keys are also doing nothing.  Brightness is stuck at about 50% after "upgrading" to heron.  I should have left gutsy on there.  

The fix in the link above didn't work for me, either.  Total disaster of an upgrade, IMO.

---

### Post by mc4man on 2008-05-02
sometimes you got to keep searching and maybe you'll find a solution, maybe not. a temporary hack would be to adjust gamma, not ideal but maybe helpful
ck. here [http://ubuntuforums.org/showthread.php?p=4847939#post4847939](http://ubuntuforums.org/showthread.php?p=4847939#post4847939)

---

### Post by SunnyRabbiera on 2008-05-02
well you can try and install kgamma, kdebase-kio-plugins and kde-hal-device-manager.
I use that to adjust my monitor brightness.

---

### Post by kspncr on 2008-08-12
This may not help the OP but if I may, I'll direct your attention to this thread: [http://ubuntuforums.org/showthread.php?t=881241](http://ubuntuforums.org/showthread.php?t=881241) which helped me on my Compaq (I had the exact same problem as OP)

---

### Post by ss339 on 2008-09-09
THis will definately help if al else fails


[http://www.linuxscrew.com/2007/10/25/ajust-lcd-brightness-from-command-line-works-at-dell-1501/](http://www.linuxscrew.com/2007/10/25/ajust-lcd-brightness-from-command-line-works-at-dell-1501/)

works for me

---

