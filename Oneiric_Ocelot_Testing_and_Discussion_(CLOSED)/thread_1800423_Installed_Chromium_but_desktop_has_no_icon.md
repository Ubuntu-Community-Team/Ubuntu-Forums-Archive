---
title: "Installed Chromium but desktop has no icon"
date: 2011-07-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by iClouseau88 on 2011-07-08
Hello,

I am using Ubuntu 11.10 i386 updated July 8 just a few minutes ago.

```

uname -r

3.0-3-generic

```

I just installed chromium browser but cannot find its icon anywhere on the desktop (Unity 2D).  Search function shows, for example:

File Name @ Folder:

chromium-browser.desktop @ /usr/share/app-install/desktop

chromium-browser.png @ /usr/share/app-install/icons

Any suggestions?  Thanks for your help!

:confused:

---

### Post by rapiertg on 2011-07-09
> **iClouseau88 said:**
> Hello,

I am using Ubuntu 11.10 i386 updated July 8 just a few minutes ago.

```

uname -r

3.0-3-generic

```I just installed chromium browser but cannot find its icon anywhere on the desktop (Unity 2D).  Search function shows, for example:

File Name @ Folder:

chromium-browser.desktop @ /usr/share/app-install/desktop

chromium-browser.png @ /usr/share/app-install/icons

Any suggestions?  Thanks for your help!

:confused:

Something like that was happening to me. Weird is, that if i use gdm instead of lightdm as login manager chromium is in there as it should.

---

### Post by iClouseau88 on 2011-07-09
Hi,
Lightdm was automatically installed in one of the recent updates. Which command should I be using in order to get gdm working instead of lightdm?

---

### Post by iClouseau88 on 2011-07-09
Hi noumanshahid,

I don't understand your message.  Are you saying you have Chromium icon if you select Ubuntu in your login screen?

---

### Post by buzzmandt on 2011-07-09
If it's an upgrade you should be able to do 
```
sudo dpkg-reconfigure gdm
```
set the default manager to gdm then reboot.

---

### Post by iClouseau88 on 2011-07-09
Hello buzzmandt & rapiertg,

A check with Synaptic shows gdm as not installed, so I installed it first,set gdm as default display manager then reboot.

After reboot, still no Chrome or Chromium icon!

Synaptic shows the following packages as being installed:

[LIST]
[*]gdm 3.0.4-0ubuntu4

[*]google-chrome-stable 12.0.742.112-r9030 (I installed this yesterday via automatic method, after not seeing chromium-browser icon)

[*]chromium-browser 12.0.742.112~r9030 (installed first, yesterday)
[/LIST]

Also checked using:

```

sudo dpkg-reconfigure gdm

```

Found gdm already set as default display manager

From my experience with openSUSE, I also check to make sure libpng is installed:

[LIST]
[*]libpng12-0 installed
[*]libpng12-dev installed
[/LIST]

I may have to check in launchpad to see if this "no Chrome/chromium icon" problem is a bug.

Anyway, Unity2D is starting to get to my nerve, especially when the apps icons are sometime purposely hidden, e.g. when clicking the + sign I only see just a few icons, not seeing the terminal.  I had to hit the right pane a few times to get it to show all applications.

1.  How do I make "terminal" icon permanent?

2.  Any way I can select Gnome 3 instead of Unity2D?

Fedora 15 with Gnome 3 is much less hassle to use than Unity2D.

:(

---

### Post by buzzmandt on 2011-07-09
if gdm not installed> sudo apt-get install gdm

---

### Post by iClouseau88 on 2011-07-09
Hi buzzmandt,

Gdm already installed.

I suspect that the icon missing problem may be due to a missing shortcut or missing link that launches the application.

Any other "experts", please feel free to chime in.  Thanks.

---

### Post by iClouseau88 on 2011-07-09
Hi,

In /usr/share/themes/Radiance, there are 3 folders: gtk-2.0, gtk-3.0 and metacity1.

The first folder gtk-2.0, has a sub-folder called "Apps" which includes "chromium.rc" among other files. The folder gtk-3.0 does not have this file.

Could it be possible that Chromium does not work in gtk3 yet?

---

### Post by iClouseau88 on 2011-07-09
Hi,

It appears that for the time being, Ubuntu 11.10 alpha2 has Firefox as default web browser.  Looking at /usr/share/applications/firefox.desktop via "sudo gedit", I notice that this file is described in full, whereas the /google-chrome.desktop and /chromium-browser.desktop files are much shorter and have temporary profile.

Any suggestions?

:confused:

---

### Post by iClouseau88 on 2011-07-09
Hi,

I typed google-chrome into the terminal and got the browser running.  Now, how do I make the icon appear permanently on the desktop so that I can run the program without going to the terminal every time?

Thanks a lot for your help.

---

### Post by cariboo on 2011-07-09
Can't you just create a launcher on the desktop, then click the icon to change it, just like you normally would. 

I just tried it here on Unity 3D, it found the proper chromium icon automgically.

BTW Firefox will be the default browser for the foreseeable future.

---

### Post by VinDSL on 2011-07-10
> **cariboo907 said:**
> Can't you just create a launcher on the desktop, then click the icon to change it, just like you normally would. 

I just tried it here on Unity 3D, it found the proper chromium icon automgically.
Yep!  That's what I suggest (and what I do).
[LIST=1]
[*]Create a launcher on your Desktop.
[*]Test the launcher, to make sure it works.
[*]MOVE the launcher from your Desktop to ~/home/(username)/.local/share
[*]DRAG the launcher from ~/home/(username)/.local/share to the Launcher Panel.
[/LIST]
Works like a charm, for me...  ;)

---

### Post by iClouseau88 on 2011-07-10
Hello VinDSL,

Thanks for your reply.  First of all, there seems to be a confusion, at least on my part, about the terminology of the word "launcher".  As I understand, "launcher" refers to the "dash" or the vertical bar/column that has lots of icons on the desktop.  Because of this, I don't quite understand Steps #3 & #4 in your post.  Did you actually mean "(Chromium) icon" instead of "launcher"?  I would appreciate if you could clarify for me.

Anyway, I was able to get the Chromium browser icon working by:

1. Launch the browser application via the terminal

2. When the browser icon shows up in the "launcher/dash",right click it and select "Keep In Launcher"

3. Now the Chromium browser icon stays in the "launcher/dash" and opens  Chromium browser when I click on it

---

### Post by iClouseau88 on 2011-07-11
Hi everyone,

I found a good site that explains this "launcher" subject:

[http://askubuntu.com/questions/23816/how-to-make-use-launcher]("http://askubuntu.com/questions/23816/how-to-make-use-launcher")

Another related link:

[http://askubuntu.com/question/37434/how-do-i-add-applications-to-the-launcher]("http://askubuntu.com/question/37434/how-do-i-add-applications-to-the-launcher")

Cheers!
:)

---

