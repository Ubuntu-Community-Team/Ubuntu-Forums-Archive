---
title: "Right-Click Image in Nautilus to Make Wallpaper"
date: 2012-06-04
forum: New to Ubuntu
---

### Post by RichieB07 on 2012-06-04
Is there a way to right click on an image in Nautilus and set it as the desktop background without opening it in EOG or going through the "Appearance" menu?  I know Windows and OS X have this, so why doesn't Ubuntu?
I'm on 12.04, have been using Ubuntu since 10.04, and have found this to be incredibly frustrating as I change my wallpaper often.

---

### Post by shafi.dude99 on 2012-06-04
> **RichieB07 said:**
> Is there a way to right click on an image in Nautilus and set it as the desktop background without opening it in EOG or going through the "Appearance" menu?  I know Windows and OS X have this, so why doesn't Ubuntu?
I'm on 12.04, have been using Ubuntu since 10.04, and have found this to be incredibly frustrating as I change my wallpaper often.

you need to add plug-in to do that .... plugin name is nautilus-wallpaper

open synaptic manager and search for nautilus-wallpaper and install it...

---

### Post by RichieB07 on 2012-06-04
> **shafi.dude99 said:**
> you need to add plug-in to do that .... plugin name is nautilus-wallpaper

open synaptic manager and search for nautilus-wallpaper and install it...

I installed that and it didn't show up in the context menu still.  I even restarted, ran sudo apt-get autoclean, autoremove, update, and upgrade.  Still not in the menu.

---

### Post by mcduck on 2012-06-04
The "nautilus-wallpaper" extension does exactly that, but I'm not sure if it's available for Nautilus 3.x yet. You could check if it's available in Ubuntu's repositories and try if it works...

---

### Post by traditionalist on 2012-06-04
> **RichieB07 said:**
> I installed that and it didn't show up in the context menu still.  I even restarted, ran sudo apt-get autoclean, autoremove, update, and upgrade.  Still not in the menu.

Get "nautilus-actions" it does that and a lot of other stuff. You can also set up your own extensions;

[https://launchpad.net/~nae-team/+archive/ppa/+packages]("https://launchpad.net/%7Enae-team/+archive/ppa/+packages")

[[IMG]http://img214.imageshack.us/img214/9608/workspace1001o.th.png[/IMG]]("http://img214.imageshack.us/i/workspace1001o.png/")

get it here;

[http://www.webupd8.org/2011/12/nautilus-actions-extra-pack-of-useful.html](http://www.webupd8.org/2011/12/nautilus-actions-extra-pack-of-useful.html)

---

### Post by traditionalist on 2012-06-04
This is the configuration package in action;

[[IMG]http://img812.imageshack.us/img812/953/selection001ct.th.png[/IMG]](http://img812.imageshack.us/i/selection001ct.png/)

I have set up several things in the context menu using it;

[[IMG]http://img442.imageshack.us/img442/3289/workspace1001p.th.png[/IMG]](http://img442.imageshack.us/i/workspace1001p.png/)

very useful indeed.

---

### Post by RichieB07 on 2012-06-04
> **traditionalist said:**
> Get "nautilus-actions" it does that and a lot of other stuff. You can also set up your own extensions;

[https://launchpad.net/~nae-team/+archive/ppa/+packages]("https://launchpad.net/%7Enae-team/+archive/ppa/+packages")

[[IMG]http://img214.imageshack.us/img214/9608/workspace1001o.th.png[/IMG]]("http://img214.imageshack.us/i/workspace1001o.png/")

get it here;

[http://www.webupd8.org/2011/12/nautilus-actions-extra-pack-of-useful.html](http://www.webupd8.org/2011/12/nautilus-actions-extra-pack-of-useful.html)

Thanks, that did it.  The "nautlius-wallpaper" and even a "Nautilus Actions Configuration Tool" in the SC don't work with 12.04, but that PPA does.  Thanks!

---

### Post by traditionalist on 2012-06-04
> **RichieB07 said:**
> Thanks, that did it.  The "nautlius-wallpaper" and even a "Nautilus Actions Configuration Tool" in the SC don't work with 12.04, but that PPA does.  Thanks!

What's an SC? Oh..I get it  Software Centre? Indeed, some of the stuff there doesn't work very well or not at all on 12.04

Anyway I think this stuff is marvelous.  Am also working on a colour coding setup for nautilus;

for info see here;

[http://my.opera.com/area42/blog/2011/05/06/using-nautilus-emblems-like-color-labels-on-mac-os-x](http://my.opera.com/area42/blog/2011/05/06/using-nautilus-emblems-like-color-labels-on-mac-os-x)

---

### Post by Ravi5kumar on 2012-07-31
@[traditionalist]("http://ubuntuforums.org/member.php?u=1616174"): What version of ubuntu are you using? Mine is 12.04 and this nautilus config tool doesn't work! Holy ****!!

---

