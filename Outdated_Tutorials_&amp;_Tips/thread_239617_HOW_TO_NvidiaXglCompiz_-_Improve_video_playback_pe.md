---
title: "HOW TO: Nvidia/Xgl/Compiz - Improve video playback performance/Eliminate Jaggies"
date: 2006-08-19
forum: Outdated Tutorials &amp; Tips
---

### Post by kpkeerthi on 2006-08-19
**About:**
1. How to eliminate choppiness and tearing in fullscreen Video/DVD playback and Cube rotation.
2. How to eliminate jaggies from compiz cube and window edges (wobbly plugin) - antialiasing

**Prequisites:**
1. Nvidia graphics card 
2. Binary "nvidia" driver.
3. Ubuntu 6.06 
4. Xgl/Compiz

**Step 1: Verify OpenGL** 
**Part 1**
Open a terminal and do:
```

$ glxinfo | grep OpenGL

```

If you get something similar to:
```

OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce Go 7800 GTX/PCI/SSE2
OpenGL version string: 1.2 (2.0.2 NVIDIA 87.62)

```
... then proceed to Part 2 of Step 1. 

If, otherwise, you see
```

OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

```
... follow [instructions here]("http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29") to install "nvidia" binary driver.

**Part 2**
Now, check if opengl libraries are linked properly:
```

$ ls -al /usr/lib/libGL.*

```

The result should be similar to:
```

**lrwxrwxrwx 1 root root     19 2006-08-19 09:39 /usr/lib/libGL.so -> /usr/lib/libGL.so.1**
lrwxrwxrwx 1 root root     17 2006-07-11 20:08 /usr/lib/libGL.so.1 -> libGL.so.1.0.8762
-rw-r--r-- 1 root root 540136 2006-07-10 07:10 /usr/lib/libGL.so.1.0.8762

```
Most importantly, you should see the line highlighted above. If not, do
```

$ sudo ln -s /usr/lib/libGL.so.1 /usr/lib/libGL.so

```
**Reboot**.

**Step 2: Eliminate "tearing" in DVD and other video playback**
Now that OpenGL has been setup properly, lets get the "tearing" fixed in fullscreen DVD playback.
**Part 1**
Enable vsync:
```

$ gksudo gedit /etc/init.d/gdm

```
Open the file and locate the line (near line# 37) containing:
```

if [ -r /etc/environment ]; then
  if LANG=$(pam_getenv -l LANG); then
    export LANG
  fi
  if LANGUAGE=$(pam_getenv -l LANGUAGE); then
    export LANGUAGE
  fi

fi

```

Now add ```
export __GL_SYNC_TO_VBLANK="1"
``` above it. It should now look similar to below:
```

**export __GL_SYNC_TO_VBLANK="1"**

if [ -r /etc/environment ]; then
  if LANG=$(pam_getenv -l LANG); then
    export LANG
  fi
  if LANGUAGE=$(pam_getenv -l LANGUAGE); then
    export LANGUAGE
  fi

fi

```
Save and exit.

Enable tripple buffering in xorg.conf:
```

$ gksudo gedit /etc/X11/xorg.conf

```
```

Section "Device"
        Identifier      "NVIDIA Corporation NVIDIA Default Card"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "RenderAccel"   "true"
**     Option          "TripleBuffer" "true"**
        Option          "NoLogo" 
EndSection

```

Save and exit. **Reboot**.

**Part 2**
Enable opengl driver in your favorite player. I personally prefer Totem-xine. 
```

$ gedit ./.gnome2/totem_config

```
Search for video.driver and add
```

video.driver:opengl

```
Save and exit.

Now, play your favorite video/DVD movie **fullscreen** in Totem-xine and enjoy tearless smooth playback.

Did you notice that cube rotation is also free from tearing? I'm sure you did. If not, try it now.

**Step 3: Eliminate jagged cube edges [OPTIONAL]**
Its also possible to eliminate the jaggies we get along the edges of the cube. Enable antialiasing by adding
```

export __GL_FSAA_MODE="2" 

```
to /etc/init.d/gdm.  **Reboot**. You should now have smooth antialiased cube and window edges. To see it in action, <Ctrl> <Atl> + left click on desktop and drag the mouse. Also dragging the windows by title bar (wobbly) should produce smooth edges.

Here is a setting that works best for me:
```

export __GL_SYNC_TO_VBLANK="1"
export __GL_FSAA_MODE="4"
export __GL_LOG_MAX_ANISO="4"
if [ -r /etc/environment ]; then
  if LANG=$(pam_getenv -l LANG); then
    export LANG
  fi
  if LANGUAGE=$(pam_getenv -l LANGUAGE); then
    export LANGUAGE
  fi

fi

```
Refer to [OpenGL Environment Variable Settings]("http://download.nvidia.com/solaris/1.0-8762/README/appendix-e.html") for more information.

**EDIT:**
This guide also helps improving the cool animations available in the latest version of compiz (quinn's). Try it to belive it.

---

### Post by lordsavant on 2006-08-19
Will ATI cards work with this tutorial past step 2 with the ATI binary drivers?  Thanks!

---

### Post by kpkeerthi on 2006-08-19
Unfortunately, no. The environment variables are nvidia specific.

---

### Post by neikous on 2006-08-24
Hm, I did everything this said, but I still have tearing in cube and wobbly. Any ideas?

I've got a PCI-E 7900 GT OC, 4 GB DDR2 4200 ram, dual 250 SATA 7200s, Pentium D 940 - 3.2 GHz. 

Everything works great except the vsync.

---

### Post by kpkeerthi on 2006-08-24
Can you post the output of ```
$ glxinfo | grep OpenGL
$ ls -al /usr/lib/libGL.*
```

.. and the environment variables in your /etc/init.d/gdm

---

### Post by neikous on 2006-08-24
$ glxinfo | grep OpenGL
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 7900 GT/PCI/SSE2
OpenGL version string: 1.2 (2.0.2 NVIDIA 87.62)
OpenGL extensions:





$ ls -al /usr/lib/libGL.*
lrwxrwxrwx 1 root root     19 2006-08-24 12:09 /usr/lib/libGL.so -> /usr/lib/libGL.so.1
lrwxrwxrwx 1 root root     17 2006-08-08 17:07 /usr/lib/libGL.so.1 -> libGL.so.1.0.8762
-rw-r--r-- 1 root root 540136 2006-07-10 10:10 /usr/lib/libGL.so.1.0.8762



Here's my whole GDM file, I'm not very Linux savvy so I wasn't sure exactly what to post. -

#! /bin/sh
#
# Originally based on:
# Version:	@(#)skeleton  1.8  03-Mar-1998  [email]miquels@cistron.nl[/email]
#
# Modified for gdm, Steve Haslam <steve@arise.dmeon.co.uk> 14mar99
# modified to remove --exec, as it does not work on upgrades. 18jan2000
# modified to use --name, to detect stale PID files 18mar2000
# sleep until gdm dies, then restart it 16jul2000
# get along with other display managers (Branden Robinson, Ryan Murray) 05sep2001

set -e

# To start gdm even if it is not the default display manager, change
# HEED_DEFAULT_DISPLAY_MANAGER to "false."
HEED_DEFAULT_DISPLAY_MANAGER=true
DEFAULT_DISPLAY_MANAGER_FILE=/etc/X11/default-display-manager
PATH=/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/sbin/gdm
PIDFILE=/var/run/gdm.pid
UPGRADEFILE=/var/run/gdm.upgrade

if [ -e $UPGRADEFILE -a "$1" != "restart" -a "$1" != "force-reload" ]; then
	SSD_ARG="--startas $DAEMON"
	rm -f $UPGRADEFILE
else
	SSD_ARG="--exec $DAEMON"
fi

# Allow cdd to override the config
if [ -f /etc/gdm/gdm-cdd.conf ]; then
	CONFIG_FILE="--config=/etc/gdm/gdm-cdd.conf"
fi

test -x $DAEMON || exit 0

export __GL_SYNC_TO_VBLANK="1"

if [ -r /etc/environment ]; then
  if LANG=$(pam_getenv -l LANG); then
    export LANG
  fi
  if LANGUAGE=$(pam_getenv -l LANGUAGE); then
    export LANGUAGE
  fi

fi

. /lib/lsb/init-functions

case "$1" in
  start)
  	if [ -e "$DEFAULT_DISPLAY_MANAGER_FILE" -a "$HEED_DEFAULT_DISPLAY_MANAGER" = "true" -a "$(cat $DEFAULT_DISPLAY_MANAGER_FILE 2>/dev/null)" != "$DAEMON" ]; then
		log_warning_msg "Not starting GNOME Display Manager (gdm); it is not the default display manager."
	else
		# if usplash is runing, make sure to stop it now, yes "start" kills it.
	        if pidof usplash > /dev/null; then
			/etc/init.d/usplash start
		fi
		log_begin_msg "Starting GNOME Display Manager..."
		start-stop-daemon --start --quiet --oknodo --pidfile $PIDFILE --name gdm $SSD_ARG -- $CONFIG_FILE >/dev/null 2>&1 || log_end_msg 1
		log_end_msg 0
	fi
  ;;
  stop)
	log_begin_msg "Stopping GNOME Display Manager..."
	start-stop-daemon --stop  --quiet --oknodo --pidfile $PIDFILE --name gdm $SSD_ARG --retry 30 >/dev/null 2>&1
	log_end_msg 0
  ;;
  reload)
	log_begin_msg "Reloading GNOME Display Manager configuration..."
	log_warning_msg "Changes will take effect when all current X sessions have ended."
	start-stop-daemon --stop --signal USR1 --quiet --pidfile \
		$PIDFILE --name gdm $SSD_ARG >/dev/null 2>&1
	log_end_msg 0
  ;;
  restart|force-reload)
	$0 stop || true
	$0 start
  ;;
  *)
	log_success_msg "Usage: /etc/init.d/gdm {start|stop|restart|reload|force-reload}"
	exit 1
  ;;
esac

exit 0





Thanks for the quick reply :)

---

### Post by BongoBob on 2006-08-25
Would anyone happen to know how would I go about enabling openGL for VLC media player?

---

### Post by metathran on 2006-08-27
I already knew this tips and it really increase image quality, tearing in video, and cube edge aliasing...

But there is a disadvantage to use

```

export __GL_FSAA_MODE="2" 

```

With this setting everything is smooth but FSAA seems to be applied to the font too, so when you wait 3-4 seconds when watching pages in firefox you can clealy see that font become blur, and this effect disappear if you click on the page then come again a few seconds later...

In fact it affects everything displayed on the screen for example the toolbar of this form become blur...

](*,)

---

### Post by junamuno on 2006-08-27
Great Guide!!!! ThX

---

### Post by kpkeerthi on 2006-08-27
> **metathran said:**
> 
export __GL_FSAA_MODE="2" 
With this setting everything is smooth but FSAA seems to be applied to the font too, so when you wait 3-4 seconds when watching pages in firefox you can clealy see that font become blur, and this effect disappear if you click on the page then come again a few seconds later...

In fact it affects everything displayed on the screen for example the toolbar of this form become blur...

Hmm.. Thats strange. I don't see the problem with my setup. Did you check the FSAA settings that is appropriate for your video card here...
[http://download.nvidia.com/solaris/1.0-8762/README/appendix-e.html](http://download.nvidia.com/solaris/1.0-8762/README/appendix-e.html)

FSAA="2" seems to have different effect in different cards. May be that should explain why. Just wondering? :confused:

---

### Post by metathran on 2006-08-27
I will try others settings, i have a 6600GT AGP
For now i tried with "1" and "2" but same results

...And yes if i remove the lines from gmd it solves the problem but i lost antialiasing of course...

---

### Post by etotehpii on 2006-08-29
When I search for video.driver in totem_config it comes up with nothing.  I've been able to do everything without any problems up until this step.

---

### Post by kpkeerthi on 2006-08-29
Try adding the property yourself at the end of the file.

---

### Post by FuturePilot on 2007-02-18
> **etotehpii said:**
> When I search for video.driver in totem_config it comes up with nothing.  I've been able to do everything without any problems up until this step.
Same here. There seems to be no directory for /.gnome2/totem_config. So far I've been able to fix the 3D cube from tearing, now if I could just get it to stop tearing up my videos so bad. How would you go about adding that line to Mplayer?

---

### Post by WakkiTabakki on 2007-02-18
> **FuturePilot said:**
> Same here. There seems to be no directory for /.gnome2/totem_config. So far I've been able to fix the 3D cube from tearing, now if I could just get it to stop tearing up my videos so bad. How would you go about adding that line to Mplayer?

Since some totem versions ago, it no longer has its own output setting but uses the Gnome settings.
Run  gstreamer-properties from the terminal (or 'Multimedia System Selector' from the System-menu, which is hidden by default!) and choose the output sink under Video/Default Output.
Note that opengl is probably not listed, so choose 'Custom' and type in 'glimagesink' (the package 'gstreamer0.10-gl' must be installed).

The output is clear and fast with no tearing at all (video with sideways movement give me horrible tearing using xv video output). Unfortunately, the gl-sink start in its own window, and is completely out of sync with audio (at least in Edgy, haven't tried the Feisty versions yet...)

/N

---

### Post by FuturePilot on 2007-02-18
Ok, now it works perfectly when I'm running Beryl. But when I'm not running Beryl I still get jaggies. Is there a way to get it working good when not using Beryl?

---

### Post by sshetye on 2007-02-25
<Since this came up 1st hit on google for video slowdown in beryl>

For ATI folks: Try mplayer.

1. enable "multiverse" and "universe" servers in the System->Administration->Software sources

2. Search for mplayer in synaptics package manager for mplayer.

3) Install Smile

4) On compiz/beryl/some opengl desktop, the following worked for me.

- X11 (software mode, poor quality)
- Xv (accelerated video, black screens on other software, WORK great in mplayer)
- OpenGL (again, works great but screen flashes for the 1st 1-2 seconds).

The point is that the video doesn't run in "3d" - if you try spinning the desktop/cube, only the video's window border flies around in 3d space. The actual video itself remains in 2d, "behind" the borders of the window (like a portal?).

Anyway, its the best of having the 3d desktop AND having accelerated filtered video. Try it out.

FYI, my setup is ATI Radeon 9800 with Xorg drivers (NOT ATI proprietary) with beryl doing the eye candy.

---

### Post by foureight84 on 2007-03-16
is there a guide to do this for intel/aiglx? i have an issue with jagged videos using xshm and totem-xine. i tried using gxine instead of xshm but the contrast is off, and there's a weird blue overlay when i move the window around.

---

### Post by Princegiri on 2007-12-27
NOTE: posted this in the 'compiz fans.. try this guide' thread also.. came here as this one was active

Hai.... i followed the guide and stuff... evrything you said is true.....

but then though there are no jaggies and tearing on the cube, there is heavy tearing on the wobbly windows.... cant seem to eliminate that.....
must i turn off some options in the nvidia-settings panel? [i mean by introducing variables like .. VBLANK=1 .. we are forcing some stuff rite? so should some options on the nvidia panel be turned off?]

AND the same 'no jaggies' and 'no tearing' on the compiz cube were obtained by other means as well ... check this out......
[http://ubuntuforums.org/showthread.p...=anti+aliasing](http://ubuntuforums.org/showthread.p...=anti+aliasing)
I tried this out seperately, and it works too..... but still there is heavy tearing on the wobbly windows

i cant seem to eliminate tearing on the wobbly windows [by making any open window taller than it is wide, and moving it from side to side you should see tearing if any].... THe cube however looks gorgeous......

ps ; im on Fiesty Fawn 32 bit with a 8600 GS card

---

