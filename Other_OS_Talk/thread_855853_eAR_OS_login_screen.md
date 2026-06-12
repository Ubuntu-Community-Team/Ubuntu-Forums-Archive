---
title: "eAR OS login screen"
date: 2008-07-10
forum: Other OS Talk
---

### Post by rutmang on 2008-07-10
Hello,

This issue revolves only around the login screen of the themes mentioned.

I installed the ubuntustudio-look package, and now I am unable to change back to the ear os gdm theme for the login screen.  I only installed it, did not make any selections to change to it from the default earos theme.  But yet, studio became the login screen background.

I click the radio button in the login screen manager window to change back to earos, close, reopen the manager and it shows no selection.

I log out and its back to the ubuntu studio login screen.  I remove ubunutu studio login screen theme from the same manager.  Logout and now its "unable to load" the studio theme screen and kicks me to default gnome footprint login screen.

Is there a way to reinstall the acoustic reality gdm theme?  I see no package in synaptic.  How can I restore the original default login screen?  Is there a "theme package" i can install from the appearance dialog?

Thanks!
Jim

oh, and... I LOVE THIS THING!

---

### Post by earos.dk on 2008-07-11
If you "crashed" the GDM theme with an overwrite the only way to bring it back is currently to rip it from the Live CD, because there is still not yet a repository and because I could not simple (in a snap) fix the Ubiquity installer to accept the eAR OS graphical GDM theme (today I could). Here is how:

1) Boot from the Live CD.
2) Mount your hard disk by clicking the hard disk icon in the upper panel.
2) Start a console - terminal
3) Overwrite the GDM themes on the hard disk with the themes from the Live CD:

sudo cp -r /usr/share/gdm/themes/*  /media/disk/usr/share/gdm/themes/*

Well, it is not tested, but I think it will work :-)

---

### Post by arvvvs on 2008-07-20
you should allow more than one folder to be the music folder, or the video.

---

### Post by earos.dk on 2008-07-20
Today, I returned from my first 8-days summer vacation WITHOUT a computer and cell phone, and therefore I have not read anything on the Internet the past 8 days :-)

--

#arvvvs,

You can create symbolic links to whatever you want to access of external disks or internal folders.

Start a terminal and go to for example the eAR-Music folder or the eAR-Video folder. Then use the 

```
ln -s  "originpath" "symbolicname"
```

command and you can access music/video files stored on external hard disks, networks or ...... everywhere inside the media center.

---

