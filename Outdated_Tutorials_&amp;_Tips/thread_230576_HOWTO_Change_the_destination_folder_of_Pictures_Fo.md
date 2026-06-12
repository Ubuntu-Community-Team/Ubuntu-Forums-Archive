---
title: "HOWTO: Change the destination folder of Pictures Folder in Screensaver"
date: 2006-08-06
forum: Outdated Tutorials &amp; Tips
---

### Post by dage on 2006-08-06
In gnome 2.0 there is a screensaver call "Pictures folder" , to use this screensaver you have to have a folder named "Pictures" in your home folder. The screensaver will slideshow all pictures in this folder.

To change the folder destination of this screensaver (Ex : /media/win_d/tux instead of your Pictures folder in your home folder) :
_ sudo gedit /usr/share/gnome-screensaver/themes/personal-slideshow.desktop
_ Go to line 95 (Exec=slideshow --location=Pictures)
_ Change the name of the destination folder (Pictures) with what ever you want like /usr/share/pixmaps or /media/win_d/blabla . If the destination folder is in your home folder you can just put the name of your folder (yourfolder) but not the whole name (/home/yourname/yourfolder)

Hope that I didn't duplicate someone :D

have fun ;)

---

### Post by fishonadish on 2006-10-24
For Edgy it's /usr/share/applications/screensavers/personal-slideshow.desktop

It's a strange lack of configurability in the screensaver app that there isn't a GUI option for this...

---

### Post by hikaricore on 2006-10-25
> **fishonadish said:**
> It's a strange lack of configurability in the screensaver app that there isn't a GUI option for this...

Yea, you can thank the wonderful folks who gave us gnome for butchering xscreensaver.  Just about the only thing they went wrong with in my opinion.

---

### Post by bford16 on 2008-05-04
In Hardy Heron, the line is simply "exec=slideshow."  To customize the location, just add "--location=PATH," where PATH is the location of your pictures.

---

### Post by oliwek on 2009-03-24
thanks for your tip bford16, it works well in intrepid too...

(just do not use ~ in the PATH : for example type "--location=/home/xxx/Pictures/screensaver" instead of just "--location=~/Pictures/screensaver", or strangely it doesn't work)

---

### Post by shane2peru on 2009-05-12
We are all the way up to Jaunty and still editing this file. :)  Works for me too.  The file is located here:
/usr/share/applications/screensavers/personal-slideshow.desktop
And it is a little smaller now-a-days looks like this:
```

[Desktop Entry]
Encoding=UTF-8
Name=Pictures folder
Comment=Display a slideshow from your Pictures folder
Exec=slideshow 
TryExec=slideshow
StartupNotify=false
Terminal=false
Type=Application
Categories=GNOME;Screensaver;
OnlyShowIn=GNOME;
X-Ubuntu-Gettext-Domain=gnome-screensaver

```

Needs changed to this:
```

[Desktop Entry]
Encoding=UTF-8
Name=Pictures folder
Comment=Display a slideshow from your Pictures folder
Exec=slideshow[COLOR="Red"] --location=/home/username/Location_of_Pictures[/COLOR]
TryExec=slideshow
StartupNotify=false
Terminal=false
Type=Application
Categories=GNOME;Screensaver;
OnlyShowIn=GNOME;
X-Ubuntu-Gettext-Domain=gnome-screensaver

```

---

### Post by johnjaylward on 2009-08-05
You could always just create a symlink to whatever folder you want under the Pictures folder in your home directory. This way it isn't a system wide change, and you can easily swap out what photos to show. Although it would be nice if there was a settings option to adjust this from the Screen Saver configuration.

example:
cd ~/Pictures
ln -s /multimedia/Pictures/2009

---

### Post by yoghurt on 2009-08-11
> **johnjaylward said:**
> You could always just create a symlink to whatever folder you want under the Pictures folder in your home directory. This way it isn't a system wide change, and you can easily swap out what photos to show. Although it would be nice if there was a settings option to adjust this from the Screen Saver configuration.

example:
cd ~/Pictures
ln -s /multimedia/Pictures/2009

Yes, that is a better method I think. Kudos :)

---

### Post by helicase on 2009-10-02
And now for Karmic...

I had it set up just fine in Jaunty with --location=/PATH. Unfortunately, this was overwritten when I updated to Karmic beta, so I put the --location=/PATH back. Well, it looks OK in the preview window of the screensaver menu and the full screen preview, but when the actual screensaver activates I still get the default pictures folder.

I also had a look at the cosmos screensaver, which is basically the same screensaver, but using a different folder; and that one works. Any ideas?

---

### Post by Lessss on 2009-11-11
I gave up on this route and instead selected in the screen saver to use F-spot photos. Then in Fspot I imported the drive folder location and it imported all the picture locations ( not the pics).  When I want to add a photo, I open Fspot and drag the photo into fspot and it creates a new link.  It took a while to import my 20,000 pics but it didn't crash the screen saver like the other methods I tried.

---

### Post by armag.info on 2009-11-24
Any clue how to make gnome screensaver to look for images recursively? Lessss, I think I'll go the same way:)

---

### Post by geoffm on 2010-06-06
The config file path has changed since.

now you have to edit: /usr/share/applications/screensavers/personal-slideshow.desktop

There's the line:
Exec=/usr/lib/gnome-screensaver/gnome-screensaver/slideshow --location=Pictures

Change "Pictures" to your screensaver pictures folder.

For example, in my case the line is:
Exec=/usr/lib/gnome-screensaver/gnome-screensaver/slideshow --location=Pictures/screensaver/

the subfolder "screensaver" contains symlinks to the folders that I want to include in the slideshow.

---

### Post by wiredsoul on 2010-09-08
Perhaps its a bit late to weigh in on this post, but I just found that the slideshow theme engine now uses [XDG User Dirs]("http://www.freedesktop.org/wiki/Software/xdg-user-dirs") to find the Pictures folder.  So given the default setup you should be able to edit $HOME/.config/user-dirs.dirs and modify the line:
[INDENT]XDG_PICTURES_DIR="$HOME/pics"
[/INDENT]to something like:
[INDENT]XDG_PICTURES_DIR="$HOME/my-pic-folder"
[/INDENT]This is not idel as it may break other apps that might use XDG settings.  I just started using it and havnen't noticed a problem yet, and it does solve the screensaver issue on Karmic (9.10, linux-2.6.31-22-generic).

HTH,
mrb

---

### Post by i.am.technofreak on 2010-10-18
Thanks wiredsoul, that fixed it for me on maverick.  couldn't figure out why my changes in the .desktop files weren't doing anything.  Now all is well!

---

### Post by maxpoweron on 2011-01-27
Thanks wiredsoul!  Just like i.am.technofreak said, it works on Maverick!

---

### Post by mjones41 on 2011-08-28
I agree with Lessss

The easiest way is to install F-spot, and import in to F-spot (and mark as favourites) the photos or folder you want.  Then the F-spot option will come up in your gnome screensaver options.

The best use yet for F-spot ;)

---

