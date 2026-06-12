---
title: "X11 Forwarding full desktop to Linux, Windows and macOS"
date: 2019-06-13
forum: New to Ubuntu
---

### Post by artim96 on 2019-06-13
Since I have absolutely no clue where to post this, I'm doing it here:
We have a PC running Ubuntu 19.04 including SSH Server. Now I would like to write a manual for the topic in the headline. Setting up X11 Forwarding isn't hard for any of the OSs. But I don't want our users to have to figure out the name of the program they might want to "stream", I want to get the whole gnome desktop. But all I could find was "startx". But executing that, Putty (on Windows) just gives me 
```
/usr/lib/xorg/Xorg.wrap: Only console users are allowed to run the X serverxinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error
Dateideskriptor, der auf die Konsole verweist, konnte nicht gefunden werden.
```
(Yes, that strange mix of English and German).

What I have as manual:
For Linux, just use ssh -X, -C if compression needed.

For macOS, install XQuartz, rest like Linux.

For Windows, install VcXsrv (seems to be the best choice, still getting updates) as X Server and Putty for ssh, enable X11 Forwarding in Putty.
Is there any special setting for VcXsrv I forgot? I don't have any macOS or Linux device to check with.

---

### Post by TheFu on 2019-06-14
XDMCP is the way a full window manager is remotely accessed for X/Windows. I don't think it works over ssh -X.
Have you considered using x2go?  It is 2-3x faster than VNC-anything and uses ssh authentication in the NX protocol.  No need to touch putty on Windows, except to setup the ssh-keys.  It works with OSX, Linux and Windows clients.

Simple, one solution, stuff that works better than the alternatives is a good thing, right?

I wouldn't use non-LTS desktops in a business.  19.04 support ends in 6 months. Do you really want to upgrade business desktop OSes every 6 months?

If you don't need the entire desktop, you can use ssh -X on the LAN.  It doesn't work so great over the WAN, IME.  Also, video streaming isn't really possible with any of the non-commercial solutions. It works, sorta, if the network is fast enough, but ... it isn't good and hidef content is really poor.

If your Ubuntu systems are running inside a KVM virtual machine, then you can use the SPICE display protocol. I believe this to be the highest performance solution for remote video on a LAN available today. Access to any virtual machine desktop is possible using SPICE with local QXL video drivers loaded.  I think ssh tunnels can be configured and know that TLS encryption can be used.  I find the day to day connection for SPICE is outside my workflow, so even though I use remote desktops daily, almost all day, SPICE isn't compelling enough for my needs.  x2go is stable and works really well for business productivity needs. It is my habit and has thin client options.



[https://wiki.ubuntu.com/xdmcp](https://wiki.ubuntu.com/xdmcp) - commonly used in LANs with very thin clients running an X/Server.
[https://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](https://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications) is a little old, but might help lurkers with a few options.

---

### Post by artim96 on 2019-06-14
Well, we are no business in the typical sense and 18.10 and maybe even older versions are no option because of a bug that has been fixed earlier this year but for some reason hasn't been backported to 18.10.

I've read about XDMCP already but nothing with that much detail, so thanks for that. I'll try that out and see if I already set it up correctly yesterday.
But am I understanding right that with X2go can just get the whole desktop while still authenticate via ssh? That PC has no ssh key secured connection since you can't get anything that relevant, you authenticate via LDAP.
But to get the desktop, am I just launching X2go or do I have to launch the desktop environment through a command first?

---

### Post by TheFu on 2019-06-14
18.10 EOL was last month.  18.04 is the current LTS. Releases for even years, in April are when Ubuntu LTS releases happen.  18.04 gets backports for security issues and new kernels though the HWE upgrades available with each .1, .2, .3, .4. .5, release.
I'm on 
```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04[COLOR="#FF0000"].6[/COLOR] LTS
Release:        16.04
Codename:       xenial
```
an LTS release with linux-generic-hwe-16.04  providing kernel version 4.15.0.51.72.  More about HWE: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

x2go has multiple methods for how remote stuff is displayed.  By default, you get the desktop. It is a virtual desktop, not the one someone sitting local would see.  10, 50, 100 people can remote connect to the same computer and each see their own desktop. There is a way for a view-only "watcher." I've never used that, but I've seen it used at a tech conference to make recordings of presentations with the presentation full screen and talking head in a corner.  The most my little company had concurrently on the same machine via x2go was 6 - that was everyone in the company.

No need to start ssh/putty just prior to running the x2go client.  There are command line options to make it 1 button to get a desktop or one specific window/application.  As with all remote desktop solutions, don't use a heavy GPU-dependent desktop. If you use LXDE, XFCE or Mate desktop environments, with the correct keyboard mappings (see x2go wiki), they all work pretty well. On Windows, I installed the full font package too.

The NX protocol includes ssh for the connection. Any method used by ssh to authenticate users should workm assuming the ssh authentication is working.  I've used ssh with passwords, ssh-keys, and if the remote system is setup in PAM to allow ssh authentication via LDAP, then that works too. I've used it - openldap. 

There are many kinds of optimizations for having multiple clients on the same machine to make the CPU and RAM needed efficient.

It took me longer to write this reply than it would have to install and try out x2go.  Use their PPA and follow their install instructions.  On Windows, I have to remember to manually get a new install - I hate the way Windows doesn't centralize management of installed software.

---

### Post by artim96 on 2019-06-14
well, X2Go isn't compatible with GNOME and even through XDMCP I can't get it to work. And I think that's all already too much. And I don't really need fancy stuff like multiple sessions. All I want is to just simply transmit the GNOME desktop through X11 forwarding.
All you are posting might be nice but completely misses the point. And I can't imagine that it should be that hard to just launch up GNOME through terminal.

In the mean time back to the setup I started with I stumbled over "gnome session" to just execute to start the desktop. But that just gives me a blank screen. But checking for that package I see it's not installed. But in the Snap list I find gnome-3-26-1604 and gnome-3-28-1804, but I can't just run them via snap run gnome-3-28-1804. That gives me "Fehler: Kann Anwendung "gnome-3-28-1804" nicht in "gnome-3-28-1804" finden" (Error: can't find application "gnome-3-28-1804" in "gnome-3-28-1804")....how do I run gnome through terminal then?

---

### Post by TheFu on 2019-06-14
x2go is compatible with Gnome2.  Mate, Cinnamon, XFCE, LXDE are all based on Gnome2.
[https://wiki.x2go.org/doku.php/doc:de-compat](https://wiki.x2go.org/doku.php/doc:de-compat) has the list of known working DEs.

Nothing prevents gnome2, 3, 4, libraries and programs written to use those libraries from working on a gnome2 desktop or any other compatible Window Manager. There is a standard. The Gnome development team decided to require high-end graphics in their v3 solution. It was a trade-off.

XDMCP is really old. The last time I saw it used anywhere was in the mid-1990s. ZERO security.

I tried setting up a VNC server, running a client with a base X/server, then manually set the DISPLAY and running gnome-session. Got the fail-whale error, which basically says not enough of gnome was running to even display or figure out an error to report.

Sorry. I don't have any better answer other than what has already been posted. Good luck to you. If you do find a solution, please post it here.

---

### Post by kevdog on 2019-06-15
I take it that installing cygwin isn't an option on your windows machine?

---

### Post by artim96 on 2019-06-17
> **kevdog said:**
> I take it that installing cygwin isn't an option on your windows machine?
I want to make it as easy as possible. If it's a easy as the one I described or even easier (and especially no further performance issues, X11 Forwarding already doesn't seem to be the fastest) it would be a solution

---

### Post by artim96 on 2019-06-17
Anyways, I have the feeling that Ubuntu 19.04 uses a lot of snap apps for the desktop (I already replaced the calculator and system monitor with the deb variants since snaps are slow as hell, even slower than flatpaks), at least "snap list" shows apps like gnome-3-28-1804, gnome-characters and gtk-common-themes. So I used this manual [https://linuxconfig.org/how-to-install-gnome-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-install-gnome-on-ubuntu-18-04-bionic-beaver-linux) to install normal gnome, following the "Full Gnome Desktop Installation on Ubuntu" part, but I have still no gnome-session for installed packages. So not sure how to get the right package name to launch it

---

### Post by kevdog on 2019-06-17
Wait -- I might be confused.  Describe your situation.  What exactly are you trying to do.  ssh over an X session from a Windows machine to a Linux server?  And your having a problem installing a Xserver on Windows?

---

### Post by artim96 on 2019-06-17
> **kevdog said:**
> Wait -- I might be confused.  Describe your situation.  What exactly are you trying to do.  ssh over an X session from a Windows machine to a Linux server?  And your having a problem installing a Xserver on Windows?
I think I was quite clear. I want X Forwarding over ssh and display the whole desktop. Independent of source OS. But I can't figure out how to actually make it start the desktop environment since I have no clue what's the right package name

---

### Post by kevdog on 2019-06-17
Maybe it wasn't clear to me.  Source OS??? I'm not sure what you mean.

Here's how I'm interpreting.

Server - Ubuntu (Or linux variant)
Client - Mac,OS,Windows

On the client machine you actually have to install an X-server.  (I know the terminology doesn't make sense, but the client machine needs to run an X-Server for this process to work)
So for various clients
Linux - X server is built in
MacOS - XQuartz
Windows - Xming (that's what I would use, although there are other clients that could be used as well).

---

### Post by artim96 on 2019-06-23
Server: Ubuntu 19.10
Clients: macOS, Windows, Linux

the part with the X server is already written.

If you'd actually read my posts you'd have seen in the first post
> [COLOR=#000000]What I have as manual:
[/COLOR][COLOR=#000000]For Linux, just use ssh -X, -C if compression needed.[/COLOR]

[COLOR=#000000]For macOS, install XQuartz, rest like Linux.[/COLOR]

[COLOR=#000000]For Windows, install VcXsrv (seems to be the best choice, still getting updates) as X Server and Putty for ssh, enable X11 Forwarding in Putty.[/COLOR]
[COLOR=#000000]Is there any special setting for VcXsrv I forgot? I don't have any macOS or Linux device to check with.[/COLOR]
and in my last post
> [COLOR=#000000]But I can't figure out how to actually make it start the desktop environment since I have no clue what's the right package name[/COLOR]

So X Server is obviously no problem since I'm able to run any other GUI program I know the package name of. That still doesn't help me calling the GNOME desktop (especially without root rights). I can find out somehow what I have to call to display the program I want to use. But the guide is meant for people having no clue about stuff and probably don't want to know. So I want to tell them how to call the desktop so they can run everything like they are sitting in front of the PC. But therefore I'd have to figure out how to actually call the desktop environment. "gnoem-session" just displays a blank black screen.

---

