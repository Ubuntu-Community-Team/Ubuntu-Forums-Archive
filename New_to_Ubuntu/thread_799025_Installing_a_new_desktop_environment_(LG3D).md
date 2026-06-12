---
title: "Installing a new desktop environment (LG3D)"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by halberdier25 on 2008-05-18
Hey,

I am looking at installing Sun Microsystems' desktop Looking Glass 3D.  I used [this](http://www.ubuntugeek.com/install-sun-looking-glass-desktop-environment-in-ubuntu.html) tutorial, but when I get to the sources.list file, I don't know where to go.  It won't let me add anything, but I can overwrite, which is something I'm not willing to do without confirmation of its safety.  Could someone please clear this up?  Thanks,

Gutsy Gibbon Ubuntu

---

### Post by shifty_powers on 2008-05-18
to add anything to your sources file,

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by JoshuaRL on 2008-05-18
[https://lg3d.dev.java.net/lg3d-getting-started.html](https://lg3d.dev.java.net/lg3d-getting-started.html)

That might get you started.  I think they might have a .deb for you to install with.

EDIT
From that page:
> 
There are 3 LG3D repositories. The stable repository has the latest stable releases (0.8.1, 1.0 etc.). The testing repository has the pre-release builds (alpha, beta etc.) for the latest version and the unstable repsoitory has the nightly builds. To access these repositories, add the following lines to /etc/apt/sources.list and then comment/uncomment the appropriate line(s). 
  	## LG3D repsoitories
  	deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) stable contrib
  	# deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) testing contrib
  	# deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) unstable contrib

Then you can 
          % apt-get update
  	  % apt-get install lg3d-core
        OR, on Ubuntu systems, 

run the Synaptic Package Manager from the System/Administration menu, 
click on the Reload button and then 
Search for lg3d and mark the lg3d-core package for installation. 
click on the Apply button to download and install 

Choosing lg3d-core for installation should automatically choose/mark lg3d-jdk and lg3d-java3d for installation. You will need to accept the 3 licenses for lg3d, jdk and java3d to complete the installation. 

Application Mode (lg3d-app) : This mode is also known as "app mode." In this mode also LG3D runs in a window on your desktop but now allows for native X11 applications to be run in the same window alongside LG3D applications. 
To run LG3D in the app mode : 

Check to see if OpenGL 1.3 or later is supported:

% glxinfo | grep "GLX version"
GLX version: 1.3

If you see a value lower than 1.3, update your graphics driver by following the descriptions in the Graphics Card section of the Requirements. LG3D may run with OpenGL 1.2, but 1.3 is highly recommended. 

Change the directory to the LG3D installation directory. 

Run the app mode by typing:

% bin/lg3d-app

In addition to the dev mode features, you should now be able to run X applications inside the LG3D window. Try running xterm by clicking the terminal icon on the taskbar. You should see an xterm floating inside the 3D space. If you encounter any issues, please refer to the Troubleshooting section. 

If you want, you can make the LG3D window start in fullscreen by using the "-f" option: 

% bin/lg3d-app -f 
In this mode lg3d-app is still running under the GNOME window manager, so you still have access to the GNOME taskbar and the applications it contains, but the LG3D window will always occupy the entire screen. You will not be able to resize it. 

If you'd like to configure the LG3D window further, check out the Resizing and Configuring LG3D Window document . 

Linux Note: if you have installed LG3D in /usr/share/lg3d and you ran postinstall during the installation process, there is another way to run app mode. In this configuration LG3D has been added as another desktop session type in the gdm desktop session chooser. When the system boots and the session chooser appears, click on "Session" and then click on the menu item "Looking Glass". In this mode GNOME does not run and LG3D runs as the sole window manager. 

Explore the Project Looking Glass desktop and start dreaming of new ways to enhance the desktop user experience with 3D! When you're ready to do development, skip over to the Project Looking Glass Developer's Guide for information about developing with Project Looking Glass

/EDIT

---

### Post by kamitsukai on 2008-05-18
OMG this looks amazing :D

---

### Post by halberdier25 on 2008-05-18
Ok, so it all went smoothly until terminal spat at me.

```
sudo apt-get install lg3d-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lg3d-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up lg3d-core (1.0.0) ...
/usr/share/lg3d/bin/postinstall: line 10: /bin/arch: No such file or directory
/usr/share/lg3d/bin/../bin/add-lg-to-gdm: line 28: /bin/arch: No such file or directory
Success. LG has been added as a gdm session.
/usr/share/lg3d/bin/postinstall: line 43: cd: /usr/share/lg3d/bin/../lib/linux-/lg3d-x11/programs/Xserver: No such file or directory
chown: cannot access `Xorg': No such file or directory
chgrp: cannot access `Xorg': No such file or directory
chmod: cannot access `Xorg': No such file or directory
dpkg: error processing lg3d-core (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 lg3d-core
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Now, when I go to change the session and log in it fails immediately.  Suggestions?

---

### Post by kamitsukai on 2008-05-18
well thats a shame i got an error installing it...[http://ubuntuforums.org/showthread.php?p=4989601](http://ubuntuforums.org/showthread.php?p=4989601) if anyone can help


[Edit]
i got same error as above

---

### Post by kamitsukai on 2008-05-18
Just tried to use it by selecting it from the login window and it brings up an error message and logs you out...

---

### Post by JoshuaRL on 2008-05-18
Alright, try these two commands:
```

sudo apt-get install -f
sudo dpkg --configure -a

```
and then log out to see if that is a Session you can run.

---

### Post by halberdier25 on 2008-05-18
Same error message logging in.  I reinstalled LG3D to see if it would change, but the exact same thing happened.

---

### Post by halberdier25 on 2008-05-18
[doublepost][bump]

I tried reinstalling it in the Synaptic Package Manager and got the following error at the end of installation:

```
E: lg3d-core: subprocess post-installation script returned error exit status 1
```

---

### Post by kamitsukai on 2008-05-18
Someone on my other thread has said that the packages are broken an there is nothing that can be done...[http://ubuntuforums.org/showthread.php?p=4989601](http://ubuntuforums.org/showthread.php?p=4989601)

---

### Post by kk0sse54 on 2008-05-18
such a shame it looked so sweet too.....

---

### Post by kamitsukai on 2008-05-18
> **C!oud said:**
> such a shame it looked so sweet too.....

Yer i know what you mean, i was getting really geared up to trying it:(

---

### Post by JoshuaRL on 2008-05-18
You might try their forums to see if you can get help or contact someone to let them know the package is broken.

[http://forums.java.net/jive/forum.jspa?forumID=80](http://forums.java.net/jive/forum.jspa?forumID=80)

---

### Post by kamitsukai on 2008-05-18
thnx i will let them know...

---

### Post by Rodomyro on 2008-12-11
Hello and salutes from Chile!

I have just found the solution to this installation problem:

I work with Ubuntu 8.04 

Just messing around with my terminal, I realized that all problems came due to 2 missing folders. So, with no more introductions, open up a Terminal (Yakuake rocks!):

```
sudo nautilus
```

Then make your way to 

/bin 

and create a Folder called "Arch"

The next move is to make your way to 

/usr/share/lg3d/lib


And change the name of folder 

"linux-x686" (or related)

to 

"linux-"

And that's it!! :lolflag:

Now, back to terminal, type:

```
sudo apt-get install -f
```
```
sudo dpkg --configure -a
```

And it should work without problems.

Enjoy !!

--Rodo--

---

### Post by nandu312 on 2009-02-13
That was Good one:)

---

### Post by gw7714 on 2009-03-05
I found a temporary solution, so you could at least try the desktop environment, it's a SLAX based live CD from Sun, here's a link:

                                        [https://lg3d-livecd.dev.java.net/Web-Site/Welcome.html](https://lg3d-livecd.dev.java.net/Web-Site/Welcome.html)

---

