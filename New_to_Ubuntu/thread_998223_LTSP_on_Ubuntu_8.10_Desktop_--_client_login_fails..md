---
title: "LTSP on Ubuntu 8.10 Desktop -- client login fails."
date: 2008-11-30
forum: New to Ubuntu
---

### Post by JackVrouwes on 2008-11-30
_What happens:_ 
The first Ubuntu screen comes up when I boot the thin client from CD.  The progress bar remains motionless at about 10% completion for a long time before the Ubuntu "user" login screen comes up.  The "password" screen goes black and the "user" screen reappears each time I try to login as either superuser or another user.

_My question:_
I have read whatever I can find on this (old) subject. Can anybody help me? Please be gentle to this noob.  I am stumped -- I can see something is wrong with the gnome-keyring, but I don't know what to do about it.  Can somebody suggest in specific terms what I should try?

_My setup:_ 
There are two D-Link DFE-530TX+ nics in he server (AMD Athlon 1800+, 1.5M memory.) eth0 at addr 10.0.0.5, and eth19 at 192.168.0.1.  The diskless only client (AMD K6-2/500, 512 Kb memory) has an AOpen AON-325D nic.  The AOpen reports Realtek RTL8139 @0xe800.  The interconnection is with a crossover cable on eth19.  The server runs Ubuntu 8.10 desktop.  I installed LTSP per [https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall).  The client boot-CD contains the gpxe-0.9.6-rtl8139.iso image from rom-o-matic.  (note: I picked rtl8139:10ec8139 for NIC/ROM to generate the ROM image since nothing was mentioned about AOpen in [http://www.rom-o-matic.net/gpxe/gpxe-0.9.6/src/bin/NIC](http://www.rom-o-matic.net/gpxe/gpxe-0.9.6/src/bin/NIC).)

_What I tried so far:_  
**(1)** Verified normal interconnection both ways by pinging. (I used tomsrtbt on the diskless client, see [http://www.toms.net/rb/download.html](http://www.toms.net/rb/download.html))  
**(2)** Updated the SSH keys per [https://wiki.ubuntu.com/DebugThinClientLogin](https://wiki.ubuntu.com/DebugThinClientLogin). This did not resolve the problem.
**(3)** Checked authentication per [https://wiki.ubuntu.com/DebugThinClientLogin](https://wiki.ubuntu.com/DebugThinClientLogin). 
The output is here:
---------------------------------------------
Nov 27 13:17:04 happy sshd[4980]: Server listening on 0.0.0.0 port 22.
Nov 27 13:17:30 happy gdm[5516]: pam_unix(gdm:session): session opened for user jaap by (uid=0)
Nov 27 13:17:30 happy gdm[5516]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Nov 27 13:17:30 happy gdm[5516]: gnome-keyring-daemon: couldn't lookup keyring component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Nov 27 13:17:30 happy gdm[5516]: Autolaunch error: X11 initialization failed.
Nov 27 13:17:30 happy gdm[5516]: )gnome-keyring-daemon: couldn't lookup ssh component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Nov 27 13:17:30 happy gdm[5516]: Autolaunch error: X11 initialization failed.
Nov 27 13:17:30 happy gdm[5516]: )gnome-keyring-daemon: couldn't lookup pkcs11 component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Nov 27 13:17:30 happy gdm[5516]: Autolaunch error: X11 initialization failed.
Nov 27 13:17:30 happy gdm[5516]: )
Nov 27 13:17:30 happy gnome-keyring-daemon[5777]: Couldn't unlock login keyring with provided password
Nov 27 13:17:30 happy gnome-keyring-daemon[5777]: Failed to unlock login on startup
-----------------------------------------------------

**(4)** Checked file ".xsession-errors per [https://wiki.ubuntu.com/DebugThinClientLogin](https://wiki.ubuntu.com/DebugThinClientLogin).
The output is here:
---------------------------------------------
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Unable to create /home/jaap/.dbus/session-bus
x-session-manager[5788]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager'
Window manager warning: Failed to read saved session file /home/jaap/.config/metacity/sessions/1026ee04801ceb6576122781705635466400000057880007.ms: Failed to open file '/home/jaap/.config/metacity/sessions/1026ee04801ceb6576122781705635466400000057880007.ms': No such file or directory
Initializing nautilus-share extension
seahorse nautilus module initialized

** (nautilus:5890): WARNING **: Unable to add monitor: Not supported

(gnome-panel:5888): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -9 and height 24
Unable to open desktop file file:///home/jaap/Desktop/jws_app_shortcut_1184717311459.desktop for panel launcher: No such file or directory
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

x-session-manager[5788]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout


Tracker version 0.6.6 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at [http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Initialising tracker...
starting HAL detection for ac adaptors...none found
Failure: Module initalization failed

** (nm-applet:5946): WARNING **: No connections defined

** (nm-applet:5946): WARNING **: nm_client_get_devices: error getting devices: A security policy in place prevents this sender from sending this message to this recipient, see message bus configuration file (rejected message had interface "org.freedesktop.NetworkManager" member "GetDevices" error name "(unset)" destination "org.freedesktop.NetworkManager")

Throttle level is 0
5888
  PID TTY          TIME CMD
 5849 ?        00:00:00 pulseaudio
  PID TTY          TIME CMD
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
-------------------------------------------------------------

**(5)** I also tried to to set the root password on the thin client according to [https://help.ubuntu.com/community/EdubuntuFAQ#How%20do%20I%20set%20the%20root%20password%20on%20the%20thin%20clients?](https://help.ubuntu.com/community/EdubuntuFAQ#How%20do%20I%20set%20the%20root%20password%20on%20the%20thin%20clients?).  The result stumped me again.  What should I do with this?
-------------------------------------------------------------
jaap@happy:~$ sudo chroot /opt/ltsp/i386
[sudo] password for jaap: 
id: cannot find name for group ID 117
id: cannot find name for group ID 119
-------------------------------------------------------------

---

### Post by canthus13 on 2008-11-30
I don't know a whole lot about LTSP, but I noticed in some of the logs you posted that it seems like SAMBA needs to be installed...

--Me

---

### Post by JackVrouwes on 2008-12-01
> **canthus13 said:**
> I don't know a whole lot about LTSP, but I noticed in some of the logs you posted that it seems like SAMBA needs to be installed...

--Me

Thanks canthus13.  The protocols in LTSP are DHCP and tftp (trivial file transfer protocol) according to [http://floppsie.comp.glam.ac.uk/Glamorgan/gaius/networks/2.pdf](http://floppsie.comp.glam.ac.uk/Glamorgan/gaius/networks/2.pdf) . It does nowhere mention Samba.

Another good reference I found is [http://www.informit.com/articles/article.aspx?p=1186281&seqNum=2](http://www.informit.com/articles/article.aspx?p=1186281&seqNum=2) . This describes mainly Edubuntu.  I wonder if Edubuntu allows me to save my current Ubuntu desktop. However, this article seems to indicate that possibility. In that case, I may try that route instead of what I did before if I get totally stuck. I'll reread the article carefully.

Has anyone traveled that route successfully?

---

