---
title: "HELP needed to setup vncserver and run it."
date: 2012-09-26
forum: New to Ubuntu
---

### Post by xachu4u on 2012-09-26
Note: i have no prior experience using vnc nor have i seen anybody using vnc

I installed vncserver following the instructions given at:
[http://coddswallop.wordpress.com/2012/05/09/ubuntu-12-04-precise-pangolin-complete-vnc-server-setup/](http://coddswallop.wordpress.com/2012/05/09/ubuntu-12-04-precise-pangolin-complete-vnc-server-setup/)


this is what i did at the terminal:

[B]sudo apt-get update

sudo apt-get install gnome-core gnome-session-fallback vnc4server[/B]
##############################################################

now i changed the file .vnc/xstartup as shown

[B]#!/bin/sh

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
#exec /etc/X11/xinit/xinitrc
gnome-session --session=gnome-classic &

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &[/B]


#################################################################

next i typed **vncserver** at the command line
I didnt get any GUI...

the contents of the log file are:
[B]

Xvnc Free Edition 4.1.1 - built Feb  5 2012 20:04:02
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
Underlying X server release 40300000, The XFree86 Project, Inc


Thu Sep 27 08:46:26 2012
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5904
 vncext:      created VNC server for screen 0
error opening security policy file /etc/X11/xserver/SecurityPolicy
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Speedo/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/misc/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/75dpi/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/100dpi/, removing from list!
Could not init font path element /usr/share/fonts/X11/75dpi/, removing from list!
gnome-session[5284]: WARNING: Failed to acquire org.gnome.SessionManager[/B]

###########################################################

PLEASE help me solve this problem

---

### Post by HermanAB on 2012-09-27
Don't do that.

VNC is the favourite way (pretty much the only way) to get your Ubuntu machine hacked.

Rather read up on SSH and use that instead.  It does everything VNC does and much more, plus SSH is secure.

---

### Post by asmoore82 on 2012-09-27
> **HermanAB said:**
> Don't do that.

VNC is the favourite way (pretty much the only way) to get your Ubuntu machine hacked.

Rather read up on SSH and use that instead.  It does everything VNC does and much more, plus SSH is secure.

No, security is not a shiny shrink wrapped product that "just works." A proper VNC setup can be much more secure than SSH with a weak password. Likewise, a haphazard VNC setup is asking for trouble.

The real best practice that it would be very helpful to mention instead of just saying "VNC - there be dragons!" is that if you are going to use VNC over the Internet, not just a local LAN, then it should be locked down to only accept localhost traffic and you should tunnel into it with SSH (with a strong password :P).

---

### Post by steeldriver on 2012-09-27
> **xachu4u said:**
> 
next i typed **vncserver** at the command line
I didnt get any GUI...

PLEASE help me solve this problem

what exactly are you trying to do?

running vncserver in itself  won't give you a gui (on the local machine) - it will give you a port  you can connect to with a remote client to start an X session

we can help you set it up (securely - using SSH tunneling - if appropriate) but you will need to describe exactly what your situation is (what/where is the server? what client will you be using? will this be over a LAN or over a public network?)

---

### Post by xachu4u on 2012-09-27
well....security is not my top priority right now...

I want this thing to work....over a local network ( wifi adhoc..).

Isn't that possible?

---

### Post by xachu4u on 2012-09-27
@steel driver.

this is my plan.

Set up an ad-hoc connection

I go three laps(one with vnc server installed and other two has a vnc client, remmina remote desktop client)....

I need to "broadcast" my desktop on the other two laps...

Isn't that possible?What am i missing here?

---

### Post by steeldriver on 2012-09-27
What *buntus (distrib / version) are you running? the later ones include 'Desktop Sharing' out of the box, you just need to enable it then point your client at the remote port (5900 by default for the :0 primary display)

FWIW I'm not sure that vncserver will do what you want - sharing an existing physical display is typically done with vino (e.g. Ubuntu) or x11vnc (e.g. Xubuntu). AFAIK vncserver is more for headless situations (it's a display server in its own right, rather than relaying an existing display)

I can't help you with the adhoc networking

---

### Post by xachu4u on 2012-09-27
> **steeldriver said:**
> What *buntus (distrib / version) are you running? the later ones include 'Desktop Sharing' out of the box, you just need to enable it then point your client at the remote port (5900 by default for the :0 primary display)

FWIW I'm not sure that vncserver will do what you want - sharing an existing physical display is typically done with vino (e.g. Ubuntu) or x11vnc (e.g. Xubuntu). AFAIK vncserver is more for headless situations (it's a display server in its own right, rather than relaying an existing display)

I can't help you with the adhoc networking


ok.
i am using ubuntu 12.04 LTS. i have ticked the option "Allow other users to view your desktop"..but then how do i "point your client at the remote port (5900 by default for the :0 primary display)"?

I didn't understand that part. Do i need to use remmina.?

---

### Post by steeldriver on 2012-09-27
both server and client will default to port 5900 afaik so all you need to do in the remmina client is select VNC as the protocol and then fill in your remote IP (or hostname, if you have local name services) username and pw

---

### Post by EkiLibRiuM on 2012-09-27
I agree thatt in this way it's very good way to be hacked.....hmmmm..don't know ???....

---

### Post by toypilot on 2012-11-05
How does SSH do everything VNC does?

---

### Post by klein de usa on 2012-11-05
there isn't anything fast about setting up vnc in less you use [team viewer]("http://www.teamviewer.com/") over the internet

how i set it up is i install openssh server on all computers then i install x11vnc server on the computer that i wont to view and tightvnc viewer on the computers to view the vncserver  this method is really involved

---

