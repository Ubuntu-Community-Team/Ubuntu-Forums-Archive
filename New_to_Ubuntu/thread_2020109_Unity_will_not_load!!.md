---
title: "Unity will not load!!"
date: 2012-07-07
forum: New to Ubuntu
---

### Post by smashthew on 2012-07-07
Okay, so I did all of the recent updates through the update manager yesterday, and rebooted... and now nothing loads, it's just my wallpaper really. I can open a terminal and run commands from there, but i do not have a unity dash at all..

When I try to run unity --reset, this is what I get:


matthew@matthew-FQ563AA-ABA-a6750f:~$ unity --reset
WARNING: Unity currently default profile, so switching to metacity while resetting the values
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x220026f

Initializing composite options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libopengl.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'opengl'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libcompiztoolbox.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'compiztoolbox'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libdecor.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'decor'
Initializing vpswitch options...done
Initializing snap options...done
Initializing mousepoll options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libresize.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'resize'
Initializing place options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libmove.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'move'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libwall.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'wall'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libgrid.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'grid'
Initializing session options...done
Initializing gnomecompat options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libanimation.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'animation'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libfade.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'fade'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunitymtgrabhandles.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'unitymtgrabhandles'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libworkarounds.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'workarounds'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libscale.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'scale'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libexpo.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'expo'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libezoom.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'ezoom'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunityshell.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'unityshell'
compiz (core) - Warn: unhandled ConfigureNotify on 0xc00093!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
Initializing animation options...done
Initializing annotate options...done
Initializing blur options...done
Initializing clone options...done
Initializing colorfilter options...done
Initializing commands options...done
Initializing resize options...done
Initializing move options...done
Initializing cube options...done
Initializing decor options...done
Initializing expo options...done
Initializing ezoom options...done
Initializing fade options...done
Initializing grid options...done
Initializing imgjpeg options...done
Initializing kdecompat options...done
Initializing mag options...done
Initializing neg options...done
Initializing obs options...done
Initializing opacify options...done
Initializing opengl options...done
Initializing put options...done
Initializing resizeinfo options...done
Initializing ring options...done
Initializing rotate options...done
Initializing scale options...done
Initializing scaleaddon options...done
Initializing screenshot options...done
Initializing shift options...done
Initializing staticswitcher options...done
Initializing switcher options...done
Initializing thumbnail options...done
Initializing unitymtgrabhandles options...done
Initializing unityshell options...done
Initializing wall options...done
Initializing water options...done
Initializing winrules options...done
Initializing wobbly options...done
Initializing workarounds options...done
Setting Update "main_menu_key"
Setting Update "run_key"


and it hangs there.


Any help? Thank you.

---

### Post by NikTh on 2012-07-08
Ok , as you can see probably its compiz problem. 
(3) Suggestions:

(1) ```
sudo apt-get install compizconfig-settings-manager
``` and open it with ```
ccsm
``` , check if "Unity plugin" its enabled . If its not then enable it. 

(2) You can try to delete any settings you have in compiz and generaly... with this command [COLOR=Red]everything[/COLOR] concerns [COLOR=Red]personal settings[/COLOR] will [COLOR=Red]delete [/COLOR][COLOR=Black]!! 
[/COLOR]```
rm -rf .compiz* .gconf* .config/dconf/ .config/compiz*
```and ```
sudo reboot
```(3)If nothing above fix the problem you can create a new user from Virtual terminal (Ctrl+alt+F2) with this commands
```
sudo service lightdm stop
sudo adduser newuser
sudo passwd newuser
sudo service lightdm start
```newuser = any name you want. 
Then try to login with new user account and promote him to administrator (from users account) . Copy all you personal files.. from old user to new **[COLOR=Red]except [/COLOR]**[COLOR=Black]config files and settings. [/COLOR]

---

### Post by smashthew on 2012-07-08
I did forget to mention that I'm using 12.04, if that matters.

I opened Compiz, Unity was not enabled, however enabling it did not cause it to start working, even after reboot.

I reset everything with the command you offered, but to no avail.

And also, adding a new user did not work either.

Where can I go from here?

Thank you for your help.

---

### Post by NikTh on 2012-07-08
> **smashthew said:**
> 

Where can I go from here?

Try to reinstall .. 
```
sudo apt-get install --reinstall ubuntu-mono ubuntu-minimal ubuntu-desktop unity unity-common unity-2d
```

---

### Post by Valezan on 2012-08-17
Hi Smashthew,
 Have you already solved your problem ?
 I'am also using Ubuntu 12.04 and I encountered the same one yesterday after updating and I have found a solution in this thread : [http://ubuntuforums.org/showthread.php?t=1859134](http://ubuntuforums.org/showthread.php?t=1859134)
 In my case, I have just reinstalled the ATI driver with Jockey.
 I hope it may help you.

---

