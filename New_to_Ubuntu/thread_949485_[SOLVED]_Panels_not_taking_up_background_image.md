---
title: "[SOLVED] Panels not taking up background image"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by float379 on 2008-10-16
Hey!! I have a problem with my panels in ubuntu. Every time i try to change the panel background to some solid color or a image or if i try to adjust the transparency, the changes are reflected in only part of the panel(notably the icon free area). Areas with icons like the main menu bar, notification area and some launchers, retain the theme in use.
  I am relatively new to ubuntu, and am using 8.04 hardy heron. Also, i recently followed a tutorial dress up ubuntu as an os x. Would that have affected my panel behaviour?

---

### Post by damis648 on 2008-10-16
That is just the way it works, unfortunately. If you are using compiz, though, you can go to ccsm and go to General and Change the transparency of
```
name=gnome-panel
```, but the whole bar will change transparency, including the icons.

---

### Post by Het Irv on 2008-10-16
It may have something to do with your menus, you can try deleting the bar and adding a new one. If you do that probably the best way to do that would be to create the new one first, and then delete the old one.

---

### Post by Therion on 2008-10-16
This is often a theme issue as well.  Sometimes when I have that issue with the panels not being properly transparent, changing to a different theme will resolve the issue.  

And yes, sometimes that IS a bit of a Catch-22 situation...

---

### Post by jerome1232 on 2008-10-16
I second therion's suggestion it I've only had this problem with certain theme's.

Sometimes you can get a similar result to the old theme by selecting another theme then heavily customizing it to use most of the old theme's features.

---

### Post by sayems on 2008-10-16
How to restore Gnome default value

As a new Ubuntu (Linux) user (like I am), there are times where you would want to mess with your Gnome, playing around with it and start adding/removing stuffs here and there.

If you have, somewhat, intentionally broken your Gnome settings (for instance, missing window buttons, disappearing application menu, or even worse, crashing gnome-panel), there is still a solution.

All you need to do now is to restore the Ubuntu/Gnome default settings.

To give you an idea, all Gnome settings are stored in folders, and they are user specific. That said, by simply removing these customization folders, you will be able to get back the fresh settings!

Type the following into your command : Alt+F2

rm -rf .gnome .gnome2 .gconf .gconfd .metacity

Eventually, do a restart and you should get back the default Ubuntu/Gnome settings!

And it's time to start playing with the Gnome customizations again ;)

---

### Post by float379 on 2008-10-16
Thanks for all the advice guys, but unfortunately i've tried most of it out. Changing my theme to an older one doesn't help, and adding a new panel is only good as long as no menus/applications are added to it :-(.I haven't tried the rm or rf commands 'coz there has been a fair proportion of people who have warned me against using it, if i dont't understand it completely.My problem is not so much transparency as it is the panel not behaving as an homogeneous object.

---

### Post by float379 on 2008-10-16
Correction: I did cycle through a few themes, and yeah, it does work for a few of the older themes. Thanks for the help!!! One more thing, how do i mark this as solved?

---

### Post by jerome1232 on 2008-10-16
edit: You got it, congrats, to mark as solved use thread tools in the top right.

There's nothing dangerous in removing the directoires he gave you, it'll clear out all gnome and gnome app preferences though.

I'm using clearlooks theme at the moment and I have zero problems with the panel, using Ubuntu Studio theme I had the problems your talking about (any theme that puts a nice gradient type of thing on the panel seems to cause it)

sorry that didn't help.

---

