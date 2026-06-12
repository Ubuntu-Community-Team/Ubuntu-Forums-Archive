---
title: "HOWTO: Get the Debian menu which lists all installed apps"
date: 2005-10-22
forum: Outdated Tutorials &amp; Tips
---

### Post by coolblue on 2005-10-22
The Debian menu is EXTREMELY USEFUL!!!....quite often u'll find that certain apps u had installed via APT/synaptic do not appear in the KDE/Gnome menu but u can be almost sure that if its not there, it MUST be in the Debian menu:D ....and then u can copy ur fav app from the Debian menu into ur KDE/Gnome menu. Do u miss the Debian menu which listed all installed apps on your system?

To get it:

1. Enable the breezy Universe repository
2. sudo apt-get update
3. sudo apt-get install menu

Thats it:p 

Atleast for me its been very useful. Things like dvdrip, acidrip, bioinformatics apps and other unconventional or non-KDE/non-gnome apps usually cannot be found in the KDE/Gnome menu but u'll easily spot them in the Debian menu if u've installed them.

Hope this helps:cool: 

Don't forget to give me ur feedback;)

---

### Post by tseliot on 2005-10-22
How do I access this Debian menu?

---

### Post by fog on 2005-10-22
Applications-->Debian :)

---

### Post by tseliot on 2005-10-22
thanks

---

### Post by Mustard on 2005-10-22
Ah cool.  I've been wondering how to do this.  I had it going in Hoary, and was missing it greatly after a clean install of Breezy.

Much appreciated. :)

-edit-

Just tried it and it hasn't yet appeared in my menu.  I tried a killall gnome-panel, with no luck.  I checked the menu editor and I can see it there, but it won't allow me to tick it.  I expect it will be there after I reboot, but I'm online atm (dialup) and I won't be resetting the computer until I get my .25 cents worth out of this connection. :)

I'll report back later on whether it appeared after a reboot.

---

### Post by LaserJock on 2005-10-22
The reason that the Ubuntu menu has less items than the Debian menu is that Ubuntu uses the freedesktop.org specifications for .desktop files (where menu and mime type information is held) and Debian doesn't. I believe (but could be wrong) that this is because Ubuntu uses Xorg instead of Xfree86. Anyway, all the packages from Debian need to have a proper (according to freedesktop.org) .desktop file placed in the right directory. To do this the .deb packages need to be rebuilt. This is also fairly low on the todo list for the Universe developers so a  lot hasn't been done. If you want to help, [http://wiki.ubuntu.com/UniversePackageWithoutDesktopFile](http://wiki.ubuntu.com/UniversePackageWithoutDesktopFile) has a list (I don't think it is very current but it is a place to start) of packages that need a new .desktop file. If you aren't familiar with packaging just make the .desktop file and  add it to [http://wiki.ubuntu.com/UniversePackageWithoutDesktopFileExampleFiles](http://wiki.ubuntu.com/UniversePackageWithoutDesktopFileExampleFiles) or talk to the guys at #ubuntu-motu on irc.freenode.net . Any help would be appreciated.

-LaserJock

---

### Post by traherom on 2005-10-22
[QUOTE=Mustard]Ah cool.  I've been wondering how to do this.  I had it going in Hoary, and was missing it greatly after a clean install of Breezy.

Much appreciated. :)

-edit-

Just tried it and it hasn't yet appeared in my menu.  I tried a killall gnome-panel, with no luck.  I checked the menu editor and I can see it there, but it won't allow me to tick it.  I expect it will be there after I reboot, but I'm online atm (dialup) and I won't be resetting the computer until I get my .25 cents worth out of this connection. :)

I'll report back later on whether it appeared after a reboot.[/QUOTE]Use smeg (Applications -> System Tools -> Applications Menu Editor) to turn it on. It took me a few tries to get the option to stick, but it's there now. :)

---

### Post by ToastedToad on 2005-10-22
Hmmmm, no matter what it will not stay ticked, actually it will not tick at all....same thing on both 32bit and 64bit Breezies.

---

### Post by Mustard on 2005-10-23
I can confirm that it will not tick, regardless of what I do.  I can see the option in the menu.  In fact if I remember rightly, it was there before I even installed this.  So I would say that installing 'menu' hasn't actually changed anything on my Breezy 2.6.12-9-686 kernel.

---

### Post by graveman on 2005-10-23
i can't get it to work  ... it just won't let me tick it what ever i do..
help anyone??

---

### Post by ToastedToad on 2005-10-24
It is now working on my 64bit, i don't know what did it though, maybe a reboot. I'm glad it is, as a recent Debian convert I missed it.

---

### Post by coolblue on 2005-10-24
[QUOTE=graveman]i can't get it to work  ... it just won't let me tick it what ever i do..
help anyone??[/QUOTE]

Well I'm on Kubuntu and it works very well..why not switch to the lovely Kubuntu?;) :p

---

### Post by Mustard on 2005-10-24
[QUOTE=coolblue]Well I'm on Kubuntu and it works very well..why not switch to the lovely Kubuntu?;) :p[/QUOTE]

Hehehe..that's one hell of a big workaround for such a little problem. :D

---

### Post by PascalL on 2005-10-24
Same problem here!
I have the debian menu working in KDE, but I can't activate it in Gnome.

Pascal

---

### Post by SilentCacophony on 2005-10-24
Hi. Just thought I'd link an older thread on the same subject here. Those that can't get the menu to appear may find more info there. It was aimed at Hoary, so it may not be entirely valid for Breezy, though.

[Howto have a menu which shows all installed applications on your system]("http://www.ubuntuforums.org/showthread.php?t=32220")

**[COLOR="Sienna"]EDIT -[/COLOR]** I tried this myself (I'm running Gnome, btw,) and had the same problem with the menu not showing under Applications. From comments in the above link, I found that installing the **menu-xdg** package will make it work for gnome. In my case, the panel updated automatically after installing the package, and it was available.

So, if you use gnome, the process would be like so:

1. Enable the breezy Universe repository
2. sudo apt-get update
3. sudo apt-get install menu [I]menu-xdg
4. update-menus
[/I]

---

### Post by davidanderica on 2006-03-20
Thank you,
update-menus worked for me in Breezy 5.10.

---

### Post by eyebrowman92 on 2006-03-20
[QUOTE=coolblue]The Debian menu is EXTREMELY USEFUL!!!....quite often u'll find that certain apps u had installed via APT/synaptic do not appear in the KDE/Gnome menu but u can be almost sure that if its not there, it MUST be in the Debian menu:D ....and then u can copy ur fav app from the Debian menu into ur KDE/Gnome menu. Do u miss the Debian menu which listed all installed apps on your system?

To get it:

1. Enable the breezy Universe repository
2. sudo apt-get update
3. sudo apt-get install menu

Thats it:p 

Atleast for me its been very useful. Things like dvdrip, acidrip, bioinformatics apps and other unconventional or non-KDE/non-gnome apps usually cannot be found in the KDE/Gnome menu but u'll easily spot them in the Debian menu if u've installed them.

Hope this helps:cool: 

Don't forget to give me ur feedback;)[/QUOTE]


or you can just use automatix and install it.\\:D/

---

### Post by WoodyMahan on 2006-03-21
I just set this up and it works great.  Glad to another option for program listings.

Thanks!

---

### Post by drubulvr on 2006-06-24
I had done a bunch of apt-get's and then after several of them I went "darn it, I'll have to add them manually."

I googled, found your post, added the menu...and I just want to hug you right now!
[QUOTE=coolblue]The Debian menu is EXTREMELY USEFUL!!![/QUOTE]

---

### Post by maniacmusician on 2006-06-24
this isn't working too well for me (i'm using xubuntu) installing the menu didn't do anything, and neither did installing menu-xdg. when I used "update-menus," a category called "Others" was added to my Applications menu, with all the missing apps in it, but its not organized at all like the Debian menu. Actually, its not organized, period. It just alphabetically lists all the apps. So without the organization of the Debian menu, its pretty useless. 

so does anyone know how to make the Debian menu work in Xfce?

thanks.

---

### Post by Thund3rstruck on 2006-06-24
Damn this is really handy! Now I wonder why Ubuntu would not include this menu by default

---

### Post by afoglia on 2006-08-21
> **maniacmusician said:**
> 
so does anyone know how to make the Debian menu work in Xfce?


I figured it out.  Reading my old Breezy configuration off the hard drive, here's what I learned.

In your home directory open the ~/.config/xfce4/desktop/menu.xml file with your favorite text editor.  You're going to want to insert the lines

```

<menu name="Debian">
        <include type="file" src="menudefs.hook"/>
</menu>

```

anywhere between the <xfdesktop-menu> and </xfdesktop-menu> tags.  I inserted it immediately above the last <separator/> (line ~88), so it would appear right under the System menu.

---

### Post by Evans on 2006-11-19
i am having the same problem in gnome but i have menu-xdg and menu (used automatix) and the menu will not show - i wonder if this is dependent on something in the kubuntu package because i installed kubuntu got the menu and then uninstalled kubuntu and lost it

---

### Post by ChrisNiemy on 2006-11-20
Hi,

if you encounter problems, the solution is maybe in this thread here:
[http://www.ubuntuforums.org/showthread.php?p=1783021](http://www.ubuntuforums.org/showthread.php?p=1783021)

worked for me.

Greets, -Chris

---

### Post by sparrowhawk on 2006-11-20
Automatix !

---

### Post by arnieboy on 2006-11-20
> **Evans said:**
> i am having the same problem in gnome but i have menu-xdg and menu (used automatix) and the menu will not show - i wonder if this is dependent on something in the kubuntu package because i installed kubuntu got the menu and then uninstalled kubuntu and lost it

do the following to make the debian menu visible:
```
update-menus
```

---

### Post by mistypotato on 2007-01-12
Update-Menus ------ doesn't fix it

Automatix  ---- doesn't fix it



Sudo update-menus......"might"

---

### Post by stalefries on 2007-01-13
```
 sudo aptitude install menu menu-xdg
update-menus
```That worked for me in Ubuntu edgy.

Note: I don't use easy install scripts.

---

### Post by Tyche on 2007-03-14
In case this hasn't been updated before:

To get the Debian menu in Edgy
1. Enable the edgy Universe repository
2. sudo apt-get update
3. sudo apt-get install menu menu-xdg
4. update-menus

Earlier versions of this procedure listed Breezy.  Basically, it should work with whatever release you are using, simply by replacing the name of the release with the name of YOUR CURRENT RELEASE.  In other words:

1. Enable the <your current release name> Universe repository
2. sudo apt-get update
3. sudo apt-get install menu menu-xdg
4. update-menus

BTW, I'm not taking credit for any of the information (other than my replacing breezy with edgy to see if it would work :) )  I'm really just trying to make it easier for noobs and near noobs (my category) to get it to work.  To me, it's the most valuable menu item on the menu.

Now, if I can just remember how to do it the NEXT time I update <BIG GRIN>

---

