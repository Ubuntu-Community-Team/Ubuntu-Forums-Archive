---
title: "[SOLVED] Accidentally removed my tool\deskbar"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by Eriks_Knor on 2008-09-09
Wow. THAT was educational. And it'll teach me to watch what the hell I'm doing in Synaptic Package Manager #-o

So, Like the title says, I accidentally removed my toolbar from the GNOME desktop. I have a mouse and a lovely background and NO buttons.

How do I boot to SHELL? Once I boot to SHELL, do I use *sudo apt-get install deskbar*?

Thanks a heap.
I'll be over here applying head to desk.

---

### Post by mikewhatever on 2008-09-09
You can call out a terminal windows with alt+f2, gnome-terminal, and then reinstall whatever you want. If you prefer synaptic, use alt+f2, gksudo synaptic.

---

### Post by elmoosecapitan on 2008-09-09
Did you uninstall it or just remove it off your desktop?

---

### Post by Bölvaður on 2008-09-09
what you are looking for is called gnome-panel I think

Here is a list of (some of the) programs installed that come up when I look for gnome is synaptic, so you can see which ones you might be missing.

compiz-gnome
gnome-applets   and  gnome-applets-data
gnome-control-center
gnome-desktop-data
**gnome-panel    and gnome-panel-data**
gnome-session
gnome-system-monitor
gnome-terminal    and gnome-terminal-data


so perhaps you should Alt+F2 and ask for gnome-terminal to work from there.

---

### Post by graben3 on 2008-09-09
> **Bölvaður said:**
> what you are looking for is called gnome-panel I think

I confirm... you need gnome-panel package installed

alt+F2

type : gksudo synaptic

Then search for : gnome-panel

check it and apply

---

### Post by Eriks_Knor on 2008-09-09
I was in Synaptic and I somehow marked it for complete removal.

---

### Post by Eriks_Knor on 2008-09-09
Sorry for looking like an utter dunce, but when should I hit alt+F2 during boot? Having a little trouble getting the terminal to come up.

---

### Post by starcannon on 2008-09-09
after you log into your desktop, press:

Alt+F2

then type:
```

gnome-terminal

```

Press enter, you now have a terminal.

To restore your gnome-panels (toolbars) follow this guide:
[http://ubuntuforums.org/showpost.php?p=5578191&postcount=10](http://ubuntuforums.org/showpost.php?p=5578191&postcount=10)

Have fun.

---

### Post by Eriks_Knor on 2008-09-09
> **starcannon said:**
> after you log into your desktop, press:

Alt+F2

then type:
```

gnome-terminal

```

Press enter, you now have a terminal.

To restore your gnome-panels (toolbars) follow this guide:
[http://ubuntuforums.org/showpost.php?p=5578191&postcount=10](http://ubuntuforums.org/showpost.php?p=5578191&postcount=10)

Have fun.

I've logged into my desktop, I press Alt+F2 and get nothing. Is something supposed to come up?
Also, I went ahead and swapped keyboards to make sure it wasn't an issue there. keyboard works fine.

---

### Post by Bölvaður on 2008-09-09
it seems like you are missing more than gnome-panel

are you able to Ctrl+Alt+F5 ?


edit.

if you get there, check if you can install gnome-terminal and gnome-panel from apt-get (like sudo apt-get gnome-terminal)

---

### Post by Eriks_Knor on 2008-09-09
> **Bölvaður said:**
> it seems like you are missing more than gnome-panel

are you able to Ctrl+Alt+F5 ?


edit.

if you get there, check if you can install gnome-terminal and gnome-panel from apt-get (like sudo apt-get gnome-terminal)

Yes. HAH! I have a shell login screen!

---

### Post by bobnutfield on 2008-09-09
If you can get to your desktop, right click on it, choose Create Launcher, and in the box that says Command, type:> gnome-terminal

That will create a terminal icon on your desktop and you can double click it to open a terminal.  You should then be able to download and install gnome-panel.

---

### Post by Eriks_Knor on 2008-09-09
> **bobnutfield said:**
> If you can get to your desktop, right click on it, choose Create Launcher, and in the box that says Command, type:

That will create a terminal icon on your desktop and you can double click it to open a terminal.  You should then be able to download and install gnome-panel.

There's no window when i right click. Sorry, failed to mention that earlier.
I do, however have a shell up and tried as Bolvadur suggested and typed sudo apt-get gnome-terminal. 
My response was Invalid operation gnome-terminal
AH!! Just typed sudo apt-get install gnome-terminal and it looks like it installed.
Now I just need to get it going on my desktop.

---

### Post by bobnutfield on 2008-09-09
If you were able to install gnome-terminal, then you should also be able to install the gnome-panel in the same way.  But, as previously suggested, there may be more missing than just your panel if you are not getting a pop-up menu on your desktop when you right-click on it.

---

### Post by Eriks_Knor on 2008-09-09
> **bobnutfield said:**
> If you were able to install gnome-terminal, then you should also be able to install the gnome-panel in the same way.  But, as previously suggested, there may be more missing than just your panel if you are not getting a pop-up menu on your desktop when you right-click on it.

Okay...
I installed gnome-terminal and gnome-panel via Shell.
I booted to my desktop. I have my toolbars (sorry for the Windows terminology)but i had three error prompts come up:

Error prompt the First:
The panel encountered a problem while loading "OAFID:GNOME_FastUsersSwitchApplet".
Do you want to delete the applet from your configuration?

Error Prompt The Second:
The panel encountered a problem while loading
"OAFID:GNOME_MixerApplet".
Do you want to delete the applet from your configuration?

Error Prompt The Third:
The panel encountered a problem while loading
"OAFID:GNOME_Panel_TrashApplet".
Do you want to delete the applet from your configuration?

This to me sounds like I'm going to have to spend some time in Synaptic and check a bunch of GNOME-related items to be installed.

Man, when I break it, I break it good.

---

### Post by bobnutfield on 2008-09-09
> sudo apt-get install gnome-panel-data

Try that.

---

### Post by Eriks_Knor on 2008-09-09
> **bobnutfield said:**
> Try that.

Here's what I got:

blankee@ubufile:~$ sudo apt-get install gnome-panel-data
[sudo] password for blankee: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-panel-data is already the newest version.
gnome-panel-data set to manually installed.
The following packages were automatically installed and are no longer required:
  evolution-common libsdl1.2debian libsdl1.2debian-alsa libarchive1
  libvorbisfile3 sqlite libexchange-storage1.2-3 gnome-cards-data
  libgtksourceview1.0-0 dvd+rw-tools libpt-1.10.10-plugins-alsa libggzmod4
  libxml-twig-perl libsqlite0 libgtkhtml3.16-cil libedata-cal1.2-6
  libpt-1.10.10 nautilus-data libmono-cairo2.0-cil system-tools-backends
  gtkhtml3.14 libeel2-data libdirectfb-1.0-0 guile-1.6-libs libdmx1
  libnet-dbus-perl libcdio-cdda0 gdm python-uno libegroupwise1.2-13
  libflickrnet2.1.5-cil libggz2 libgdata1.2-1 libgtksourceview-common
  libmono-sqlite2.0-cil libao2 libqthreads-12 gnome-games-data
  libgdata-google1.2-1 libwps-0.1-1 libopal-2.2 cdrdao liblpint-bonobo0
  libcdio-paranoia0 libeel2-2 liboobs-1-4 libggzcore9 gnome-system-tools gvfs
  gvfs-backends sqlite3 gnome-applets-data libguile-ltdl-1 libmng1
  libgtkhtml3.14-19
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
blankee@ubufile:~$ 

Still can't right click on my desktop.

---

### Post by bobnutfield on 2008-09-09
Try either rebooting or typing Ctrl+Alt+Bckspce to restart X.

---

### Post by Yannick Le Saint kyncani on 2008-09-09
Hi Eriks_Knor,

You can go to a console with ctrl+alt+f1, login, then "sudo apt-get install ubuntu-desktop". That should take care of most of the packages you've accidentally removed.

Cheers.

---

### Post by skillllllz on 2008-09-09
Try "sudo apt-get install ubuntu-desktop"
Installing the "ubuntu-desktop" meta package should automatically install all of the other needed packages which are currently missing.

---

### Post by skillllllz on 2008-09-09
Beat me to it :)

Oh well, great minds think alike!

> **Yannick Le Saint kyncani said:**
> Hi Eriks_Knor,

You can go to a console with ctrl+alt+f1, login, then "sudo apt-get install ubuntu-desktop". That should take care of most fo the packages you've accidentally removed.

Cheese.

---

### Post by Eriks_Knor on 2008-09-09
> **skillllllz said:**
> Beat me to it :)

Oh well, great minds think alike!

And that fixed it!

Thanks everybody! These Forums are the best!

---

### Post by Avionix on 2008-10-27
I had the same problem, I used the create launcher option above and gave myself a terminal. After many attempts at re-installing ubuntu desktop among other things I eventually typed gnome-panel in the terminal and...problem solved.Thanks to all above for their suggestions, I'm learning more all the time.

:)

---

