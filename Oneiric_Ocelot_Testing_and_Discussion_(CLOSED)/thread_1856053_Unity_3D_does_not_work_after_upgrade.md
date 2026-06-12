---
title: "Unity 3D does not work after upgrade"
date: 2011-10-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by koma77 on 2011-10-07
I upgraded from 11.04 to 11.10, and when I log in using unity 3D I just get a desktop background with icons. No dashboard or anything else.

If I create a new user I can log in to unity 3D.

I guess this means that there is a problem with upgrading from 11.04 to 11.10 with respect to unity configuration files...

I don't know where this bug should be reported?

Does anyone know what to try? I don't want to delete my upgraded user...

---

### Post by effenberg0x0 on 2011-10-07
Switch too a VT (Ctrl+Alt+F1 to F6) and run
unity --reset
sudo service lightdm stop
sudo service lightdm start

If that is not enough, after loggins in swutch again to a VT and run
DISPLAY=:0.0 /usr/bin/ccsm
Switch back with Ctrl+Alt+F7 and activate the Unity Plugin in ccsm.

Regards,
Effenberg

---

### Post by koma77 on 2011-10-07
Thanks for the advice!

It did not work, but I got some interesting results, I think.

When running the "unity --reset" command in a virtual console the unity segfaults!

Before it hits the segmentation fault it says:

```
compiz (unity) - Warn: unsupported internal format
```

This is what is printed to stderr:

```
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing resize options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing scale options...done
Initializing session options...done
unity-panel-service: ingen process hittades
Initializing unityshell options...done
Initializing addhelper options...done
Initializing animationaddon options...done
Initializing annotate options...done
Initializing bench options...done
Initializing blur options...done
Initializing clone options...done
Initializing colorfilter options...done
Initializing commands options...done
Initializing crashhandler options...done
Initializing cube options...done
Initializing cubeaddon options...done
Initializing debugspew options...done
Initializing extrawm options...done
Initializing fadedesktop options...done
Initializing firepaint options...done
Initializing group options...done
Initializing imgjpeg options...done
Initializing kdecompat options...done
Initializing loginout options...done
Initializing mag options...done
Initializing maximumize options...done
Initializing mblur options...done
Initializing neg options...done
Initializing notification options...done
Initializing obs options...done
Initializing opacify options...done
Initializing put options...done
Initializing reflex options...done
Initializing resizeinfo options...done
Initializing ring options...done
Initializing rotate options...done
Initializing scaleaddon options...done
Initializing scalefilter options...done
Initializing screenshot options...done
Initializing shelf options...done
Initializing shift options...done
Initializing showdesktop options...done
Initializing showmouse options...done
Initializing splash options...done
Initializing staticswitcher options...done
Initializing switcher options...done
Initializing td options...done
Initializing thumbnail options...done
Initializing trailfocus options...done
Initializing wallpaper options...done
Initializing water options...done
Initializing widget options...done
Initializing winrules options...done
Initializing wobbly options...done
Initializing zoom options...done
compiz (unity) - Warn: unsupported internal format
Segmentation fault (core dumped)
```

---

### Post by effenberg0x0 on 2011-10-07
You can reinstall unity and compiz, which will probably fix everything anyway. 

At a VT (Ctrl+Alt+F1 to F6):
```

sudo service lightdm stop 
sudo service gdm stop 
sudo killall -s KILL /usr/bin/X 
sudo apt-get remove --purge gdm gdm-guest-session 
sudo apt-get update 
sudo apt-get install --reinstall unity unity-2d-spread unity-lens-files unity-scope-musicstores unity-2d unity-asset-pool unity-lens-gwibber unity-services unity-2d-launcher unity-common unity-lens-music unity-2d-panel unity-greeter unity-place-applications unity-2d-places unity-lens-applications unity-place-files compiz compiz-dev compiz-kde compiz-plugins-main-default compizconfig-backend-gconf compiz-fusion-bcop compiz-plugins compiz-plugins-main-dev compizconfig-backend-kconfig compiz-fusion-plugins-extra compiz-plugins-default compizconfig-settings-manager compiz-fusion-plugins-main compiz-plugins-extra compiz-core compiz-gnome compiz-plugins-main lightdm lightdm-gtk-greeter lightdm-qt-greeter 
sudo mv ~/.Xauthority ~/.Xauthority.backup
sudo apt-get upgrade
sudo service lightdm start

```Then if you still get nothing at the desktop, try the commands I suggested before.

Regards,
Effenberg

---

### Post by koma77 on 2011-10-07
I ran all the commands you suggested, but still the same result.

So I tried to run the commands from comment #2.

I got the compiz config settings manager on my desktop, and I activated the unity plugin (which was not activated).

Even so, the problem persists...

A strange thing is that if I run "unity --reset" from Unity 2D I get both Unity 2D and Unity 3D at the same time.

I wonder what it is that makes unity (or compiz) segfault? 
I'm afraid that many more people will get similar segfaults when 11.10 is out.
I have not fiddled with unity in 11.04 so the config settings should not be exotic enough to produce segfaults...

Is there some way that I can remove all the compiz-related settings? And get the default ones for unity?

---

### Post by effenberg0x0 on 2011-10-07
```
DISPLAY=:0.0 /usr/bin/ccsm
Switch back with Ctrl+Alt+F7 and activate the Unity Plugin in ccsm.
```Great, so you can Login to Unity 3D and you could open ccsm using the command I posted above. Now, when you setup ccsm, you gotta make sure that the following plugins are activated: Unity Plugin, Composite, OpenGL. ccsm may crash while you're starting / stopping plugins. It is really unstable. In this case, switch back to the VT and launch it again with the DISPLAY command above.

Once you have ccsm options set, switch to the VT once more and run 
```
sudo service lightdm stop
sudo service lightdm start 
```You *should* have fixed your desktop but the truth is that you might have to start/stop lightdm a couple times before you can see the Unity bar and panel. Or at least that's what I am seeing in a couple test PCs here.

Now, if your Ubuntu 2D session is running OK and the 3D one simply won't run, I have to wonder if your current setup allows you to run an accelerated desktop (OpenGL). You can test it like this:

Login to Ubuntu 3D session
Switch to any VT and run:

[HTML]/usr/lib/nux/unity_support_test -p
[/HTML]If you get a yes to everything, your PC supports it. Otherwise, let us know in which item you get a NO.

Also, in this same VT, run

```
DISPLAY=:0.0 /usr/bin/glxgears
```Do you see any error in the VT? If you switch to the Ubuntu 3D desktop (Ctrl+Alt+F7), do you see GlxGears running?

Regards,
Effenberg

---

### Post by effenberg0x0 on 2011-10-07
> **koma77 said:**
> Is there some way that I can remove all the compiz-related settings? And get the default ones for unity?

Yes, using unity --reset, which I believe you already ran a couple times. Also, the long command I posted to you a few posts above reinstalled compiz packages to defaults. Which is why I am wondering if your PC setup (specially the video driver) supports OpenGL.

Regards,
Effenberg

**EDIT: **Looking at Unity source code, the error message you mentioned (unsupported format) refers to lack of GLX support. If you Video Card does support OpenGL, we must investigate why it is not working to its specs. A driver reinstall would be a good idea.
```

switch (status)
GL_FRAMEBUFFER_UNSUPPORTED:
compLogMessage ("unity", CompLogLevelWarn, "unsupported internal format");
```

**EDIT 2:** An idea: Run ccsm and click on the Composite plugin. Uncheck the "Unredirect Fullscreen Windows" checkbox. Exit, restart your session. This option may conflict with your Card+Driver capabilities.

---

### Post by koma77 on 2011-10-07
> ```
DISPLAY=:0.0 /usr/bin/ccsm
Switch back with Ctrl+Alt+F7 and activate the Unity Plugin in ccsm.
```Great, so you can Login to Unity 3D and you could open ccsm using the command I posted above. Now, when you setup ccsm, you gotta make sure that the following plugins are activated: Unity Plugin, Composite, OpenGL. ccsm may crash while you're starting / stopping plugins. It is really unstable. In this case, switch back to the VT and launch it again with the DISPLAY command above.


I can verify that the three plugins are activated in ccsm.

> 
Once you have ccsm options set, switch to the VT once more and run 
```
sudo service lightdm stop
sudo service lightdm start 
```You *should* have fixed your desktop but the truth is that you might have to start/stop lightdm a couple times before you can see the Unity bar and panel. Or at least that's what I am seeing in a couple test PCs here.


Still no luck...

> 
Now, if your Ubuntu 2D session is running OK and the 3D one simply won't run, I have to wonder if your current setup allows you to run an accelerated desktop (OpenGL). You can test it like this:

Login to Ubuntu 3D session
Switch to any VT and run:

[HTML]/usr/lib/nux/unity_support_test -p
[/HTML]If you get a yes to everything, your PC supports it. Otherwise, let us know in which item you get a NO.


Everything says yes. (I have a quite common nVidia card that is not too old.)

> 
Also, in this same VT, run

```
DISPLAY=:0.0 /usr/bin/glxgears
```Do you see any error in the VT? If you switch to the Ubuntu 3D desktop (Ctrl+Alt+F7), do you see GlxGears running?

Regards,
Effenberg


I get spinning gears on the desktop and no error messages in the console.
Frame rate is several thousands FPS.


You also mentioned that the configuration files should be reset when "unity --reset" is run.

The problem is that "unity --reset" itself segfaults, probably before it has resetted anything... That way I'm stuck with bad config files that prevent this whole thing from working.

[B]Also, importantly: If I create a new user and log in to a "Unity 3D" desktop everything works. 
[/B]

So, to me it seems that there is a bug in the way unity (or something) parses setting files/registry stuff (or something).

And I ran that apt-get remove + apt-get purge thing as well, but still no luck.

Is there a simple way to get a core file from the segfault and take a look at what it says?

---

### Post by koma77 on 2011-10-07
> **effenberg0x0 said:**
> **EDIT: **Looking at Unity source code, the error message you mentioned (unsupported format) refers to lack of GLX support. If you Video Card does support OpenGL, we must investigate why it is not working to its specs. A driver reinstall would be a good idea.
```

switch (status)
GL_FRAMEBUFFER_UNSUPPORTED:
compLogMessage ("unity", CompLogLevelWarn, "unsupported internal format");
```

**EDIT 2:** An idea: Run ccsm and click on the Composite plugin. Uncheck the "Unredirect Fullscreen Windows" checkbox. Exit, restart your session. This option may conflict with your Card+Driver capabilities.


I have reinstalled the driver a couple of times (using the "Hardware Driver" dialog).

In ccsm/composite the "Unredirect Fullscreen Windows" was already unchecked. I checked it, but it did not help. So I unchecked it again.

Since the 3D unity seems to work flawlessly for a newly created user I don't think that my hardware is to blame.

---

### Post by effenberg0x0 on 2011-10-07
I see... New test:

sudo service lightdm stop
sudo gconftool-2 --recursive-unset /apps/compiz
sudo gconftool-2 --recursive-unset /apps/compiz-1
sudo gconftool-2 --recursive-unset /apps/compizconfig-1
sudo unity --reset
sudo service lightdm start

Regards,
Effenberg

---

### Post by koma77 on 2011-10-07
> **effenberg0x0 said:**
> I see... New test:

sudo service lightdm stop
sudo gconftool-2 --recursive-unset /apps/compiz
sudo gconftool-2 --recursive-unset /apps/compiz-1
sudo gconftool-2 --recursive-unset /apps/compizconfig-1
sudo unity --reset
sudo service lightdm start

Regards,
Effenberg


I tried the above mentioned things (with the gconf and unity parts run both with and without sudo) but still the same result.

The difference being that when running "sudo unity --reset" I now get:

```
Traceback (most recent call last):
  File "/usr/bin/unity", line 213, in <module>
    reset_unity_compiz_profile ()
  File "/usr/bin/unity", line 84, in reset_unity_compiz_profile
    except (GError, AttributeError), e:
NameError: global name 'GError' is not defined

```

and no segfault.

Maybe I can try to reinstall those packages again now?

By the way: thanks for trying to help me! Really appreciate it!

---

### Post by effenberg0x0 on 2011-10-07
I am really curious about the problem you're facing. It's not something I have seen here so far. We tried a lot of things that usually solve the problem. We'll certainly learn something new when we find out whats going on there.

We have not looked at your video card driver. You mention its a NVidia. What model and which driver are you using (nvidia-current, from Ubuntu repos, proprietary from Nvidia website, OpenSource Community Driver (Nouveau)?

Regards,
Effenberg

---

### Post by koma77 on 2011-10-07
I have a nVidia Corporation GT200 [GeForce GTX 260] (rev a1) card and I'm using nVidias proprietary drivers from the official Ubuntu reops. (That "Hardware Drivers" thingy).

According to the nVidia X Server Settings panel I'm running version 280.13.

The segfault when doing "unity --reset" is back. It was me forgetting to run it whilst running (the crippled) Unity 3D...


I took the liberty to run strace on the "unity --reset" command to see if I could get any wiser as to why it segfaults.

It's difficult to say if really has something to do with this, but it seems like unity is loading svg-files when the SIGSEGV happens:

```
[pid 25401] sched_yield()               = 0
[pid 25401] lstat("/usr/share/icons/Humanity/places/48/user-trash.svg", {st_mode=S_IFREG|0644, st_size=31961, ...}) = 0
[pid 25401] open("/usr/share/icons/Humanity/places/48/user-trash.svg", O_RDONLY) = 22
[pid 25401] fstat(22, {st_mode=S_IFREG|0644, st_size=31961, ...}) = 0
[pid 25401] read(22, "<?xml version=\"1.0\" encoding=\"UT"..., 65536) = 31961
[pid 25401] read(22, "", 65536)         = 0
[pid 25401] close(22)                   = 0
[pid 25401] sched_yield()               = 0
[pid 25401] --- SIGSEGV (Segmentation fault) @ 0 (0) ---
```

Just to make sure, I opened the svg file in Eye of Gnome, and it looks ok. So possibly just a red herring.

I'm going to be away from the computer for 2 hours or so, but I'll gladly test any ideas when I get back!

---

### Post by effenberg0x0 on 2011-10-07
Could it be some sort of error related to the icon set? Maybe not finding an icon, a corrupted SVG or wrong permissions in the icon svg file?
Well, that would be absolutely new to me (and ridiculous) but.... lets look at it.

sudo apt-get install --reinstall human-icon-theme humanity-icon-theme human-netbook human-theme.

sudo ls -lha /usr/share/icons/Humanity/places/48 (paste results here).

This a long shot. I doubt it can be the culprit but we have to check it.

Regards,
Effenberg

---

### Post by techvish81 on 2011-10-07
> **koma77 said:**
> I tried the above mentioned things (with the gconf and unity parts run both with and without sudo) but still the same result.

The difference being that when running "sudo unity --reset" I now get:

```
Traceback (most recent call last):
  File "/usr/bin/unity", line 213, in <module>
    reset_unity_compiz_profile ()
  File "/usr/bin/unity", line 84, in reset_unity_compiz_profile
    except (GError, AttributeError), e:
NameError: global name 'GError' is not defined

```

and no segfault.

Maybe I can try to reinstall those packages again now?

By the way: thanks for trying to help me! Really appreciate it!
i had the same problem which is now solved.
what i did was ..
1)log out using ctrl+alt+del, select unity2d and login
2)install ccsm (compiz config settings manager) from software centre.
3)open it and scroll down till u have unity plugin checkbox, uncheck and then recheck it(if it is already unchecked just check it). it will ask to resolve conflicts, click on resolve conflict button and u may get 2-3 conflicts, select the middle button in all the conflicts, and now u will have everything working..

u may have to restart your system in between using terminal 'sudo reboot'. but don't panic it will be ok.

---

### Post by effenberg0x0 on 2011-10-07
> **techvish81 said:**
> i had the same problem which is now solved.
what i did was ..
1)log out using ctrl+alt+del, select unity2d and login
2)install ccsm (compiz config settings manager) from software centre.
3)open it and scroll down till u have unity plugin checkbox, uncheck and then recheck it(if it is already unchecked just check it). it will ask to resolve conflicts, click on resolve conflict button and u may get 2-3 conflicts, select the middle button in all the conflicts, and now u will have everything working..

u may have to restart your system in between using terminal 'sudo reboot'. but don't panic it will be ok.

Hopefully you're right. I'm out of ideas on how to help the OP.

Regards,
Effenberg

---

### Post by koma77 on 2011-10-07
I tried to reinstall the human icon sets.

This is what it looks like:

```

sudo ls -lha /usr/share/icons/Humanity/places/48
totalt 392K
drwxr-xr-x 2 root root  20K 2011-10-07 23:05 .
drwxr-xr-x 9 root root 4,0K 2010-04-16 20:38 ..
lrwxrwxrwx 1 root root   23 2011-08-25 23:27 application-x-gnome-saved-search.svg -> folder-saved-search.svg
-rw-r--r-- 1 root root 4,1K 2011-08-25 23:37 bookmark-missing.svg
lrwxrwxrwx 1 root root   16 2011-08-25 23:27 desktop.svg -> user-desktop.svg
lrwxrwxrwx 1 root root   14 2011-08-25 23:27 distributor-logo.svg -> start-here.svg
lrwxrwxrwx 1 root root   19 2011-08-25 23:27 edittrash.svg -> user-trash-full.svg
lrwxrwxrwx 1 root root   14 2011-08-25 23:27 emptytrash.svg -> user-trash.svg
-rw-r--r-- 1 root root  11K 2011-08-25 23:37 folder-documents.svg
lrwxrwxrwx 1 root root   19 2011-08-25 23:27 folder-downloads.svg -> folder-download.svg
lrwxrwxrwx 1 root root   19 2011-08-25 23:27 folder_download.svg -> folder-download.svg
-rw-r--r-- 1 root root 6,6K 2011-08-25 23:36 folder-download.svg
lrwxrwxrwx 1 root root   13 2011-08-25 23:27 folder_home.svg -> user-home.svg
lrwxrwxrwx 1 root root   13 2011-08-25 23:27 folder-home.svg -> user-home.svg
-rw-r--r-- 1 root root   57 2011-08-25 22:55 folder.icon
lrwxrwxrwx 1 root root   19 2011-08-25 23:27 folder_images.svg -> folder-pictures.svg
lrwxrwxrwx 1 root root   19 2011-08-25 23:27 folder-images.svg -> folder-pictures.svg
-rw-r--r-- 1 root root 9,3K 2011-08-25 23:36 folder-music.svg
lrwxrwxrwx 1 root root   19 2011-08-25 23:27 folder-open.svg -> folder-visiting.svg
lrwxrwxrwx 1 root root   19 2011-08-25 23:27 folder_pictures.svg -> folder-pictures.svg
-rw-r--r-- 1 root root 9,1K 2011-08-25 23:36 folder-pictures.svg
-rw-r--r-- 1 root root 9,9K 2011-08-25 23:36 folder-publicshare.svg
-rw-r--r-- 1 root root 7,1K 2011-08-25 23:37 folder-recent.svg
lrwxrwxrwx 1 root root   11 2011-08-25 23:27 folder-remote-ftp.icon -> folder.icon
lrwxrwxrwx 1 root root   17 2011-08-25 23:27 folder-remote-ftp.svg -> folder-remote.svg
lrwxrwxrwx 1 root root   11 2011-08-25 23:27 folder-remote.icon -> folder.icon
lrwxrwxrwx 1 root root   11 2011-08-25 23:27 folder-remote-nfs.icon -> folder.icon
lrwxrwxrwx 1 root root   17 2011-08-25 23:27 folder-remote-nfs.svg -> folder-remote.svg
lrwxrwxrwx 1 root root   11 2011-08-25 23:27 folder-remote-smb.icon -> folder.icon
lrwxrwxrwx 1 root root   17 2011-08-25 23:27 folder-remote-smb.svg -> folder-remote.svg
lrwxrwxrwx 1 root root   11 2011-08-25 23:27 folder-remote-ssh.icon -> folder.icon
lrwxrwxrwx 1 root root   17 2011-08-25 23:27 folder-remote-ssh.svg -> folder-remote.svg
-rw-r--r-- 1 root root  19K 2011-08-25 23:37 folder-remote.svg
-rw-r--r-- 1 root root 9,9K 2011-08-25 23:36 folder-saved-search.svg
-rw-r--r-- 1 root root 5,5K 2011-08-25 23:37 folder.svg
-rw-r--r-- 1 root root 8,0K 2011-08-25 23:37 folder-system.svg
-rw-r--r-- 1 root root  12K 2011-08-25 23:37 folder-templates.svg
-rw-r--r-- 1 root root 8,3K 2011-08-25 23:37 folder-ubuntu.svg
lrwxrwxrwx 1 root root   16 2011-08-25 23:27 folder-videos.svg -> folder-video.svg
-rw-r--r-- 1 root root  11K 2011-08-25 23:36 folder-video.svg
-rw-r--r-- 1 root root 5,7K 2011-08-25 23:36 folder-visiting.svg
lrwxrwxrwx 1 root root   16 2011-08-25 23:27 gnome-ccdesktop.svg -> user-desktop.svg
lrwxrwxrwx 1 root root   16 2011-08-25 23:27 gnome-desktop-config.svg -> user-desktop.svg
lrwxrwxrwx 1 root root   11 2011-08-25 23:27 gnome-folder.icon -> folder.icon
lrwxrwxrwx 1 root root   10 2011-08-25 23:27 gnome-folder.svg -> folder.svg
lrwxrwxrwx 1 root root   11 2011-08-25 23:27 gnome-fs-blockdev.icon -> folder.icon
lrwxrwxrwx 1 root root   17 2011-08-25 23:27 gnome-fs-blockdev.svg -> folder-remote.svg
lrwxrwxrwx 1 root root   20 2011-08-25 23:27 gnome-fs-bookmark-missing.svg -> bookmark-missing.svg
lrwxrwxrwx 1 root root   16 2011-08-25 23:27 gnome-fs-dav.svg -> gnome-fs-web.svg
lrwxrwxrwx 1 root root   16 2011-08-25 23:27 gnome-fs-desktop.svg -> user-desktop.svg
-rw-r--r-- 1 root root 5,5K 2011-08-25 23:36 gnome-fs-directory-accept.svg
lrwxrwxrwx 1 root root   11 2011-08-25 23:27 gnome-fs-directory.icon -> folder.icon
lrwxrwxrwx 1 root root   10 2011-08-25 23:27 gnome-fs-directory.svg -> folder.svg
lrwxrwxrwx 1 root root   11 2011-08-25 23:27 gnome-fs-ftp.icon -> folder.icon
lrwxrwxrwx 1 root root   17 2011-08-25 23:27 gnome-fs-ftp.svg -> folder-remote.svg
lrwxrwxrwx 1 root root   13 2011-08-25 23:27 gnome-fs-home.svg -> user-home.svg
lrwxrwxrwx 1 root root   33 2011-08-25 23:27 gnome-fs-loading-icon.svg -> ../../status/48/image-loading.svg
lrwxrwxrwx 1 root root   11 2011-08-25 23:27 gnome-fs-network.icon -> folder.icon
lrwxrwxrwx 1 root root   17 2011-08-25 23:27 gnome-fs-network.svg -> folder-remote.svg
lrwxrwxrwx 1 root root   11 2011-08-25 23:27 gnome-fs-nfs.icon -> folder.icon
lrwxrwxrwx 1 root root   17 2011-08-25 23:27 gnome-fs-nfs.svg -> folder-remote.svg
lrwxrwxrwx 1 root root   18 2011-08-25 23:27 gnome-fs-server.svg -> network-server.svg
lrwxrwxrwx 1 root root   11 2011-08-25 23:27 gnome-fs-share.icon -> folder.icon
lrwxrwxrwx 1 root root   17 2011-08-25 23:27 gnome-fs-share.svg -> folder-remote.svg
lrwxrwxrwx 1 root root   11 2011-08-25 23:27 gnome-fs-smb.icon -> folder.icon
lrwxrwxrwx 1 root root   17 2011-08-25 23:27 gnome-fs-smb.svg -> folder-remote.svg
lrwxrwxrwx 1 root root   11 2011-08-25 23:27 gnome-fs-ssh.icon -> folder.icon
lrwxrwxrwx 1 root root   17 2011-08-25 23:27 gnome-fs-ssh.svg -> folder-remote.svg
lrwxrwxrwx 1 root root   19 2011-08-25 23:27 gnome-fs-trash-empty-accept.svg -> user-trash-full.svg
lrwxrwxrwx 1 root root   14 2011-08-25 23:27 gnome-fs-trash-empty.svg -> user-trash.svg
lrwxrwxrwx 1 root root   19 2011-08-25 23:27 gnome-fs-trash-full.svg -> user-trash-full.svg
-rw-r--r-- 1 root root  12K 2011-08-25 23:37 gnome-fs-web.svg
lrwxrwxrwx 1 root root   13 2011-08-25 23:27 gnome-home.svg -> user-home.svg
lrwxrwxrwx 1 root root   14 2011-08-25 23:27 gnome-main-menu.svg -> start-here.svg
lrwxrwxrwx 1 root root   18 2011-08-25 23:27 gnome-mime-x-directory-nfs-server.svg -> network-server.svg
lrwxrwxrwx 1 root root   18 2011-08-25 23:27 gnome-mime-x-directory-smb-server.svg -> network-server.svg
lrwxrwxrwx 1 root root   11 2011-08-25 23:27 gnome-mime-x-directory-smb-share.icon -> folder.icon
lrwxrwxrwx 1 root root   17 2011-08-25 23:27 gnome-mime-x-directory-smb-share.svg -> folder-remote.svg
lrwxrwxrwx 1 root root   11 2011-08-25 23:27 gnome-mime-x-directory-smb-workgroup.icon -> folder.icon
lrwxrwxrwx 1 root root   17 2011-08-25 23:27 gnome-mime-x-directory-smb-workgroup.svg -> folder-remote.svg
lrwxrwxrwx 1 root root   19 2011-08-25 23:27 gnome-stock-trash-full.svg -> user-trash-full.svg
lrwxrwxrwx 1 root root   14 2011-08-25 23:27 gnome-stock-trash.svg -> user-trash.svg
lrwxrwxrwx 1 root root   11 2011-08-25 23:27 gtk-directory.icon -> folder.icon
lrwxrwxrwx 1 root root   10 2011-08-25 23:27 gtk-directory.svg -> folder.svg
lrwxrwxrwx 1 root root   11 2011-08-25 23:27 gtk-network.icon -> folder.icon
lrwxrwxrwx 1 root root   17 2011-08-25 23:27 gtk-network.svg -> folder-remote.svg
lrwxrwxrwx 1 root root   11 2011-08-25 23:27 inode-directory.icon -> folder.icon
lrwxrwxrwx 1 root root   10 2011-08-25 23:27 inode-directory.svg -> folder.svg
lrwxrwxrwx 1 root root   11 2011-08-25 23:27 neat.icon -> folder.icon
lrwxrwxrwx 1 root root   11 2011-08-25 23:27 network.icon -> folder.icon
lrwxrwxrwx 1 root root   11 2011-08-25 23:27 network_local.icon -> folder.icon
lrwxrwxrwx 1 root root   17 2011-08-25 23:27 network_local.svg -> folder-remote.svg
-rw-r--r-- 1 root root  15K 2011-08-25 23:36 network-server.svg
lrwxrwxrwx 1 root root   17 2011-08-25 23:27 network.svg -> folder-remote.svg
lrwxrwxrwx 1 root root   11 2011-08-25 23:27 network-workgroup.icon -> folder.icon
lrwxrwxrwx 1 root root   17 2011-08-25 23:27 network-workgroup.svg -> folder-remote.svg
lrwxrwxrwx 1 root root   14 2011-08-25 23:27 novell-button.svg -> start-here.svg
lrwxrwxrwx 1 root root   16 2011-08-25 23:27 other-desktop.svg -> user-desktop.svg
lrwxrwxrwx 1 root root   18 2011-08-25 23:27 redhat-network-server.svg -> network-server.svg
lrwxrwxrwx 1 root root   11 2011-08-25 23:27 redhat-system-group.icon -> folder.icon
lrwxrwxrwx 1 root root   18 2011-08-25 23:27 server.svg -> network-server.svg
-rw-r--r-- 1 root root 9,7K 2011-08-25 23:37 start-here.svg
lrwxrwxrwx 1 root root   11 2011-08-25 23:27 stock_folder.icon -> folder.icon
lrwxrwxrwx 1 root root   10 2011-08-25 23:27 stock_folder.svg -> folder.svg
-rw-r--r-- 1 root root  20K 2011-08-25 23:36 stock_music-library.svg
lrwxrwxrwx 1 root root   39 2011-08-25 23:27 stock_playlist.svg -> ../../mimes/48/audio-x-mp3-playlist.svg
lrwxrwxrwx 1 root root   11 2011-08-25 23:27 stock_shared-by-me.icon -> folder.icon
lrwxrwxrwx 1 root root   11 2011-08-25 23:27 stock_shared-to-me.icon -> folder.icon
-rw-r--r-- 1 root root 7,8K 2011-08-25 23:36 stock_smart-playlist.svg
lrwxrwxrwx 1 root root   19 2011-08-25 23:27 stock_trash_full.svg -> user-trash-full.svg
lrwxrwxrwx 1 root root   14 2011-08-25 23:27 trashcan_empty.svg -> user-trash.svg
lrwxrwxrwx 1 root root   19 2011-08-25 23:27 trashcan_full.svg -> user-trash-full.svg
lrwxrwxrwx 1 root root   43 2011-08-25 23:27 user-bookmarks.svg -> ../../actions/48/gnome-app-install-star.svg
-rw-r--r-- 1 root root 5,5K 2011-08-25 23:37 user-desktop.svg
-rw-r--r-- 1 root root 3,3K 2011-08-25 23:36 user-home.svg
lrwxrwxrwx 1 root root   19 2011-08-25 23:27 user-images.svg -> folder-pictures.svg
lrwxrwxrwx 1 root root   19 2011-08-25 23:27 user-pictures.svg -> folder-pictures.svg
lrwxrwxrwx 1 root root   11 2011-08-25 23:27 user-share.icon -> folder.icon
lrwxrwxrwx 1 root root   17 2011-08-25 23:27 user-share.svg -> folder-remote.svg
-rw-r--r-- 1 root root  74K 2011-08-25 22:55 user-trash-full.svg
-rw-r--r-- 1 root root  32K 2011-08-25 23:36 user-trash.svg
lrwxrwxrwx 1 root root   14 2011-08-25 23:27 xfce-trash_empty.svg -> user-trash.svg
lrwxrwxrwx 1 root root   19 2011-08-25 23:27 xfce-trash_full.svg -> user-trash-full.svg

```

I don't know if that tells you anything, but it did not help to reinstall the themes.

Toggling the checkbox in ccsm did not help eihter.

I believe that compiz is segfaulting also when the ccsm starts fiddling...

---

### Post by effenberg0x0 on 2011-10-07
I just wanted to see if you have the files, if the links are correct, etc. Its equal to mine.

I guess no luck with the suggestion on post #[**15**]("http://ubuntuforums.org/showpost.php?p=11319786&postcount=15") too? I got curious as to simply Deactivating / Activating Unity Plugin is CCSM using the 2D session could probably solve the problem, as the poster reported.

Regards,
Effenberg

---

### Post by effenberg0x0 on 2011-10-07
Ah, I missed one attempt actually.

sudo service lightdm stop
whoami (make sure you're logged in with the user who can't use the Ubuntu session)

sudo mv ~/.local ~/.local.old
sudo mv ~/.cache/compizconfig-1 ~/.cache/compizconfig-.old
sudo mv ~/.compiz-1 ~/.compiz-1.old
sudo mv ~/.config/compiz-1 ~/.config/compiz-1.old
sudo mv ~/.cache/unity ~/.cache/unity.old
sudo mv ~/.cache/zeitgeist ~/.cache/zeitgeist.old

sudo service lightdm start 
DISPLAY=:0.0 /usr/bin/ccsm &
Activate/deactivate Unity Plugin and close ccsm
sudo service lightdm restart

Regards,
Effenberg

---

### Post by koma77 on 2011-10-07
Comment # 15 did not solve the problem unfortunately.

And moving the configuration files did not work either. I thought that would do the trick since the 3D Unity works fine for a newly created user...

(And I verified that I was logged in as the correct user when I was moving files...)

Very strange problem...
You mentioned that you took a look in the source code of unity.
Where can I download that and have a look myself?

I'm off to get some sleep now, but I'll continue digging tomorrow...

Cheers!

---

### Post by effenberg0x0 on 2011-10-07
Hey,

You can get it at [https://code.launchpad.net/unity](https://code.launchpad.net/unity)
Have a look here too as you'll probably need to use bazar: [http://unity.ubuntu.com/getinvolved/#coding](http://unity.ubuntu.com/getinvolved/#coding)

I'll try to think of something that might help you. It's frustrating to try all of this and still fail.

Regards,
Effenberg

---

### Post by techvish81 on 2011-10-07
I did the steps before the update released after 12am. then after the unity 3d appeared normal I updated my system. while yours broke after update. 
I dont know what is this but there may be some conflicts in unity plugin and other ccsm settings which I resolved by chance..  ha ha ha.. I am not a geek but I think it is.something in  compiz not unity.

---

### Post by asampaleanu on 2011-10-08
Hi Effenberg,

Looks like the OP is having the same problem as I am with which you were trying to help in the other thread I started. I found this thread while searching for "nvidia-current" as I was thinking that the problem might be with my nvidia driver. 

With Natty, I was using the nvidia proprietary driver, 280.13 (same as the OP), but I seem to recall after the oneiric update that the additional drivers control panel was showing that nvidia-current was being used. I changed this to the proprietary ones 'nvidia-current-updates' and I thought that this is what caused things to fail after a reboot. Just looking at it now, though, I see in synaptic that nvidia-current and nvidia-current-updates seem to be pretty much the same (280.13-0ubuntu5 vs 280.13-0ubuntu4). I tried switching back to nvidia-current, but it didn't help in restoring the full Unity 3D UI.

If it matters, my video chipset is the Nvidia NVS 4200m.

Cheers

---

### Post by koma77 on 2011-10-08
Finally I was able to solve this tricky problem!

Here follows a somewhat confusing explanation of what I did and found out:

I started by focusing on the SEGFAULT that was being generated when I started unity. To get the segfault I would log into unity 3D, switch to a console and start unity from there. It didn't matter if I started unity with --reset or not. The result was still the same: segfault.

By using strace I could see that the last files opened by unity prior to the segfault was an icon.

By using gdb, via the --advanced-debugging option to unity, I could take a look at the backtrace at the point of the segfault.

The segfault happens inside the nVidia driver.

The last non-nVidia code that executed was RenderIcon (no surprise). From the printouts it is evident that the rendering of the very first icon (the trashcan) fails. 

This icon is properly rendered for a newly created user on my computer. For that user everything in unity 3d works. So the icon itself was not to blame.

But what could be the difference?

I think it is a combination of circumstances leading to unity sending bad stuff to the gfx-driver. The gfx-driver should however not segfault...

I then tried to start unity in a virtual terminal as usual. Immediately after starting unity (we're talking milliseconds here...) I switched to the X desktop. 

Unity started up nicely without any segfault!!!

It was 100% reproducible. I tested to start unity 10 times without the lightning fast switch to X (ctrl-alt-F7): segfault.
Then 10 times with the lightning fast switch: worked fine.

So, I believe there were a race condition between unity and something else.

I then cleared out some old stuff in my "startup programs" which I guess have been residing there for ages. It was stuff like color profiling for monitor, etc.

[B]I simply made the list of startup programs similar to that of a newly created user of the system.

Now it works all the time, directly from login![/B]


I can't explain why the lightning-fast switch works. (I used the correct DISPLAY setting etc...).

But it is obviously possible for a startup program to prevent unity from using the GL-rendering of the nVidia-driver.

If anyone wants me to do any tests to find out the real root cause I'll be happy to do so.

Big thanks to Effenberg for a lot of helpful information and ideas!!

---

