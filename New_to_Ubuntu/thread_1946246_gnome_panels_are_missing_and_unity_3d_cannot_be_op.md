---
title: "gnome panels are missing and unity 3d cannot be opened"
date: 2012-03-24
forum: New to Ubuntu
---

### Post by crave-n on 2012-03-24
hello,
i'm pretty new to ubuntu ,
lastly i installed intel graphics drivers using
```
$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 8844C542  $ sudo apt-get update  $ sudo apt-get dist-upgrade
```after restarting gnome i cant see the top panel and also the cairo-dock  ,while tryin to open unity 3d all i get after entering the password is  the same user selection screen.Also the startup time for loading the  gnome/unity 2d is very long. thanks for the help :razz:

---

### Post by collisionystm on 2012-03-24
FYI. That command is not installing intel drivers. Its just updating your ubuntu key and running an update.

The linux kernel is already packaged with the latest intel drivers. The newer the kernel, the newer the driver.

You need to load Unity 2D. Open a terminal and type, unity --replace 

let it run until it closes.

---

### Post by astrobob.tk on 2012-03-24
> **crave-n said:**
> hello,
i'm pretty new to ubuntu ,
lastly i installed intel graphics drivers using
```
$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 8844C542  $ sudo apt-get update  $ sudo apt-get dist-upgrade
```after restarting gnome i cant see the top panel and also the cairo-dock  ,while tryin to open unity 3d all i get after entering the password is  the same user selection screen.Also the startup time for loading the  gnome/unity 2d is very long. thanks for the help :razz:

I am not suer about Unity, but in gnome (10.04) I use the following command to restart the gnome panel:
```
killall gnome-panel
```

---

### Post by crave-n on 2012-03-25
after i run the unity -replace command i get
> Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
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
compiz (unityshell) - Error: GL_ARB_vertex_buffer_object not supported

Segmentation fault and all the title bars seem to be gone

---

### Post by crave-n on 2012-03-25
> **astrobob.tk said:**
> I am not suer about Unity, but in gnome (10.04) I use the following command to restart the gnome panel:
```
killall gnome-panel
```
i've tried running the killall code but it says that there is no program running in the name gnome-panel...

---

### Post by astrobob.tk on 2012-03-25
> **crave-n said:**
> i've tried running the killall code but it says that there is no program running in the name gnome-panel...

I guess it is logical since Unity replaces gnome. There's no point of using this option (my bad). Had you installed the gnome panel, it would have reset it.

Check this post if it might help: [http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html](http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html)

P.S.: I did not try the commands in this post & for safety, be extra careful (as outlined in the forums' Code of Conduct) when someone uses the remove command (rm) & super cow commands!

I advise that you wait some time for another reply confirming the *safety* of the above post.

---

### Post by collisionystm on 2012-03-25
there is not a gnome-panel in 11.10.

Try this.

Go into ubuntu 2d. Open software center. Remove Unity.

Re-Install unity.

Log off and try regular ubuntu.

---

### Post by crave-n on 2012-03-25
still ubuntu is not working all get is refreshed page with the same login screen...

---

### Post by astrobob.tk on 2012-03-26
> **crave-n said:**
> still ubuntu is not working all get is refreshed page with the same login screen...

I suggest you join unity's mailing list or irc channel ([http://unity.ubuntu.com/contact-us/](http://unity.ubuntu.com/contact-us/)) & ask them. Unity relatively new & most Ubuntuoers prefer the old gnome (at least I can talk of my self, though testing with Unuity!)

let us know if you get a solution

---

### Post by NikTh on 2012-03-26
Hello , 
it is really bizarre how from an installation of a keyserver , Unity disappeared. Maybe you did something else ? for example , used a janitor or something ?  or maybe the command "dist-upgrade" removed some packages. 
Open a terminal and try first 
```
unity --reset
``` if nothing happens then let us see the output of 
```
grep 'remove' /var/log/dpkg.log
```Thanks

---

### Post by crave-n on 2012-03-26
> 2012-03-02 21:59:55 startup packages remove
2012-03-02 21:59:56 remove mozilla-plugin-vlc 1.1.12-2~oneiric1 <none>
2012-03-02 22:00:03 startup packages remove
2012-03-02 22:00:03 remove libvlccore4 1.1.12-2~oneiric1 <none>
2012-03-03 13:53:04 startup packages remove
2012-03-03 13:53:08 remove wine1.2 1.2.3-0ubuntu1 <none>
2012-03-08 12:51:52 startup packages remove
2012-03-08 12:51:53 remove acm 5.0-27ubuntu2 <none>
2012-03-23 12:17:21 remove wine1.3 1.4-0ubuntu1~ppa1~oneiric1 <none>
2012-03-23 12:17:27 remove winetricks 0.0+20120308~ppa1 <none>
2012-03-23 12:26:45 remove wine1.3 1.4-0ubuntu1~ppa1~oneiric1 <none>
2012-03-23 12:26:51 remove winetricks 0.0+20120308~ppa1 <none>
2012-03-23 13:01:54 remove wine1.3 1.4-0ubuntu1~ppa1~oneiric1 <none>
2012-03-23 13:02:50 remove winetricks 0.0+20120308~ppa1 <none>
2012-03-23 13:12:39 remove wine1.2 1.2.3-0ubuntu1 <none>
2012-03-25 22:41:59 startup packages remove
2012-03-25 22:42:04 remove ubuntu-desktop 1.245 <none>
2012-03-25 22:42:05 remove unity 4.28.0-0ubuntu2 <none>
2012-03-25 22:55:45 startup packages remove
2012-03-25 22:55:47 remove unity 4.28.0-0ubuntu2 <none>
2012-03-25 22:55:48 remove compiz 1:0.9.6+bzr20110929-0ubuntu6.1 <none>
2012-03-25 23:01:27 remove xserver-xorg-video-all 1:7.6+7ubuntu7.1 <none>
2012-03-25 23:01:28 remove xserver-xorg-video-ati 1:6.14.99~git20110811.g93fc084-0ubuntu1 <none>
2012-03-25 23:01:29 remove xserver-xorg-video-radeon 1:6.14.99~git20110811.g93fc084-0ubuntu1 <none>
this is the output of 
grep 'remove' /var/log/dpkg.log

---

### Post by NikTh on 2012-03-26
Hello ,
try this  ```
sudo aptitude install ubuntu-desktop ubuntu-minimal ubuntu-standard xserver-xorg-video-all unity
```
then try to get in to unity 3D. 
Thanks

---

### Post by crave-n on 2012-03-28
sorry but the code didn't work still i cant login into gnome or unity 3d :(
thanks...

---

### Post by NikTh on 2012-03-28
Hello , 
The above code i gave you , did install any packages ? do you remember ? 
and also 
try these commands 
```
sudo apt-get install -f 
sudo dpkg --configure -a
``` if any errors occur post them here .
Thanks

---

### Post by crave-n on 2012-03-29
[FONT=monospace]the code
[/FONT]sudo aptitude install ubuntu-desktop ubuntu-minimal ubuntu-standard xserver-xorg-video-all unity
it didnt install any new packages and 
sudo apt-get install -f
sudo dpkg --configure -a
also didnt install anything

---

### Post by astrobob.tk on 2012-03-29
In post #4 you post:

> **crave-n said:**
> 
```
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
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
compiz (unityshell) - Error: GL_ARB_vertex_buffer_object not supported

Segmentation fault 			 		
```



The last line is a "segmentation fault" which I guess is RAM-related! How much RAM have you got? And did you upgrade your system or did a fresh installation?

check this first: [http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)
& [http://askubuntu.com/questions/73871/unity-3d-not-longer-working-after-upgrade-on-a-ubuntu-g560](http://askubuntu.com/questions/73871/unity-3d-not-longer-working-after-upgrade-on-a-ubuntu-g560)

other related links: [http://ubuntuforums.org/showthread.php?t=1860485](http://ubuntuforums.org/showthread.php?t=1860485)
[http://ubuntuforums.org/showthread.php?t=1766545](http://ubuntuforums.org/showthread.php?t=1766545)

By the way, run the following command after you have logged in:

I guess the first link will surely fix things. Hope it helps.

---

