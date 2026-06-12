---
title: "System no longer boots into X."
date: 2011-07-28
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by PhantmKllr on 2011-07-28
After a recent update, my system no longer starts an X server.

From what I can tell, the system boots successfully, but then just hangs.

I can use Ctrl -> Alt -> F2 to get to the command line, where I have been running updates (using apt-get upgrade / dist-upgrade) for the past few days now, but none of them have fixed the problem.

I'm not sure if this is LightDM's fault, but earlier I tried to set the new unity login screen as default, and the same thing happened, so I changed it back.

Is anyone else having this problem, and if so, have you been able to fix it?

---

### Post by garvinrick4 on 2011-07-28
You do have these 2 packages installed now:
lightdm
lightdm-gtk-greeter
sudo start lightdm (should say running)
startx (hopefully works)
If not working yet reboot and see if boots for you:
Below is the 2 packages that work for 3 installs for me.
```
Package: lightdm-gtk-greeter             
New: yes
State: installed
Automatically installed: no
Version: [COLOR=Red]0.9.2-0ubuntu4[/COLOR]
Priority: optional
Section: x11
Maintainer: Robert Ancell <robert.ancell@ubuntu.com>
Uncompressed Size: 160 k
Depends: libc6 (>= 2.2.5), libcairo2 (>= 1.2.4), libgdk-pixbuf2.0-0 (>= 2.22.0),
         libglib2.0-0 (>= 2.16.0), libgtk-3-0 (>= 3.0.0),
         liblightdm-gobject-1-0, libx11-6
Recommends: lightdm
Provides: lightdm-greeter, lightdm-greeter-example-gtk
Description: LightDM GTK+ Greeter
 A LightDM greeter that uses the GTK+ toolkit.
Homepage: https://launchpad.net/lightdm




``````

Package: lightdm                         
New: yes
State: installed
Automatically installed: no
Version: [COLOR=Red]0.9.2-0ubuntu4[/COLOR]
Priority: optional
Section: x11
Maintainer: Robert Ancell <robert.ancell@ubuntu.com>
Uncompressed Size: 328 k
Depends: debconf (>= 0.5) | debconf-2.0, upstart-job, libc6 (>= 2.4),
         libglib2.0-0 (>= 2.28.0), libpam0g (>= 0.99.7.1), libxcb1, libxdmcp6,
         libpam-runtime (>= 0.76-14), libpam-modules, adduser,
         lightdm-gtk-greeter | lightdm-greeter
PreDepends: dpkg (>= 1.15.7.2)
Recommends: xserver-xorg
Conflicts: liblightdm-gobject-0-0, liblightdm-qt-0-0
Provides: x-display-manager
Description: Display Manager
 LightDM is a X display manager that: 
 * Has a lightweight codebase 
 * Is standards compliant (PAM, ConsoleKit, etc) 
 * Has a well defined interface between the server and user interface 
 * Cross-desktop (greeters can be written in any toolkit)
Homepage: https://launchpad.net/lightdm

rick@rick-HP:~$ 


```
Also a link here:
[http://ubuntuforums.org/showthread.php?t=1813060](http://ubuntuforums.org/showthread.php?t=1813060)

---

### Post by garvinrick4 on 2011-07-28
These are what are installed in lightdm in Synaptics

---

### Post by Liquidplay on 2011-07-28
I had the same issue, when I removed all other lightdm related packages and re-installed lightdm and lightdm-gtk-greeter everything went back to normal (no more hangs during boot).

---

### Post by PhantmKllr on 2011-07-28
> **garvinrick4 said:**
> 
startx (hopefully works)


I run this and the X-server starts, but all I get is a black screen and a dialog box that reads: "Failed to start session 'gnome'". I click the button, and it boots me back to the command line.

Reading back at the text printed by the command "startx", there was a line that read "Failed to load module Nvidia". Maybe there's a problem with the Nvidia driver again?

> **Liquidplay said:**
> I had the same issue, when I removed all other lightdm related packages and re-installed lightdm and lightdm-gtk-greeter everything went back to normal (no more hangs during boot).

You seem to be misinterpreting my problem here. The system hangs after the boot process, but doesn't even load X-server, or LightDM for that matter.

In short, LightDM never gets the chance to load.

---

### Post by PhantmKllr on 2011-07-28
Here's the text printed by "startx":

```

(EE) FATAL: Module nvidia not found.
(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
(EE) NVIDIA:     system's kernel log for additional error messages.
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) Failed to load module "nv" (module does not exist, 0)
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

```

Had to retype this, I did my best to recreate the look. :lolflag:

---

### Post by Harry33 on 2011-07-28
> **PhantmKllr said:**
> Here's the text printed by "startx":

```

(EE) FATAL: Module nvidia not found.
(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
(EE) NVIDIA:     system's kernel log for additional error messages.
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) Failed to load module "nv" (module does not exist, 0)
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

```

Had to retype this, I did my best to recreate the look. :lolflag:

Try reinstalling nvidia-current from the repos.
You can do that from the root shell prompt:
```

sudo apt-get install --reinstall nvidia-current

```

---

### Post by xeizo on 2011-07-28
> **Harry33 said:**
> Try reinstalling nvidia-current from the repos.
You can do that from the root shell prompt:
```

sudo apt-get install --reinstall nvidia-current

```

I second that. Since about a week or so ago nvidia-current is no longer updated when installing a new kernel, like it always used to be before. So, one has to reinstall nvidia-current to compile/activate the nvidia kernel module.

I guess this will change back to like it was before wtih newer kernels.

---

### Post by 23dornot23d on 2011-07-28
Check this thread out too ..... [[COLOR=Red]_***LINK***_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1804394&page=4") ...... as I had to follow this to get it all working and had the exact same problem the module was not being seen for Nvida

---

### Post by silex89 on 2011-07-28
My system has the same problem, I'm running Oneiric through a Virtual Machine and hangs at the battery state check after the update:(

---

### Post by PhantmKllr on 2011-07-29
> **Harry33 said:**
> Try reinstalling nvidia-current from the repos.
You can do that from the root shell prompt:
```

sudo apt-get install --reinstall nvidia-current

```

> **xeizo said:**
> I second that. Since about a week or so ago nvidia-current is no longer updated when installing a new kernel, like it always used to be before. So, one has to reinstall nvidia-current to compile/activate the nvidia kernel module.

I guess this will change back to like it was before wtih newer kernels.

Alright, I'll go ahead and try it.

I won't have access to the computer for a few days, so I try it then.

---

### Post by PhantmKllr on 2011-08-02
> **Harry33 said:**
> Try reinstalling nvidia-current from the repos.
You can do that from the root shell prompt:
```

sudo apt-get install --reinstall nvidia-current

```

Put simply, this did not work.

I've been away from the computer for the past few days, and today I got around to downloading the massive amount of updates that were waiting for me, but no luck there either.

Running "startx" simply results in a blank screen. When I get back to the command line (Ctrl -> Alt -> F2), this message repeats:

> No protocol specified

and if I wait awhile, I get:

> 
xinit: giving up
xinit: unable to connect to X server: Connection refused

waiting for X server to shut down  ddxSigGiveUp: Closing log

xinit: server error
xauth:  error in locking authority file /home/*phantmkllr*/.Xauthority


Once again, care was taken to recreate the message(s) exactly as they were displayed.

Any ideas?

---

### Post by PhantmKllr on 2011-08-04
Bumping... it... up.

---

### Post by jerrylamos on 2011-08-04
Alpha 3 "Dead On Arrival".

ATI Radeon Xpress 200 "no screens found" won't do X at all.

Even tried "vesa".  Dead X.

Tried apt-get update, apt-get upgrade from command line - 500 packages upgraded(!), 15 held back, still broke.

Jerry

---

### Post by PhantmKllr on 2011-08-06
...Bump...

---

### Post by jerrylamos on 2011-08-07
lightdm still failing to start desktop on Alpha 3 Live and every daily build Live since.

Tried apt-get install lightdm-gtk-greeter and couldn't find the package,  How is Live ever going to work without lightdm-gtk-greeter even installed?

Copied in sources.list from Alpha 2, installed "new package" lightdm-gtk-greeter and still wouldn't start desktop.

apt-get install lightdm with the Alpha 2 sources.list then desktop came up.  I'm using it here.

I haven't figured out how to do ubuntu-bug to report missing desktop because desktop has to be running to file the report.  There's apparently some way do do it with "elink" but I don't know how yet.

Alpha 3 and every daily build since live is dead on arrival.

Jerry

---

### Post by sgage on 2011-08-07
> **jerrylamos said:**
> Alpha 3 and every daily build since live is dead on arrival.

The following procedure has always worked for me:

Boot into recovery mode - networked root

```
apt-get remove nvidia-current
rm /etc/X11/xorg.conf
rm /etc/modprobe.d nvidia-graphics-drivers.conf
```

Now reboot, and you'll be running with nouveau. At this point, I've been able to successfully install nvidia-current with jockey, though you may have to run nvidia-xconfig to get a proper xorg.conf.

Reboot and enjoy the nvidia drivers.

---

