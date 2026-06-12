---
title: "HOW TO: Change your mouse icon theme in a standalone window manager"
date: 2008-03-01
forum: Outdated Tutorials &amp; Tips
---

### Post by p_quarles on 2008-03-01
This is a very simple, step-by-step guide to installing and using new X mouse themes without the need to rely on a GUI configuration tool. This is useful for anyone who uses a standalone window manager as their graphical interface. Window managers such as Fluxbox and Openbox do not include tools for altering the mouse theme. At the same time, many users of these window managers are pretty picky about the look and feel of their desktop.

While attempting to figure out how to set this theme, I found several tutorials online, but none of them explained how to work with Ubuntu's file structures. For that reason, I'm making a tutorial that is specific to Ubuntu and many other Debian-based Linux distributions. I have specifically tested this on two separate machines: a desktop running x86-64 Debian Testing, and a laptop running i386 Ubuntu 7.10. 

**Step 1**:

Download and locate a mouse icon theme archive. For our purposes, we'll use the Neutral theme available at kde-look.org:
[http://www.kde-look.org/content/show.php/Neutral?content=28310](http://www.kde-look.org/content/show.php/Neutral?content=28310)

Once you have this, locate the file and unpack it:
```
tar -zxvf 28310-neutral-1.13a.tar.gz
```
This will unpack the archive into a new directory called neutral. 

**Step 2**:

Some icon theme packs may have installation scripts, but I'm going to advise that you simply ignore these. Before installing them, though, check to make sure you do not already have a theme with the same name:
```
ls /usr/share/icons
```
If you see a directory there with the name of the theme you are about to install, you should change the name of the new theme prior to proceeding.

Now, copy the new directory into the icon theme path:
```
sudo cp -R neutral/ /usr/share/icons
```
Installing the theme is truly as simple as that. 

Step 3:

You will now have to edit a file to make the new theme load up automatically. As always, when playing around with system configuration files, make a backup first:
```
sudo cp /usr/share/icons/default/index.theme /usr/share/icons/default/index.theme.bak
```
With the backup saved, you can now edit the file:
```
sudo nano /usr/share/icons/default/index.theme
```
The text file will look something like this:
```
[Icon Theme]
Inherits=core
```
To change the default theme, simply replace the value of Inherits with the directory name of the theme you want. In this case, it should now look like:
```
[Icon Theme]
Inherits=neutral
```
Save the file and exit the text editor.

The change will not take effect globally until you have restarted the window manager, but you can still test it to make sure it worked. Start any graphical application. Once you hover the mouse inside this application, you should see the new mouse icon theme. If you don't, check the file you just edited for any mistakes.

If it passes the test, you can now log out of your window manager (by pressing ctrl-alt-backspace), and then start it back up. The new icon theme will now be applied globally.

To revert this change, simply restore the backup file you made in step 3, by running this command:
```
sudo mv /usr/share/icons/default/index.theme.bak /usr/share/icons/default/index.theme
```

You can find many other good mouse icon themes at kde-look.org and gnome-look.org. Enjoy.

---

### Post by bhavi on 2008-03-24
Thanks ubuntu forums rock..

---

### Post by Jose Catre-Vandis on 2008-09-18
Thanks, finally found it :)

---

### Post by urukrama on 2008-09-19
Thank you, p_quarles.

You can also specify the mouse cursor theme in /home/USERNAME/.Xdefaults. To change the mouse cursor theme in this way, add the following to that file:

```
Xcursor.theme:NAMEOFTHETHEME
Xcursor.size:  SIZE #optional
```

Change the mouse Xcursor.theme to whatever your preferred theme is named. Some cursor themes can display more than one size; if you use a theme like that, you can specify the size with the second line (normal sizes are 32, 48 or 64). If the cursor theme only has a single size, this line is meaningless.

You can install cursor themes in /home/USERNAME/.icons or /usr/share/icons/. Make sure the name you specify in ~/.Xdefaults matches the name of the folder the theme is stored in (as always case sensitive). When you restart X, the new cursor theme should be applied.

If you prefer graphical tools, you could try out gcursor, a Gtk application to change cursor themes (with previews).

---

