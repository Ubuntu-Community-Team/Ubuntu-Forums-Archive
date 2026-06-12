---
title: "Gnome 3 Startup Applications"
date: 2012-06-06
forum: New to Ubuntu
---

### Post by s2001t on 2012-06-06
Hi all, I am looking for some help here.  I just installed 12.04, on my lenovo x61 tablet.  I use Magick-Rotation to rotate the screen.  I have been able to add magick rotation to the startup apps fine, and it works with no issue if I login using the classic gnome.  However if I login under "gnome" it will not start up, and needs to manually be started to work.  It all worked fine when I was running 12.04 under WUBI... Any ideas?

---

### Post by cortman on 2012-06-06
Press Alt+F2 to bring up the Run dialog. Type gnome-session-properties. Click the "Add" button. In the resulting dialog box give the name of the program and the command to start it up (probably magick-rotation. Click add and close.

---

### Post by s2001t on 2012-06-06
@Cortman, thank you for the reply.  I have already tried that, and it still does not initiate on startup under the "gnome" login option.  Again, if I login to "classic gnome" it works fine.  It seems to only work, when I manually start it, when I log into "gnome".

---

### Post by cortman on 2012-06-06
Hm, on a tablet I'm not sure how to get it working. I found [this thread]("http://ubuntuforums.org/showthread.php?t=1900347") about using it on another tablet- don't know if it's useful or not.

---

### Post by Favux on 2012-06-06
Hi s2001t,

Are you running it from the folder or did you use the Installer to install it?  If you used the Installer it should have already been in Startup Applications.

I run it in Fedora with Gnome and don't seem to have a problem.  If installed make sure the full path is in Startup:
```
/usr/share/magick-rotation/magick-rotation
```

---

### Post by wilee-nilee on 2012-06-06
Gnome 3 is using the window manager mutter I believe, might not be compatible. Compiz will run in the classic I believe as well.

---

### Post by Favux on 2012-06-07
I installed Gnome3 shell from the repository on my 12.04 and I see the issue.

Works fine after a manual start of magick-rotation (dbl-click on it and choose Run) in /usr/share/magick-rotation/ but doesn't load with auto-start (Startup Applications).

Are you using the Gnome3 shell from the Ubuntu Precise repositories?  Since it seems to load OK on Fedora's Gnome3 shell I'm tempted to think it is a bug in the repository's version.  That's why I asked if you installed from the repository.  Maybe the version from the Gnome3 team's PPA would work?
[https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)

---

### Post by Favux on 2012-06-14
**[SIZE="3"]Solved the issue![/SIZE]**

Using the PPA didn't fix anything.  Still think it is a Gnome Shell bug.  See this Launchpad bug report:  [https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/997112?comments=all](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/997112?comments=all)

So using:
```
gksudo gedit ~/.config/autostart/magick-rotation.desktop
```
open Magick's .desktop file and at the bottom add:
```
X-GNOME-Autostart-Delay=1
```
so it looks like:
```
[Desktop Entry]
Type=Application
Name = Magick Rotation for tablet pc's
Exec = %s
Icon = redo
Comment=Helps with automatic rotation
X-GNOME-Autostart-Delay=1
```
And log out and back in.  If 1 doesn't work try 2 or 3, doubt you'll need to go higher.

---

