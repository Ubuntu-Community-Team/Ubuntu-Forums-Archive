---
title: "[SOLVED] Screenlets not starting after installation"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by belier on 2008-10-27
Hi.

I've just installed screenlets using synaptics. I've launched it, it appears on task bar for a while with the sand glass and then disappears. I've tried to install it again using sudo apt-get install screenlets* and it happens the same. I've read about screenlets on the forum but no succes,

Any idea?

Thanks in advance

---

### Post by NewJack on 2008-10-28
After installing Screenlets, did you restart X (Ctrl-Alt-Backspace then log back in)?  If so, then look in your Sessions>Startup tab  and make sure that Screenlets is set to run at startup.  If it isn't just add it manually.  That should do the trick.

If that doesn't, then I would say to run Screenlets from the Terminal by typing ```
screenlets
``` to see if you get any error messages.  Maybe you are missing a dependency somewhere along the way.

Good luck, hope that helped!

---

### Post by CatKiller on 2008-10-28
Don't forget that you need to actually add some screenlets for anything to appear. The easiest way to do this is with the Screenlets Manager which (on Gnome, at least) is in the Accessories menu. Select the screenlets that you'd like to run and tick the "Auto start on login" box for each one that you'd like to start automatically.

It's also possible to run each screenlet manually - they're individual Python programs.

Edit: The command for starting the Screenlets Manager, in case you can't find it on the menu, is **screenlets-manager**.

---

### Post by belier on 2008-10-28
Thanks for answering.

I can see the Screenlets launcher on my Preferences menu.
If I launch screenlets-manager from konsole it gives me next error:

```
Traceback (most recent call last):
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 1201, in <module>
    app = ScreenletsManager()
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 258, in __init__
    self.create_ui()
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 586, in create_ui
    w.set_icon_from_file('/usr/share/icons/screenlets.svg')
gobject.GError: Couldn't recognize the image file format for file '/usr/share/icons/screenlets.svg'

```

If I launch it from the command line of the menu it appears an screenlets tab on the taskbar with the sand glass for a while and then disappears.

Launching screenlets from konsole it says:

```
 bash: screenlets: command not found

```

---

### Post by CatKiller on 2008-10-28
I guess the error message for screenlets-manager explains why it doesn't launch from the menu. Which version are you using? I believe there is a newer version if you add the repository listed at [www.screenlets.org](www.screenlets.org), which I understand is the same version that is in the hardy-backports repository. Perhaps the newer version will launch properly for you.

EDIT: Just realised this was the Absolute Beginner Talk section. To add a new repository, you can use Synaptic. If you select Settings -> Repositories and click on the Third Party Software tab, you can use the Add.. button to put in the Screenlets.org repository, which is ```
deb http://ppa.launchpad.net/gilir/ubuntu hardy main universe
``` You could also do it manually by editing your sources.list by typing ```
sudo nano /etc/apt/sources.list
``` at the konsole and adding that line at the bottom.

---

### Post by belier on 2008-10-29
Thanks for helping and sorry for my late answer. I can only dedicate some time at night to the computer. I've done everything and I get same error... :confused:

---

### Post by CatKiller on 2008-10-30
> **belier said:**
> Thanks for helping and sorry for my late answer. I can only dedicate some time at night to the computer. I've done everything and I get same error... :confused:

So have you updated Screenlets to the latest version? Once you've added in the repository in Synaptic, you need to press the Reload button to get the package information from the new repository, and then you should get a list of packages that you can upgrade. Or you can press the Mark All Upgrades button.

Alternatively, if you manually edited your sources.list, you can do the same thing with ```
sudo aptitude update
sudo aptitude safe-upgrade
```

---

### Post by belier on 2008-10-30
Thanks for helping again.
Still having same error...

```
Traceback (most recent call last):
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 1308, in <module>
    app = ScreenletsManager()
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 95, in __init__
    self.create_ui()
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 305, in create_ui
    w.set_icon_from_file(screenlets.INSTALL_PREFIX +'/share/icons/screenlets.svg')
gobject.GError: Couldn't recognize the image file format for file '/usr/share/icons/screenlets.svg'

```

Any other way to load the screenlets without using screenlets?

---

### Post by CatKiller on 2008-10-30
> **belier said:**
> Any other way to load the screenlets without using screenlets?

If you mean without using the screenlets-manager, then yes.

Say you wanted to run the Wallpaper Clock screenlet, then you would run ```
/usr/share/screenlets/WallpaperClock/WallpaperClockScreenlet.py &
``` The & at the end means that the process will be run in the background and shouldn't close when you close the terminal that started the process. If you decide that you want this screenlet to run whenever you log in then you don't need the & when you put this command in the KDE equivalent of Sytem -> Preferences -> Sessions.

All of the screenlets are in /usr/share/screenlets. You can also run them from wherever you've downloaded them to if you find any you like on the Internet. I believe there are quite a few at screenlets.org.

---

### Post by belier on 2008-10-30
Did what you told me.

```
[1] 9362
xavier@CasaKubuntu:/usr/share/screenlets/WallpaperClock$ CachingBackend: Loading instances from cache
No Daemon, Launching Daemon
Traceback (most recent call last):
  File "/usr/share/screenlets/WallpaperClock/WallpaperClockScreenlet.py", line 607, in <module>
    screenlets.session.create_session(WallpaperClockScreenlet)
  File "/usr/lib/python2.5/site-packages/screenlets/session.py", line 471, in create_session
    session = ScreenletSession(classobj, backend_type=backend)
  File "/usr/lib/python2.5/site-packages/screenlets/session.py", line 105, in __init__
    self.connect_daemon()
  File "/usr/lib/python2.5/site-packages/screenlets/session.py", line 110, in connect_daemon
    bus = dbus.SessionBus()
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 217, in __new__
    mainloop=mainloop)
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 106, in __new__
    bus = BusConnection.__new__(subclass, bus_type, mainloop=mainloop)
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 125, in __new__
    bus = cls._new_for_bus(address_or_type, mainloop=mainloop)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ExecFailed: Failed to execute dbus-launch to autolaunch D-Bus session
no daemon yet
Traceback (most recent call last):
  File "/usr/share/screenlets-manager/screenlets-daemon.py", line 285, in <module>
    daemon = ScreenletsDaemon()
  File "/usr/share/screenlets-manager/screenlets-daemon.py", line 63, in __init__
    pixbuf = gtk.gdk.pixbuf_new_from_file("/usr/share/icons/screenlets.svg")
gobject.GError: Couldn't recognize the image file format for file '/usr/share/icons/screenlets.svg'

[1]+  Exit 1                  /usr/share/screenlets/WallpaperClock/WallpaperClockScreenlet.py

```

Why it can't be a bit easier...

---

### Post by CatKiller on 2008-10-30
> **belier said:**
> gobject.GError: Couldn't recognize the image file format for file '/usr/share/icons/screenlets.svg'

You had an error message about SVGs not being recognised before. I haven't used KDE, so I don't know how SVG support works in Kubuntu, I'm afraid. Hopefully someone else can chime in with that.

You've still not said which version of Screenlets you're using. I've not had any problems with the version I got from the screenlets.org repository, but I do seem to recall problems with the version in whichever standard repository was current when I started using Screenlets (I can't remember when that was, I'm afraid).

---

### Post by belier on 2008-10-30
I'll search what are the svg files. The version of screenlets that I have installed is 0.1.2.3~ppa.

---

### Post by belier on 2008-10-30
FINALLY!!!!!!!!!!!
Got it working.
I've found a thread on french forum.
[http://forum.ubuntu-fr.org/viewtopic.php?id=213780](http://forum.ubuntu-fr.org/viewtopic.php?id=213780)

I had to install **librsvg** and **dbus-x11**

Thanks for everything

---

