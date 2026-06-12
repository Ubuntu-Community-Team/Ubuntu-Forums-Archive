---
title: "HOWTO: Change Menu Icon"
date: 2008-04-22
forum: Outdated Tutorials &amp; Tips
---

### Post by xfroggy on 2008-04-22
Well, after googling countless useless results with mixed solutions, I decided to write this small tutorial that might help others who are interested in changing their Ubuntu icon on main menu. As I'm writing this I'm using Ubuntu 7.10 (Gutsy) & Gnome 2.20.1.

Before I start, I would like to point out that there are 2 main menu's. One is called 'Main Menu' which is just a small icon with all the content showing on click and the other one is 'Menu Bar' which comes with Applications, Places, & System menus right beside it.

*_MAIN MENU_
Alright, lets get moving. I'm going to start with an easy solution first. If you are using 'MAIN MENU', all you have to do is:

1. Open gconf-editor (alt+f2 and type **gconf-editor**)
2. Go to apps/panel/objects
3. Look though the 'object_x' settings, looking for "tooltip Main Menu" and also "object_type menu-object" which going to show in the right side window.. 
4. When you find it, edit the value of 'custom_icon' to the full path of your custom icon's location and check the box 'use_custom_icon'.
5. Press ALT+F2 and type ```
killall gnome-panel
```

You should (hopefully) have your new custom icon showing.

*_MENU BAR_
Now for the hard part if you are using MENU BAR.
I'm going to show you how to do it on the default icon theme, since if your new icon theme doesn't come with replacement, it will fall back to the default Gnome's icon theme. I also want to point out that Menu Bar seems to be using only 22x22 icon, but you can actually fit it any size you want. I tried 32x32 icon, which just re-sized my panel and looked a bit ugly.
1. First of all lets make a backup!
```
$ cd /usr/share/icons/gnome/22x22/places
```
```
$ sudo cp -v start-here.png{,.bak}
```
2. Now it's time to replace the icon. Copy over 'start-here.png' image with your own icon. Don't forget to sudo!

**Optional**
2a. If you don't have anything on hand, here's a cool monkey icon just to give it a test. As long as you are still in the same directory, (which is /usr/share/icons/gnome/22x22/places), type the following:
```
$ sudo cp -v ../emotes/face-monkey.png start-here.png
```
3. Now, we need to update our icon cache.
```
$ cd ../..
```
Which should bring you back to /usr/share/icons/gnome & type the following:
```
$ sudo gtk-update-icon-cache -f ./
```
4. You almost done! Press ALT+F2 and type ```
killall gnome-panel
```

This also worked with a custom icon theme and scalable folder instead of 22x22, but the icon theme had only scalable directory. Also just a heads up, all you need to replace is start-here.png or start-here.vga in scalable directory for ubuntu logo, since the rest are just symlinks.

TIP: Don't go crazy on killing gnome-panel, for some reason it brakes my system after 2-3 times where I end up with nothing reloading anymore and having to restart the system.

Comments/suggestions welcome!
(I seen other tutorials on here, but they were half complete and didn't worked for the Menu Bar).
P.S. This is my first tutorial and I'm half asleep when I wrote it, so please go easy on me! :twisted:

---

