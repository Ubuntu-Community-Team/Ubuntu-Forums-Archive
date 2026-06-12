---
title: "Just updated to 11.10, No Launcher"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by Nutopia on 2011-10-16
Hi,

I just updated to 11.10. The Launcher is nowhere to be found. I have moused to the left, top left corner... no luck. I had to create an HTML file just to be able to open Firefox. Any idea how to get the launcher back?

Also, the top toolbar (with the clock and certain icons like sound, network) is gone. I have this 'File' toolbar now. Anyway to get the old one back, or at least to add icons and clock to it?

Also can't find the 'minimize' icon for any window when the window is in full screen. A shortcut to the desktop would be great, too.

Thanks.

---

### Post by philinux on 2011-10-16
> **Nutopia said:**
> Hi,

I just updated to 11.10. The Launcher is nowhere to be found. I have moused to the left, top left corner... no luck. I had to create an HTML file just to be able to open Firefox. Any idea how to get the launcher back?

Also, the top toolbar (with the clock and certain icons like sound, network) is gone. I have this 'File' toolbar now. Anyway to get the old one back, or at least to add icons and clock to it?

Also can't find the 'minimize' icon for any window when the window is in full screen. A shortcut to the desktop would be great, too.

Thanks.
Upgrades seem to be causing problems. Try this from a terminal. I think its ctrl alt t. 
Or alt f2 gnome-terminal

unity --reset

---

### Post by Nutopia on 2011-10-16
I ran the command, and I get the following. Also, the terminal window is now 'stuck' on my screen.

Initializing crashhandler options...done
Initializing obs options...done
Initializing imgjpeg options...done
Initializing clone options...done
Initializing loginout options...done
Initializing fadedesktop options...done
Initializing showmouse options...done
Removed 0 items from active_plugins
Overriding value alt_tab_timeout
Completed upgrade com.canonical.unity.unity.01.upgrade
Processing upgrade com.canonical.unity.unity.02.upgrade
profile: unity
number: 2
domain: com.canonical.unity
Overriding value x_offset
Overriding value y_offset
Overriding value distance
Overriding value vp_distance
Overriding value vp_brightness
Overriding value vp_saturation
Overriding value reflection
Completed upgrade com.canonical.unity.unity.02.upgrade
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libopengl.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'opengl'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libdecor.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'decor'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libcompiztoolbox.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'compiztoolbox'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libresize.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'resize'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libmove.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'move'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libanimation.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'animation'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunitymtgrabhandles.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'unitymtgrabhandles'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libgrid.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'grid'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libworkarounds.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'workarounds'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libexpo.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'expo'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libezoom.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'ezoom'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libwall.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'wall'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libfade.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'fade'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libscale.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'scale'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunityshell.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'unityshell'
Setting Update "audible_bell"
Setting Update "autoraise_delay"
Setting Update "maximize_window_key"
Setting Update "minimize_window_key"
Setting Update "show_desktop_key"
Setting Update "toggle_window_maximized_key"
Setting Update "toggle_window_shaded_key"
Setting Update "run_command_terminal_key"

---

### Post by philinux on 2011-10-16
I would go for a reboot now.

---

### Post by Nutopia on 2011-10-16
I rebooted - no change.

---

### Post by ianp5a on 2011-10-16
**Alt-Space** gets the maximise-minimise-restore menu.

I had the same problem after setting up my dual monitors.
I have now installed **classic gnome **and everything is back to the old way. *Hooray!*

---

### Post by Nutopia on 2011-10-16
I really liked the Unity Launcher - would be great to get it back. Any other ideas? 

I ran unity --reset again, and it just seems to hang on:
Setting Update "run_key"

Is that normal? How long should I wait for it before assuming it isn't working?

---

### Post by wildmanne39 on 2011-10-16
Hi, install compiz-settings-manager then click on it and enable the unity plugin if it is unchecked that happened to me and that is how I fixed it.
Thank you

---

### Post by Nutopia on 2011-10-16
I just did that. Does it require a restart, because the launcher still isn't here?

---

### Post by Nutopia on 2011-10-16
Well, just restarted. Still no Launcher. I guess I'll have to switch back to the gnome classic view. That's a bummer because I really liked the Launcher in 11.04, and now the upgrade to 11.10 just screwed it up.

Any other ideas I can try are very welcome.

---

### Post by wildmanne39 on 2011-10-16
Hi, it is possible that it is a problem with the upgrade, it is best to back up your data and do a clean install.
Thank you

---

### Post by Nutopia on 2011-10-16
Before I do that, does Google Chrome work in 11.10? It crashed immediately for me and a search shows this seems to be a problem for others out there. If I can't have Chrome working, I'm probably going to try to rollback to 11.04.

---

### Post by wildmanne39 on 2011-10-16
Hi, I do not know I only use firefox, but I imagine it will work even in 11.04 a lot of people had problems with it in the beginning.
Thank you

---

### Post by Nutopia on 2011-10-16
Ok, I have a backup running now. 

Since I haven't done a fresh install of Ubuntu for years, should I literally start at the beginning? Format my partition completely, install Ubuntu 11.10, restore the backup?

---

### Post by wildmanne39 on 2011-10-16
Hi, in the top right corner of the screen click on the icon that is for shutting down ubuntu and click on system settings and deja dub is listed there under backup.
Thank you

---

### Post by Nutopia on 2011-10-16
Thanks I have a backup running now.

Since I haven't done a fresh install of Ubuntu for years, should I literally start at the beginning? Format my partition completely, install Ubuntu 11.10, restore the backup?

---

### Post by wildmanne39 on 2011-10-16
Hi, that is what I would do otherwise it is going to install over the same bad configuration files and you will most likely have the same problem.
Thank you

---

### Post by zimitt on 2011-10-16
This is not a fix, but a work around. Ctr+alt+delete takes you to the log in screen, switch to "2D ubuntu" and the launcher will return, but returning to "ubuntu" returns the issue. At least you have the launcher and upper bar.

---

### Post by Gs Dewd on 2011-10-16
Yes I would do a complete reinstall and let it reset the partitions and all. Also I would be careful with restoring the backup you just made on top of your new install. You may wind up with the same problem again. You could just back up you packages and re-install them so you have all your previous programs and apps. Chrome does work with 11.10 as I am using it right now.

---

