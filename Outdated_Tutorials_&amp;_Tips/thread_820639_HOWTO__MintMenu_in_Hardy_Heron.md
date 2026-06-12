---
title: "HOWTO:  MintMenu in Hardy Heron"
date: 2008-06-06
forum: Outdated Tutorials &amp; Tips
---

### Post by airspirit on 2008-06-06
I got irritated with the triple-menu setup in gnome due to the lack of real estate on my screen, so started looking for options.  Unfortunately, all of the old mintmenu install instructions were broken for Hardy Heron.  After lots of research, here is the easy step by step to get this working for you.

[SIZE="4"]Step 1:[/SIZE]

Add the following to your repository list:

```
http://packages.linuxmint.com elyssa main upstream import
```

[SIZE="4"]Step 2:[/SIZE]

Reload your sources and search in Synaptic for mintmenu (current is 4.0) ... install that.

[SIZE="4"]Step 3:[/SIZE]

Open a terminal and run the following commands:
```
sudo killall gnome-panel
```

After a few seconds it will restart.  Now right click on a panel and go to Add to Panel ... you'll find your new shiny mintMenu option ... drag this onto your bar.  Yay!  All done!

[SIZE="4"]Step 4:[/SIZE]

Don't like the icon?  It doesn't use the distributor-icon, so run the following to get your ubuntu icon (or do similar for your custom icon):

```
sudo cp /usr/share/icons/Human/scalable/places/distributor-logo.svg /usr/share/pixmaps/mintmenu.png
sudo killall gnome-panel
```

This switches the icon to your standard distro-logo ... almost.  Right click the menu and in preferences up the icon size and get rid of the text (if you want).  Now it looks better, no?

[SIZE="4"]Notes and caveats:[/SIZE]

There is no link to the standard Add/Remove programs icon.  If you want this, you'll have to add a link into one of your application or other menus.  The default package manager in this menu is Synaptic.  I'm pretty sure there is a way to change that, but I'm not too keen on digging that deep at the moment.  Otherwise, it is nice and pretty and stable, so enjoy!

---

### Post by Vadi on 2008-06-08
You do know that you can just add the "Main Menu" applet to a gnome panel, which is even better on small real estate than that?

---

### Post by airspirit on 2008-06-08
Yeah, I played with that as well, but didn't like it nearly as much as I do the slab-style mintmenu.  The reason that I posted this is because all of the old tutorials and walkthroughs here were broken in 8.04.

When favorites is left open in mintmenu (which for me is most all the time with my top 5-6 programs) I find it much faster than the three menu option, and presumably would find it faster and easier than the one menu option as well.  It also adds a further touch of familiarity for my spouse who is having a harder time adjusting from windows to linux.

---

### Post by Vadi on 2008-06-08
That's cool. I personally love the design of the menu bar, I think it's way more efficient than what vista / kde4 offer.

---

### Post by Gourgi on 2008-06-08
i liked it for a moment 
but i find Vadi's post quite cool also 
thanks @ both 
:popcorn:

---

### Post by moriss on 2008-06-10
For those who want to configure their mintmenu a little more:
I guess mintmenu is based on the Ubuntu system Panel, that's where you can find it:
[http://code.google.com/p/ubuntu-system-panel/w/list](http://code.google.com/p/ubuntu-system-panel/w/list)
and a here's a tutorial for installing and configuring USP:
[http://ubuntuforums.org/showthread.php?t=222546&highlight=usp](http://ubuntuforums.org/showthread.php?t=222546&highlight=usp)

But I personnally think mintmenu is the best configuration for USP, I just kept it.
Thanx

---

### Post by Jose Catre-Vandis on 2008-06-10
It's Nice :)

Unless you want loads of "Mint" branded things to update on your system, remeber to remove the mint repository from your sources.list after you have done this!

---

### Post by irieari on 2008-08-22
> **airspirit said:**
> I got irritated with the triple-menu setup in gnome due to the lack of real estate on my screen, so started looking for options.  Unfortunately, all of the old mintmenu install instructions were broken for Hardy Heron.  After lots of research, here is the easy step by step to get this working for you.

[SIZE="4"]Step 1:[/SIZE]

Add the following to your repository list:

```
http://packages.linuxmint.com elyssa main upstream import
```

[SIZE="4"]Step 2:[/SIZE]

Reload your sources and search in Synaptic for mintmenu (current is 4.0) ... install that.

[SIZE="4"]Step 3:[/SIZE]

Open a terminal and run the following commands:
```
sudo killall gnome-panel
```

After a few seconds it will restart.  Now right click on a panel and go to Add to Panel ... you'll find your new shiny mintMenu option ... drag this onto your bar.  Yay!  All done!

[SIZE="4"]Step 4:[/SIZE]

Don't like the icon?  It doesn't use the distributor-icon, so run the following to get your ubuntu icon (or do similar for your custom icon):

```
sudo cp /usr/share/icons/Human/scalable/places/distributor-logo.svg /usr/share/pixmaps/mintmenu.png
sudo killall gnome-panel
```

This switches the icon to your standard distro-logo ... almost.  Right click the menu and in preferences up the icon size and get rid of the text (if you want).  Now it looks better, no?

[SIZE="4"]Notes and caveats:[/SIZE]

There is no link to the standard Add/Remove programs icon.  If you want this, you'll have to add a link into one of your application or other menus.  The default package manager in this menu is Synaptic.  I'm pretty sure there is a way to change that, but I'm not too keen on digging that deep at the moment.  Otherwise, it is nice and pretty and stable, so enjoy!
Hi Airspirit,

I tried your method of replacing the mintmenu icon with a custom one and it worked well for my laptop, but with my other computer the terminal tells me:

"cp: target `/usr/share/pixmaps/mintmenu.png' is not a directory"

Of course it's not a directory, but a a .png file, but isn't the -cp function supposed to overwrite the destination file with the source one in this case?

---

### Post by irieari on 2008-08-22
> **airspirit said:**
> I got irritated with the triple-menu setup in gnome due to the lack of real estate on my screen, so started looking for options.  Unfortunately, all of the old mintmenu install instructions were broken for Hardy Heron.  After lots of research, here is the easy step by step to get this working for you.

[SIZE="4"]Step 1:[/SIZE]

Add the following to your repository list:

```
http://packages.linuxmint.com elyssa main upstream import
```

[SIZE="4"]Step 2:[/SIZE]

Reload your sources and search in Synaptic for mintmenu (current is 4.0) ... install that.

[SIZE="4"]Step 3:[/SIZE]

Open a terminal and run the following commands:
```
sudo killall gnome-panel
```

After a few seconds it will restart.  Now right click on a panel and go to Add to Panel ... you'll find your new shiny mintMenu option ... drag this onto your bar.  Yay!  All done!

[SIZE="4"]Step 4:[/SIZE]

Don't like the icon?  It doesn't use the distributor-icon, so run the following to get your ubuntu icon (or do similar for your custom icon):

```
sudo cp /usr/share/icons/Human/scalable/places/distributor-logo.svg /usr/share/pixmaps/mintmenu.png
sudo killall gnome-panel
```

This switches the icon to your standard distro-logo ... almost.  Right click the menu and in preferences up the icon size and get rid of the text (if you want).  Now it looks better, no?

[SIZE="4"]Notes and caveats:[/SIZE]

There is no link to the standard Add/Remove programs icon.  If you want this, you'll have to add a link into one of your application or other menus.  The default package manager in this menu is Synaptic.  I'm pretty sure there is a way to change that, but I'm not too keen on digging that deep at the moment.  Otherwise, it is nice and pretty and stable, so enjoy!
Hi Airspirit,

I tried your method of replacing the mintmenu icon with a custom one and it worked well for my laptop, but with my other computer the terminal tells me:

"cp: target `/usr/share/pixmaps/mintmenu.png' is not a directory"

Of course it's not a directory, but a .png file, but isn't the -cp function supposed to overwrite the destination file with the source one in this case?

---

### Post by airspirit on 2008-08-22
I can't tell you why your system is giving that particular error.  What you may want to try doing is renaming the original file then moving the new one there.

Try the following:

mv /usr/share/pixmaps/mintmenu.png /usr/share/pixmaps/mintmenu.png.backup

Then use the copy line and see if that does the trick for you.  If that doesn't work, mind copying in a "ls -l" of what you get in that directory?

---

