---
title: "Want a minimal login screen!"
date: 2014-05-26
forum: New to Ubuntu
---

### Post by merlin6 on 2014-05-26
Hey,

I'm pretty new to Linux and want to customise it as I've read it's very customisable!

i want the login screen to be blank with just a text field for the password in the center..

is this possible?

thanks

---

### Post by deadflowr on 2014-05-26
Try a different display manager.
What you want sounds like [slim]("https://wiki.archlinux.org/index.php/SLiM") would work best.
Simply run
```
sudo apt-get install slim
```
then when it is installed, run
```
sudo dpkg-reconfigure lightdm
```
in the dialog box that opens select the option for slim and tab to highlight OK.
then reboot for it to take affect.
If slim doesn't work for you, try gdm, perhaps(gnome display manager)
```
sudo apt-get install gdm
```
and run the reconfigure command again, selecting gdm.

I don't mind lightdm, so I really don't know what kind of problems, if any, will arise if you switch over to slim.
gdm works plenty fine, though.
IMHO

---

### Post by mastablasta on 2014-05-27
if you switch to slim be sure to configure it first and add the appropriate desktop name in it's config file. see their wiki for more detailed explanation. or Arch wiki also has good instructions.

i have not noticed any issues with Slim, however i think Chrunchbang switched away from it due to some issues. not sure which ones. lightdm is also light.

---

### Post by merlin6 on 2014-05-27
Thanks guys! I'll be sure to try it out :)

---

### Post by m_duck on 2014-05-27
Yep. Slim will do as you wish as it is very easy to theme (assuming there are no suitable themes already). Just have a look at one of the stock ones (/usr/share/slim/themes or thereabouts) for details. I've not done it for a while though, so sorry I can't be more specific.

---

