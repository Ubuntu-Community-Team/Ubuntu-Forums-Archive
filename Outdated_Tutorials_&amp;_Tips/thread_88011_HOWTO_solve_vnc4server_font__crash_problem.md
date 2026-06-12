---
title: "HOWTO solve vnc4server font / crash problem"
date: 2005-11-09
forum: Outdated Tutorials &amp; Tips
---

### Post by milstead on 2005-11-09
I know this has been covered in depth in the VNC and GDM thread but I thought I would share my experience and fix for getting any old type of vnc4server to work on my Breezy system.

I was running vnc4server from an ssh server session and it was not working. Looking at the log file I discovered that it was dying because it couldn't find any fonts.

I fixed the problem by adding a link:

cd /usr/X11R6/lib/X11
sudo ln -s /usr/share/X11/fonts fonts

I think this is a bug left over from the move from XFree86 to XOrg?

It could also be some side effect of using the nvidia-glx package since the /usr/X11R6/lib directory has some nvidia files in it but not much else.

I am brand new to the forum and fairly new to Ubuntu. I'm not sure if this is the best place to post this and whether or not I should post a bug report (somehow/someplace).

Timie Milie.

---

### Post by ubuntu_demon on 2005-11-09
I changed the title of your thread

[I]This is for vncserver instead of vnc4server :

These two variables gave me some troubles when I upgraded from hoary to breezy. Commenting depth and pixelformat in /etc/vnc.conf may solve some problems :

Example: 
# $depth = "16";
# $pixelformat = "rgb565";[/I]

---

### Post by milstead on 2005-11-09
Breezy was a fresh install. The system is NOT an upgrade. I can see how my post could have caused this confusion. I meant that the change from XFree to XOrg was a developer one - that had perhaps created some bugs.

Might be worth changing the title back again?

Tim.

---

### Post by ubuntu_demon on 2005-11-09
[QUOTE=milstead]Breezy was a fresh install. The system is NOT an upgrade. I can see how my post could have caused this confusion. I meant that the change from XFree to XOrg was a developer one - that had perhaps created some bugs.

Might be worth changing the title back again?

Tim.[/QUOTE]
lol :-P
done

---

### Post by grendelkhan on 2005-11-23
I linked the xorg.conf to XF86Config and that did the trick for me.

---

### Post by nolodude on 2005-12-06
Thanks, that font link solved my problem with VNC to GDM connection.

Now I only need to find out why TV-out stopped working...

---

### Post by maino82 on 2006-01-29
I have checked out the VNC to GDM thread, as well as this one, but I am still having font problems with vncserver. I added the link but it does not seem to have done anything. Log file follows:

Sun Jan 29 15:53:11 2006
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5901
 vncext:      created VNC server for screen 0
Could not init font path element /usr/X11R6/lib/X11/fonts/Speedo/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/CID/, removing from list!

Fatal server error:
could not open default font 'fixed'
xsetroot:  unable to open display 'server1:1'
vncconfig: unable to open display "server1:1"

(gnome-terminal:10488): Gtk-WARNING **: cannot open display:
Window manager error: Unable to open X display server1:1
xset:  unable to open display "server1:1"
xsetroot:  unable to open display 'server1:1'
startkde: Starting up...
ksplash: cannot connect to X server server1:1
kded: cannot connect to X server server1:1
DCOP aborting call from 'anonymous-10540' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
kcminit: cannot connect to X server server1:1
ksmserver: cannot connect to X server server1:1
startkde: Shutting down...
klauncher: Exiting on signal 1
sound server terminated
startkde: Running shutdown scripts...
startkde: Done.

I can plainly see that it is a font problem, but simply adding the link didn't seem to fix that. What might I be overlooking here?

---

### Post by dbott67 on 2006-12-29
Although this is an old thread, please read this important security vulnerability about vnc4server if you're using it: 

[http://www.ubuntuforums.org/showthread.php?t=327275](http://www.ubuntuforums.org/showthread.php?t=327275)

-Dave

---

