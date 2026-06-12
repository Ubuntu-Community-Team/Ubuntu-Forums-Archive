---
title: "Can't find certain configuration screens to customize Ubuntu"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by socref on 2008-04-22
Hello. I am a new Ubuntu user (7.10). I can make the changes described below once I know where to do them. I've looked everywhere for customization screens, but I just can't seem to find the location(s). Your help to this "noob" is appreciated. :) 

1) I have successfully customized icons for my applications by right-clicking the original icons and selecting properties, then browsing to the folders where the icons were stored, and then applying. That was simple.

But I would like to change the default icon for my folders. Where do I go to make a global change of this icon?

2) I would like to have all video clips open in something other than the default player, Totem. Where do I change this to set another player (e.g., Kaffeine) as the default?

I know it must be right in front of my nose, but I just can't find where to do this.  :confused:

3) Where do I set other file associations (for example, so that presentations open in Powerpoint by default rather than in Open Office Presentation)? I am using Crossover Office to run Windows applications. 

I can do this one at a time by right clicking the file and selecting "open with," but I want to change the default so I'm not doing this over and over. Again, it must be right in front of my face but I just don't see the place to reset the defaults.  ](*,)

Many thanks! As you can see, I just need help with where to do these changes, not how to make them.

Socref

---

### Post by noswal on 2008-04-22
system > prefernces > theme  pick one and you can change icons in theme details


Right click a file > properties > open with ,.... whatever

---

### Post by ace007 on 2008-04-22
> 
But I would like to change the default icon for my folders. Where do I go to make a global change of this icon?

You can manage icons from the Settings>Preferences>Appearance GUI.  I dont know if that is exactly what you looking for, but it is the default icon manager.

> 
2) I would like to have all video clips open in something other than the default player, Totem. Where do I change this to set another player (e.g., Kaffeine) as the default?

3) Where do I set other file associations (for example, so that presentations open in Powerpoint by default rather than in Open Office Presentation)? I am using Crossover Office to run Windows applications.

I can do this one at a time by right clicking the file and selecting "open with," but I want to change the default so I'm not doing this over and over. Again, it must be right in front of my face but I just don't see the place to reset the defaults.


Right click on any file type and go to properties.  The last tab will control what program opens that file type.  This tab is for all file associations, not just that file.  I think that counts as "in front of your nose". :)

---

### Post by socref on 2008-04-22
> **noswal said:**
> system > prefernces > theme  pick one and you can change icons in theme details


Right click a file > properties > open with ,.... whatever


For the first suggestion: system>preferences> (appearance??)> theme, I looked and I see where I can change to select other icon themes, but I don't see anywhere there to customize **individual** icons such as the folder. Am I looking in the right place?

For the second suggestion, that's perfect. Thanks!!!  :)

socref

---

### Post by socref on 2008-04-22
> **ace007 said:**
> You can manage icons from the Settings>Preferences>Appearance GUI.  I dont know if that is exactly what you looking for, but it is the default icon manager.


Right click on any file type and go to properties.  The last tab will control what program opens that file type.  This tab is for all file associations, not just that file.  I think that counts as "in front of your nose". :)


Hi, thanks for reply. The first suggestion only appears to offer a choice of general icon themes -- packages of icons. But I don't see anywhere in there a place to customize individual icons such as the folder. 

The second suggestion is exactly what I needed (but it's not the last tab, at least not in 7.10). Thanks!!  :)

If you have any other suggestions for how I can customize individual icons such as the folders, please send them along.

socref

---

### Post by Golem XIV on 2008-04-22
> **socref said:**
> For the first suggestion: system>preferences> (appearance??)> theme, I looked and I see where I can change to select other icon themes, but I don't see anywhere there to customize **individual** icons such as the folder. Am I looking in the right place?

For the second suggestion, that's perfect. Thanks!!!  :)

socref

The theme icons are stored under /usr/share/icons

If you want to make changes, you can replace the icons in the theme folder (I recommend making a backup first).  Note also that many icons are actually a link ("shortcut" in windowspeak) to another icon, for example in /usr/share/icons/Human/scalable/devices the icon "drive-harddisk-usb.svg" is not really an icon but a link to gnome-dev-harddisk-usb.dev.

Once you made all your changes (you'll need admin rights to write in the /usr/share/icons folder) you need to refresh the icon cahe.  To do this, run a terminal and type
```
sudo gtk-update-icon-cache –force /usr/share/icons/theme_name
```
where theme_name is the name of the folder for that theme.

Again, make sure you have a backup of the original theme before you start playing around with it!

---

### Post by noswal on 2008-04-22
Right click a folder on your desktop, properties. Click the icon showing on the basic tab, it will open up to let you add a custom one. Open (for me) /usr/share/gnome-app-install/icons  which is location of icons for themes.

---

### Post by bmac on 2008-04-22
[FONT=Book Antiqua][SIZE=2]I believe this is what you want to accomplish with the individual folder icons.
1. Open File Browser
2. Select Folder and right click on folder icon - select properties
3. On the properties pop up box - Basic Tab - Left click on the icon
4. This opens a select icon pop up screen
5. Try searching under file system/usr/share/icons - I use a customized Human - unless you have a specific file where your storing icons - if so search in that folder. 
Hope this helps..

[/SIZE][/FONT]

---

### Post by socref on 2008-04-22
> **bmac said:**
> [FONT=Book Antiqua][SIZE=2]I believe this is what you want to accomplish with the individual folder icons.
1. Open File Browser
2. Select Folder and right click on folder icon - select properties
3. On the properties pop up box - Basic Tab - Left click on the icon
4. This opens a select icon pop up screen
5. Try searching under file system/usr/share/icons - I use a customized Human - unless you have a specific file where your storing icons - if so search in that folder. 
Hope this helps..

[/SIZE][/FONT]

Yes, that works for that one folder. But how do I do that so it's a global change of the icon for all folders? That's what I can't find.
Thx
socref

---

### Post by socref on 2008-04-22
> **noswal said:**
> Right click a folder on your desktop, properties. Click the icon showing on the basic tab, it will open up to let you add a custom one. Open (for me) /usr/share/gnome-app-install/icons  which is location of icons for themes.

I appreciate the reply, but this only changes the icon for that one folder. It is not a global change for all folders (unless I'm not understanding what you're suggesting).

Thx
socref

---

### Post by noswal on 2008-04-22
Then see my previous post about icons in the themes

---

### Post by socref on 2008-04-22
> **Golem XIV said:**
> The theme icons are stored under /usr/share/icons

If you want to make changes, you can replace the icons in the theme folder (I recommend making a backup first).  Note also that many icons are actually a link ("shortcut" in windowspeak) to another icon, for example in /usr/share/icons/Human/scalable/devices the icon "drive-harddisk-usb.svg" is not really an icon but a link to gnome-dev-harddisk-usb.dev.

Hmmm.... I don't see "drive-harddisk-usb.svg" in /usr/share/icons/Human/scalable/devices. I don't the link you're referring to. Are you pointing me to the right directory?

Also, I am not looking to change the theme. I am only looking to change one icon globally. I guess I can change one icon within a theme and that should do what I want. I'll have to try that.

> Once you made all your changes (you'll need admin rights to write in the /usr/share/icons folder) you need to refresh the icon cahe.  To do this, run a terminal and type
```
sudo gtk-update-icon-cache –force /usr/share/icons/theme_name
```
where theme_name is the name of the folder for that theme.

Can I just change one of the icons? Do I have to run this command you're suggested if I'm not replacing the entire theme?

> Again, make sure you have a backup of the original theme before you start playing around with it!

Thanks for suggestion. To this noob it feels like doing a lot more than I need. Hoping to learn. Thanks!
socref

---

### Post by socref on 2008-04-22
Hmmm.... Forgive me if I am not being clear. Am I making this request using improper terminology? 

I do not want to change the theme. I only want to change the icon the represents the folder, and I want to do this globally.

I understand how to change an individual folder icon (or any individual folder for that matter) using "properties." Please, someone explain how to change ONLY the folder icon but doing it globally.

If someone has already explained how to do this but I'm not understanding that instruction, please point it out to me.

Thanks.  :)
socref

---

### Post by socref on 2008-04-22
> **noswal said:**
> Then see my previous post about icons in the themes

Noswal, I did exactly as you suggest. It only changes that single folder. It is not a global change. 

What am I not understanding?

socref

---

### Post by Golem XIV on 2008-04-22
> **socref said:**
> Hmmm.... I don't see "drive-harddisk-usb.svg" in /usr/share/icons/Human/scalable/devices. I don't the link you're referring to. Are you pointing me to the right directory?[QUOTE]

That was just an example.  As I said, the icons are in /usr/share/icons

Here you will find a bunch of folders, named after the icon themes they belong to.  The Human theme is the default for Ubuntu and the icons in /usr/share/icons/Human are the icons used in the Human theme.

Note that the icon themes complement the window themes but they're not "locked" to the window theme.  You can easily use the Human window theme (window colours, buttons, backgrounds, etc.) with some other icon theme, like Mist.  It would look awful, though :-)  Usually the icons are designed to go with their "window-dressing" counterparts so that you have a consistent look on your system.

I am assuming that you are running Ubuntu Gutsy or Hardy.  If you're running Kubuntu, Xubuntu or another flavour then please let us know.

[QUOTE=socref;4766007]Also, I am not looking to change the theme. I am only looking to change one icon globally. I guess I can change one icon within a theme and that should do what I want. I'll have to try that.[QUOTE]

The icon theme you use defines the default (global) icon to use.  If you want to change the icon *globally* then you have to change the icon theme.


[QUOTE=socref;4766007]Can I just change one of the icons? Do I have to run this command you're suggested if I'm not replacing the entire theme?[QUOTE]

I'm sorry if I was not clear.  Yes, you can change just one icon, and by doing it the way I suggested that change will be reflected globally.


[QUOTE=socref;4766007]Thanks for suggestion. To this noob it feels like doing a lot more than I need. Hoping to learn. Thanks!
socref

It's not that difficult, really.  You need to do the following:
- Go to System -> Preferences -> Appearance and find out what main theme you're using.  By default on standard Ubuntu it's the Human theme.

- While still in the Appearance applet, click on Customize and then on the Icons tab to find out which icon theme you're using.

- Since I don't know which theme you're using now, I'll assume it's the default one - Human.

- The following must be done with root privileges, so either open Nautilus with root privileges (by typing **gksudo nautilus** in a terminal, by using "Open as administrator" in Nautilus if you have the gksu-nautilus plug-in installed, or by typing the console commands in the terminal with **sudo** before them).

- Open the /usr/share/icons folder.  Find the Human folder and make a backup of it by copying it somewhere where you can access it easily later if things turn out bad.

- Open the /usr/share/icons/Human folder. You will see a bunch of folders with the different icon sizes (8x8, 12x12 etc.).  Open the scalable folder.  Inside the icons are again divided in folders according to their type.  The standard folder icon is /usr/share/icons/Human/scalable/filesystems/gnome-fs-directory.svg

- Replace this icon file with whatever you want your folders to look like.  Note that your new icon has to have the same filename, gnome-fs-directory.svg.  This wil overwrite and destroy the old icon file.  that is why I have insisted on a backup.

- Close your root Nautilus window.  You don't need it any more and having it open is an invitation to disaster.

- Open a terminal and type
```
sudo gtk-update-icon-cache –force /usr/share/icons/Human
```
Note uppercase H.  Linux is case-sensitive.

- Done.  You may need to log off and back on for the change to take effect.

- If you have a problem, remove the new folder and restore the backup one. 

- Don't screw around with the root Nautilus window, use it only to do the stuff you need and close it when you're done.  As far as your system is concerned, it is a weapon of mass destruction :-)

---

### Post by socref on 2008-04-22
> **Golem XIV said:**
> 
[QUOTE=socref;4766007]Can I just change one of the icons? Do I have to run this command you're suggested if I'm not replacing the entire theme?[QUOTE]

I'm sorry if I was not clear.  Yes, you can change just one icon, and by doing it the way I suggested that change will be reflected globally.




It's not that difficult, really.  You need to do the following:
- Go to System -> Preferences -> Appearance and find out what main theme you're using.  By default on standard Ubuntu it's the Human theme.

- While still in the Appearance applet, click on Customize and then on the Icons tab to find out which icon theme you're using.

- Since I don't know which theme you're using now, I'll assume it's the default one - Human.


Well I'm using Clearlooks, but there is no Clearlooks folder where you've indicated I should look. I do see Human and some others, but not Clearlooks.

Any ideas?
socref

---

### Post by Golem XIV on 2008-04-22
Clearlooks uses the Gnome default icon theme, "gnome".

Your folder icon should be under /usr/share/icons/gnome/scalable/places

Looks like the icon file you want is /usr/share/icons/gnome/scalable/places/folder.svg

Just replace "Human" with "gnome" in my instructions.  Don't forget the backup!

---

### Post by socref on 2008-04-22
> **Golem XIV said:**
> Clearlooks uses the Gnome default icon theme, "gnome".

Your folder icon should be under /usr/share/icons/gnome/scalable/places

Looks like the icon file you want is /usr/share/icons/gnome/scalable/places/folder.svg

Just replace "Human" with "gnome" in my instructions.  Don't forget the backup!

Thanks again for your help and patience. One step closer, then one step back. OK, I found where I want to make the change, but I've come up against another problem -- possibly insurmountable?

The icon I want to use instead of the default is a .png. But the system seems to insist on a .svg icon. 

I tried to convert the .png to .svg using Gimp, but there does not appear to be a way to save the .png as .svg format.

So.... Must I use a .svg icon for this default folder icon? Am I out of luck trying to use a .png?

If I must use a .svg icon do you know the location of any tux icons in .svg format?

Thanks.
socref

---

### Post by Golem XIV on 2008-04-22
Ugh.  That part is certainly not trivial.

PNG files are raster (bitmap) files, SVG are vector...  There is no easy way to convert from raster to vector.

You could try [Delineate]("http://delineate.sourceforge.net/") but there is no DEB installer, you will have to compile it from source.

Also, check [this thread]("http://ubuntuforums.org/showthread.php?t=337820").

---

### Post by socref on 2008-04-22
> **Golem XIV said:**
> Ugh.  That part is certainly not trivial.

PNG files are raster (bitmap) files, SVG are vector...  There is no easy way to convert from raster to vector.

You could try [Delineate]("http://delineate.sourceforge.net/") but there is no DEB installer, you will have to compile it from source.

Also, check [this thread]("http://ubuntuforums.org/showthread.php?t=337820").

Thanks, Golem. Really appreciate your time explaining this. I was not aware of the raster/vector issues -- a little too technical for me, especially just to convert a single icon  :)  

I think the best thing is to search for some .svg tux icons and work with those. Maybe I'll be lucky and find some using Google!     

Talk to you later. Thanks again everyone. I definitely will get that icon changed once I find tux in .svg. 

socref

---

### Post by socref on 2008-04-22
Golem, that worked!! Thank you, thank you.  :)

But it was a bit weird getting there. Here's what I did.

I found an .svg icon and put it into usr/share/icons/gnome/scalable/places as replacement for "folder.svg." The original "folder.svg" I renamed and left it there.

I followed your instructions, closed nautilus, and opened a terminal to use your specified command:  

sudo gtk-update-icon-cache –force /usr/share/icons/gnome

But the response I got back was: 

No theme index file in '–force'.
If you really want to create an icon cache here, use --ignore-theme-index.


Well that left me stumped and I did not know what to do. So I followed your next instruction (hoping, hoping, hoping not to cause a disaster) and restarted the computer. 

Voila! My folders all now have the new .svg icon. :popcorn:

So I don't know if I blundered into getting what I wanted despite ignoring the response I got in the terminal or if it was OK to ignore that response. 

Any guesses? Was I lucky not to have screwed up things?

I guess we'll see if things remain.  

In any case, issue solved. I tried to mark the thread as "solved" but that function has been disabled in this transition to the new style.

Next I have to do something similar to change the default icons for things like my text documents, spread sheet files, etc. Now I just have to hunt down where those other default icons reside.

To everyone on the list who helped me here, thumbs up!
socref

---

### Post by Golem XIV on 2008-04-22
Glad it worked!  The "-force" parameter is actually "--force" (with two dashes in front) but the font in the forum made it look like one long dash.

Usually in Linux parameters with one letter are passed with one dash, while parameters that are entire words are passed with a double dash.  For example, **ls -s** is the same as **ls --size**

Some additional tips:
- The Tango icon theme goes very nicely with the Clearlooks one.  Tango is not installed in Ubuntu by default but you shoud be able to find it on Synaptic.  There are 3 files: tango-icon-theme, tango-icon-theme-common and tango-icon-theme-extras.
- Check out [Gnome Art]("http://art.gnome.org/") or [Gnome Look]("http://www.gnome-look.org/") for some cool icon themes.  Installing them is a snap, just drag and drop the downloaded tar.gz file over the Appearance Manager (System -> Preferences -> Appearance)
- Play around with it.  Check the other icon themes so you can get an idea of the typical structure - which type icons go where, etc. - and then maybe make your own compilation as a separate icon theme.

Good luck!

---

### Post by -gabe-noob- on 2008-04-22
if it's an icon theme, at the place where you select a theme (e.g. human) you can click on the install button and set it as your icons.

---

### Post by redbob on 2008-04-23
You may also install another themes for Ubuntu, Try to install then by Synaptics and search for "gdm themes" or "gnome themes"

---

