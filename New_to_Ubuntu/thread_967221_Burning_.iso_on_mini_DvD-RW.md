---
title: "Burning .iso on mini DvD-RW"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by elecninja on 2008-11-01
Is it possible to burn the Kubuntu iso to a mini DVD-RW?

And if so, can someone show me how to do it?

I'm using a Memorex DVD-RW that can store 1.4 GB.

---

### Post by roachk71 on 2008-11-01
It certainly can be done, given the right DVD burner (Mine gave me absolutely no problems at all burning a CD ISO image to a standard-sized DVD-R, at least, ) although it did give me one heck of a time burning to a rewritable medium.

I simply gave up on DVD-RW media and invested in a decent brand of DVD-R disks.

At present, I have no writable media (and my drive is disconnected for dual hard disk experimentation and testing,) but I'll try to guide you through the process anyway:


These instructions apply to the standard Ubuntu burning method, which doesn't always work correctly in Gutsy. If you need instructions for a different burning program, please feel free to ask.

[LIST=1]
[*]Insert the DVD medium you'd like to burn the image to into the burner
[*]If you haven't changed this setting in System-->Preferences-->Removable Drives and Media, a file manager window will pop onto the screen. Navigate to the folder containing your ISO image.
[*]Right-click on the ISO file, and select Burn to CD/DVD, and follow the burning popups from there. Once it finishes, you should have a bootable disc.
[/LIST]
If GNOME doesn't give you the file manager window, or you've changed the aforementioned setting, simply insert the disc, open the file manager using the Places menu, browse to the folder, and follow instruction #3.

A word of caution: You may not be able to erase and rewrite the DVD-RW once it has been used, depending on which drive you own. Also, there have been issues in the past with the burning app crashing with a segmentation fault, which could corrupt your newly-burned disc, so be careful. :-|

Oh, and a word of advice: I've always had problems with Memorex discs. In every batch I bought since 2002, almost all were defective. I advise using TDK or Taiyo Yuden media.

---

### Post by elecninja on 2008-11-02
Actually I'm using K3b in Kubuntu and that is only giving me the option to burn to CD-R or CD-RW for the .iso file.

---

### Post by roachk71 on 2008-11-03
You might consider installing Brasero from the repositories, using Adept Package Manager. Not to worry about running it from KDE, since all of the program's dependencies will be handled automatically. If you'd like a more consistent desktop theme (as opposed to terrible-looking base GTK+ graphics,) you might want to install gtk-qt-engine as well, and enable it in your Appearance configuration.

I made a stupid mistake last night, so I had to reinstall my OS. I'm using Xubuntu 8.04 now, and Brasero is installed by default.

---

