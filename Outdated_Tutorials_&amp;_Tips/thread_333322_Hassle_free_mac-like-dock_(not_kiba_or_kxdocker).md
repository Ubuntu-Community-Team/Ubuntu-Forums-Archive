---
title: "Hassle free mac-like-dock (not kiba or kxdocker)"
date: 2007-01-07
forum: Outdated Tutorials &amp; Tips
---

### Post by amoser on 2007-01-07
How to get an apple like dock with out hassle   
 

 This is starting with the default ubuntu desktop, but it can be done even if you have customized it.  This how to also does not require and extra programs to be installed, or any 3-d acceleration.
 

 [LIST=1]
[*]Delete the quit button in right 	hand side of the top panel, and delete the menu bar on the left hand 	side of the same bar.
[*]On the left hand side of the top 	bar, open the add to panel window; add the main menu and window 	list.  Lock both to panel.
[*]On far right hand of the top panel 	(where the quit button was) add the window selector, lock to panel
[*]Now for the bottom panel, delete 	everything except for the trash can.
[*]Add a separator to the left of the 	trash can, lock both the separator and trash can to the panel.
[*]Right click on the panel and go to 	properties.
[*]Change the size to 45-50 pixels 	(mine is at 48), uncheck the expand option, check the show hide 	buttons, and uncheck arrows on hide buttons
[*]Go to the background tab, select 	the solid color option, and change the color to white (#FFFFFF).
[*]Set the opacity to about 25%
[*]Drag your favorite applications 	from the main menu down to your new dock.
[/LIST] 

 There you go, an instant, stable, hassle free dock.  Sure it does not have all of the glitz as say kiba dock, or kxdocker; but it does have more functionality (such as you can drag a file to one of the programs in the dock, and the file will open in that application), and it is easier to add/remove programs to it.



~Alan

---

### Post by zephyrus54 on 2007-01-26
Another thing I found is that I need to make sure "keep aligned" is unchecked (right-click on your desktop to change this setting).  When it's checked and I reboot, the dock automatically starts up in the center of the screen (as opposed to the bottom, side, or wherever I originally placed it).  This is a slight annoyance, as I like my desktop items to be nicely aligned, but I guess I don't usually keep many files or icons on my desktop anyways.

I set my dock even smaller to 30 pixels, but of course everyone has their own preferences:D 

BTW, if anyone knows a fix for this bug let me know!

---

### Post by Ghil on 2007-01-26
you know, if you want to go that way, you can also just add a new panel, no need to change an already existing one.

---

### Post by Jolly Roger on 2007-01-26
This is a great way to get most of what a mac-dock offers without having to do much work. Like the OP said, there is a little bit of eye candy missing but it does look great. I've attached an image of how I have mine set up so people can see an example.

---

### Post by zephyrus54 on 2007-01-27
Here's another variation (As you can see I've got mine on the left and included the notification area, home folder, and trash bin in addition to launcher icons)

[IMG][[img]http://filelabs.net/fl1/files/screenshotCuQ8.png[/img]](http://filelabs.net)[/IMG]

---

### Post by pingvin on 2007-02-16
Having failed to run kxdocker in either Gnome or KDE (it would seem it now needs a composite window manager, which needs a good graphics card, which I don't have) I settled with an autohiding gnome-panel. You can change the timings in gconf-editor to allow instant unhiding and slower animations and slower autohiding, and change hidden size to 1 pixel. That way everything is drawn as normal, then it simply pops up on top of the windows.

Mike

---

### Post by Jussi01 on 2007-02-19
> **pingvin said:**
> Having failed to run kxdocker in either Gnome or KDE (it would seem it now needs a composite window manager, which needs a good graphics card, which I don't have) I settled with an autohiding gnome-panel. You can change the timings in gconf-editor to allow instant unhiding and slower animations and slower autohiding, and change hidden size to 1 pixel. That way everything is drawn as normal, then it simply pops up on top of the windows.

Mike

Hei, Thanks, But where in gconf-editor???

Cheers

Jussi

---

### Post by pingvin on 2007-02-20
Hi,
Go to:
gconf-editor -> apps -> panel -> toplevels -> <PANEL_NAME> (e.g. bottom panel). 
Click on this folder, there should appear several values in the opposite pane:
change the ones I mentioned by right-clicking, then "edit key" I think. Type in a new value, like "slow" for the variable animation speed.
Hope that helps. No "apply" or "save", just quit and the changes are made instantly.

And on a different note, I have got kxdocker working in Edgy, Gnome (without Beryl) by using a previous version (0.39) from a Dapper repository :-)

Mike

---

### Post by airtonix on 2007-02-27
what we need here is simply another gnome-panel-applet that is the variation of the application launcher.....simple in that it is a clone of the typical launcher but it also provides dbus feedback....or even tracks its own open windows!...

would this be viable? and if so where is the specific schemtai? bring me schemta .... i must have ze planz

oh and obviuosly you can choose your icons, and optionlly a bubble them and data-emblem-feedback frames that are laid upon the app icon.

---

### Post by wataboutbob on 2007-03-02
> **amoser said:**
> How to get an apple like dock with out hassle   
 
There you go, an instant, stable, hassle free dock.  Sure it does not have all of the glitz as say kiba dock, or kxdocker; but it does have more functionality 

~Alan

Agreed! And thanks for the tips. I find it so much more useful than kiba.

---

### Post by quirt3 on 2007-03-25
I like this but dislike the little opaque things on the sides. It also lacks theming. I would use it otherwise.

---

### Post by Mblackwell on 2007-03-26
[http://www.ubuntuforums.org/showthread.php?t=375529&highlight=dock](http://www.ubuntuforums.org/showthread.php?t=375529&highlight=dock)

Check out that topic too, if you want to increase the functions of the virtual dock.

---

### Post by vedang on 2007-08-25
thanks a lot man, ur a great help...
i have compiz-fusion installed, and for some reason, awn looks really ugly. This is much better.

---

### Post by adjohnson916 on 2007-11-25
> **airtonix said:**
> what we need here is simply another gnome-panel-applet that is the variation of the application launcher.....simple in that it is a clone of the typical launcher but it also provides dbus feedback....or even tracks its own open windows!...

For tracking its own open windows, look at this:

[http://ubuntuforums.org/showthread.php?p=2243803](http://ubuntuforums.org/showthread.php?p=2243803)

I think this will provide all the basic functionality of a launcher if it works, though still without the eye candy and the new trendy Leopard-esque "stacks" feature of the official standalone docks...

---

### Post by HA5TY on 2007-11-25
Can anybody post a picture of the final thing?

---

