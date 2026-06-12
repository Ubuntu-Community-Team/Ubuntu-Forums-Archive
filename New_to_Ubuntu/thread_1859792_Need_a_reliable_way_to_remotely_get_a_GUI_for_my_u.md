---
title: "Need a reliable way to remotely get a GUI for my ubuntu server..."
date: 2011-10-14
forum: New to Ubuntu
---

### Post by ChipGibblets on 2011-10-14
Server runs: Ubuntu Server 11.04
Client Machine runs: Vista (I know, I know...)
Connecting via my LAN
 
 
I can easily access my server remotely via putty.  I COULD access my server via Tight VNC to get a GUI.  NOW I only get a grey screen in TightVNC and I don't know why...
 
Here's how my (vim .vnc/xstartup) looks:

#!/bin/sh

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
exec sh /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 1280x1024+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &
 
I should be able to input this command: 
 
vncserver -geometry 1280x1024 -depth 24
 
And then open tightVNC, select my server, enter the password and be in.  Now I have a grey screen.  

So, I can either keep trying with tightVNC, and probably keep failing or I can try another method.  

All I want to do is be able to get a GUI look at my server via my laptop and I'm open to any help on this.  

Thank you so much.
 
NOTE: TightVNC used to immediately issue an error when I logged into the server stating (the panel encountered a problem while loading: "OAFIID:GNOME_FastUserSwitchApplet") where I could either click 'don't delete' or 'delete'.  I was told to click delete and that always worked...but one time I accidentally clicked 'don't delete' and tightVNC hasn't worked since AND I've never been given that prompt again.  
 
Please help!!!

---

### Post by collisionystm on 2011-10-14
try XRDP

sudo apt-get install xrdp

Lets you RDP to your server instead of VNC.

NOTE: You will not get the same desktop you get when at the keyboard and mouse. To my knowledge there is no 'console' mode.

---

### Post by ChipGibblets on 2011-10-14
> **collisionystm said:**
> try XRDP
 
sudo apt-get install xrdp
 
Lets you RDP to your server instead of VNC.
 
NOTE: You will not get the same desktop you get when at the keyboard and mouse. To my knowledge there is no 'console' mode.
 
Awesome.  Will do.  Now will I still use tightVNC on my client machine to get GUI or does XRDP have it's own?  Thank you for the help!

---

### Post by ArcherB on 2011-10-16
I added:

```
startxfce4 &
```

to my xstartup file in my ~/.vnc folder...

Of course, you have to xfce4 installed, but that's an easy matter.

---

### Post by scorp123 on 2011-10-16
> **ChipGibblets said:**
>  NOW I only get a grey screen in TightVNC and I don't know why...
  Are you sure you're launching any window manager or DE via VNC? Because if you're not ... then yes, all you get is a grey screen.

You should check what exactly --if anything at all-- gets started once you launch VNC!

So you'd launch VNC .... then remotely via Putty check what's running: ```
ps -efH
```

What you should be looking for is something like this (example from one of my systems):

```
sysadm      26205     1  0 Oct13 ?        00:03:13   Xvnc4 :1 -desktop sgd:1 (sysadm) -auth /home/sysadm/.Xauthority -geometry 1200x768 -depth 16 -rfbwait 30000 -rfbau
sysadm      26217     1  0 Oct13 ?        00:00:00   vncconfig -nowin
sysadm      26219     1  0 Oct13 ?        00:00:04   lxterminal
sysadm      26281 26219  0 Oct13 ?        00:00:00     gnome-pty-helper
sysadm      26282 26219  0 Oct13 pts/2    00:00:00     /bin/bash
sysadm      26220     1  0 Oct13 ?        00:25:36   transmission-gtk
sysadm      26221     1  0 Oct13 ?        00:00:00   lxsession
sysadm      26239 26221  0 Oct13 ?        00:00:03     openbox --config-file /openbox/lxde-rc.xml
sysadm      26242 26221  0 Oct13 ?        00:00:08     xscreensaver -no-splash
sysadm      26243 26221  0 Oct13 ?        00:05:59     lxpanel --profile LXDE
sysadm      26246 26221  0 Oct13 ?        00:00:02     pcmanfm --desktop --profile LXDE
```

Here the listing and the sequence of process ID's (PID's) tells us that VNC indeed did get started (process **Xvnc4**) and that it triggered several other programs (lxterminal, transmission) and then a LXDE session (lxsession).

My script for that looks like this (**~/.vnc/xstartup**):

```
#!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -nowin &
lxterminal &
transmission-gtk &
lxsession &
```

With this I get a LXDE session running inside VNC. It's fast (no unnecessary animations and stuff) even when executed remotely.

GNOME is still functional e.g. when I login locally.

---

