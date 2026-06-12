---
title: "Improve Ubuntu icon theme / network manager"
date: 2007-05-22
forum: Outdated Tutorials &amp; Tips
---

### Post by njee on 2007-05-22
USE AT OWN RISK!

There are a number of modifications floating out there that will improve the look of Ubuntu's default icons and this is my little contribution; a Human network-manager applet (Screenshot attached)

Changes the blue wireless signal bars to human/caramel theme to blend in with the desktop a bit better. An orange one was experimented with but it didn't look very good.

Download the attached nmhuman.tar.gz to your home directory and then run the following commands from the terminal.

```
sudo tar -zxvf nmhuman.tar.gz -C /usr/share/icons/Human/22x22/apps/
```

```
cd /usr/share/icons/
```

```
sudo gtk-update-icon-cache --force Human
```from the left click on the network-manager wireless icon and they should transform to the new version.

To undo the changes simply 

```
sudo rm /usr/share/icons/Human/22x22/apps/nm-signal-*
``````
sudo gtk-update-icon-cache -f /usr/share/icons/human/
```and then left click the icon one more time.

This modification will only work if you are using Human as your icon theme.

The bars are humanized but the connection animation hasn't been because I'm not very good with GIMP. If anyone wants to make their own, the original icons are found in..

/usr/share/icons/hicolor/22x22/apps/

I'm more than happy for other people to improve this.

There are a few other modifications I'd like to include in this guide, specifically for Rhythmbox, Synaptic and gtkpod but I haven't written a guide yet, expect more to come...

---

### Post by njee on 2007-05-25
Part 2 is an improved icon set for gtkpod, possibly the most ugly gnome application I know of. Having it look nice actually makes it usable for me until rhythmbox gets its shuffle/cover art transfer up to snuff.

Screenshot  of the icons are attached, to install download the attached archive to your home directory and run the following command from the terminal

```
sudo tar -zxvf gtkpodicons.tar.gz -C /usr/share/gtkpod/pixmaps/
```

Once you load up the program the new icons should be visible. I don't think it changes the menu icon but you can do that using alacarte since you know where the icons are located now.

To remove these changes the easiest way to to purge gtkpod in synaptic and just reinstall it; unpacking the original artwork.

---

### Post by njee on 2007-05-26
Part 3 is an an improved look for rhythmbox, another application people spend a lot of time looking at with a couple of unattractive icons.

This "guide" isn't really my own work, rather based on the most excellent guides posted by Lauri Taimila on his website ([http://www.taimila.com/orange-look.php](http://www.taimila.com/orange-look.php)) with a radio icon gleaned from another thread ([http://ubuntuforums.org/showthread.php?t=426773](http://ubuntuforums.org/showthread.php?t=426773)) in which gamma compiled a tango set from these icons ([http://bugzilla.gnome.org/show_bug.cgi?id=380896](http://bugzilla.gnome.org/show_bug.cgi?id=380896)).

However I'll post it here clearly and complete so that its a bit easier to follow.

Download the icons attached in this post to your home directory.
```

sudo tar -zxvf rhythmboxhuman.tar.gz -C /usr/share/icons/Human/24x24/apps/
```
```

cd /usr/share/icons/
```
```

sudo gtk-update-icon-cache --force Human
```

rhythmbox should now look significantly better. To reverse the changes simply browse to the directory you unpacked them to above and delete them, comparing to the icons from the tar if you extract it somewhere else. then update the icon cache with the second two commands above and you're all set.

---

### Post by njee on 2007-05-26
Lastly Lauri also made a nice "system-upgrade" icon for synaptic, which I'll include here.

To install is the as the rhythmbox icons, namely, download the attached icon to your home directory.

```
sudo mv system-upgrade.png /usr/share/icons/Human/24x24/apps/
```

```
cd /usr/share/icons/
```

```
sudo gtk-update-icon-cache --force Human
```

to remove all you have to do is enter

```
sudo rm /usr/share/icons/Human/24x24/apps/system-upgrade.png
```

```
cd /usr/share/icons/
```

```
sudo gtk-update-icon-cache --force Human
```

---

### Post by njee on 2007-05-26
one of the icons for the rhythmbox iconset was broken, so I fixed it.

Here is the better set

---

### Post by Emx on 2007-05-26
For me, these icons are great!

---

### Post by DC@DR on 2007-05-26
Thanks alot for your efforts, njee :-)

---

### Post by timmie on 2007-05-28
Hello,
very nice. Will you try to get these icons into the official artwork?

Then everybody could easily use them!

Thanks for your tutorial.

---

### Post by deadlydeathcone on 2007-05-30
Thanks for the icons, they're great. I made a deb of Rhythmbox 0.11 and added some of your icons that they missed in the official release [here]("http://ubuntuforums.org/showpost.php?p=2739776&postcount=18").

I didn't think it would work out as those icons are part of the gnome theme, but the trick was to install them to /usr/share/rhythmbox/icons/gnome.

edit: a screenshot is probably a good idea:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=33801&stc=1&d=1180498134[/IMG]

---

### Post by njee on 2007-05-30
There seems to be a broad agreement that rhythmbox needs a new look. I definitely feel that Lauri's icons blend in with Ubuntu human a lot more but the tango icons are much improved from the generic ones. I've filed bugs in launchpad and provided links and files so we'll see what happens; I'm not especially optimistic though as Lauri's "dist upgrade" icon bug has been kicking around for over a year now I think. Maybe it has something to do with licensing; its not immediately clear who has done all the work and what conditions they've set on their release. As far as I'm concerned the gtkpod and network man are just revisions of existing gpl'd  icons and I'm hoping the rhythmbox ones are the same.

Thanks for checking out the icons!

EDIT: deadlydeathcone are the tango icons built into the package? Do you have a deb without the modifications I can play with? I've been waiting for new rhythmbox so I can dump gtkpod; I would really appreciate it.

---

### Post by deadlydeathcone on 2007-05-31
> **njee said:**
> I've filed bugs in launchpad and provided links and files so we'll see what happens; I'm not especially optimistic though as Lauri's "dist upgrade" icon bug has been kicking around for over a year now I think. Maybe it has something to do with licensing; its not immediately clear who has done all the work and what conditions they've set on their release.

From what I can tell it's because everyone's (slowly) moving over to a new gtk icon spec for application specific icons, causing a lot of bugs like that to end up on the backburner.

> **njee said:**
> EDIT: deadlydeathcone are the tango icons built into the package?

Yeah, all of the icons in the screen I posted above except for those on the Queue, Repeat and Shuffle buttons come from the official release. The only icon changes I made besides that were replacing the replace the legacy rhythmbox application icon with the newer, tangoed one (which is on the tooltip in the screen above) and adding in a 22x22 rhythmbox icon for the gnome menus.

> Do you have a deb without the modifications I can play with? I've been waiting for new rhythmbox so I can dump gtkpod; I would really appreciate it.

There's actually a repository that just got set up for it [here]("http://blog.blackdown.de/2007/06/01/rhythmbox-0110-for-ubuntu-feisty-fawn/"). It's the same as vanilla 0.11 except for one added plugin.

---

### Post by Miguel on 2007-08-15
Sorry for resurrecting the thread but am I the only one that finds the new rhythmbox icon too similar to a bluetooth icon? I mean, it's nice and all, but being white with some blue circles might lead to some confusion. IMHO, a tad greyer loudspeaker might be better.

---

