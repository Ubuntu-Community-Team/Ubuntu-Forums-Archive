---
title: "How can I undo system&gt;prefrences&gt;sessions?"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by Dan_472 on 2008-10-16
Hello

I used *system -> preferences -> sessions* to make it so that Firefox would load at startup (Ubuntu 8.04).  Unfortunately, now the desktop doesn't always work.  It will run very slowly, sometimes not respond to the keyboard, or not load the toolbar at the top.

Can I put it back the way it used to be by editing a file or something?  I have another working user on Ubuntu, as well as Puppy Linux on the same system.

Thank You

---

### Post by Keen101 on 2008-10-16
try recovery mode. Maybe you can get in long enough to remove it.

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

### Post by iponeverything on 2008-10-16
just get to a terminal with ctrl+alt+f2 and rename the firefox binary.

then it won't start -- you can get back into sessions and remove it.

then rename it back again..

---

