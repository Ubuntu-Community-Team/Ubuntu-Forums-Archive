---
title: "remoting into vncserver presents gray screen"
date: 2021-07-30
forum: New to Ubuntu
---

### Post by sniper8752 on 2021-07-30
When I remote into my local Ubuntu Server (20), all I see is this gray screen.  How do I resolve this so I can remotely access/control the server via a desktop environment?

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288897&stc=1[/IMG]

---

### Post by TheFu on 2021-07-30
That is the root window for X/Windows.  You need to run a window manager or DE at this point.

Or better, dump VNC-whatever and use x2go which is 2-3x faster and 1000x more secure since it uses ssh-tunnels as part of the NX protocol.

---

### Post by ActionParsnip on 2021-07-31
This is a good guide
[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04)

But first, what are you wanting to do on the remote system once you get connected? Why set up VNC? Yes it's for remote access but what activities will you be doing on the desktop once connected? There may be a sleeker solution to what you want to do.

---

### Post by sniper8752 on 2021-07-31
I was actually following this guide: [https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-20-04).
I installed the default Ubuntu DE, which I believe is gnome.
Here is my xstartup file:
```
[FONT=monospace][COLOR=#000000]#!/bin/sh[/COLOR]

xrdb $HOME/.Xresources
xsetroot -solid grey
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
# Fix to make GNOME work
export XKL_XMODMAP_DISABLE=1
/etc/X11/Xsession
# Added by me. 
startx
gnome-session

[/FONT]
```
After this attempt, it still doesn't work.  
I am trying to remote into it to manage my VirtualBox VMs.

---

### Post by TheFu on 2021-07-31
```
xsetroot -solid grey
```

That is why you see a gray screen.

I don't think gnome3 works with vnc.  Use openbox to start.

The way I'm positive will work,
start an **xterm** in the file above. There won't be any window decorations.
Inside the xterm, run **openbox &**

If you want remote anagement of VMs,
Use kvm/qemu with libvirt.
setup ssh with shh-keys for authentication.
From your workstation, run virt-manager.  Configure the connection to the remote VM host with ssh+qemu and SPICE.

Enjoy near native performance.

Or just use ssh x-forwarding to run the program. this can't be used for a remote desktop, but any normal application should work fine.   

$ ssh -X  user@remote command &

```
ssh -X thefu@hadar virt-manager &
```
i don't use vbox. Perhaps that command will work?

---

### Post by ActionParsnip on 2021-07-31
Use LXDE or XFCE but why the VNC connection at all?....

---

### Post by sniper8752 on 2021-07-31
How else would I remote into it?  I don't want to have to sit in front of it.

---

### Post by TheFu on 2021-07-31
> **sniper8752 said:**
> How else would I remote into it?  I don't want to have to sit in front of it.

VNC is the worst of all possible answers.
ssh is the best, but it is a text interface by default.  

That isn't to say that ssh can't make running remote GUI applications easy.  I do it all day, every day.  Right now, the system I'm using is running a light WM with 2 local terminals.  Then there are about 15 other windows, each running on different systems. Those GUI windows just happen to be displayed on my light-desktop.  X/Windows is network aware and has been since the 1980s.  This browser window I'm using right now to type a reply is running on the different system, through an ssh-tunnel using the built-in X11-forwarded that ssh has supported for about 25 yrs.  It is like running the program locally.  All the traffic to display the Firefox browser gets tunneled through an encrypted ssh connection.  My local system is running an X/server and firefox running on the remote system is the X/client.  X/Windows has a client/server architecture, but it is opposite almost every other client/server system used in the world.
For example, I can run almost any GUI program remotely through an X-Forward tunnel - or even a remote shell - and then launch GUI programs on the remote system, but have each of those remote GUI program windows display on my local box.  This is how Unix gurus work and have worked for 25+ yrs.

**VNC and RDP are clunky in comparison.**

The negative for X-Forwarding is that X/Windows doesn't attempt to be network efficient, so performance at startup can take a few seconds to load on slower networks.  OTOH, having each program, regardless of where it is actually running, appear like a local application is extremely convenient.  Any program that doesn't need direct GPU access will work.  That's like 50,000 programs ... and the only price to make it work is ssh.

For example, if I want an terminal on a different system, regulus, I'll run:
```
xterm -geometry 80x25+2+670 -u8 -fs 12 -fa Monospace -sb -fg green -bg black -e ssh -X regulus &
```
From that terminal, I can launch anything except a window manager.
The simplified version for that command is:
```
xterm  -e ssh -X regulus &
```

If I want to run thunderbird (an email program), I'll use ... 
```
ssh -X thefu@regulus "firejail thunderbird " &
```
Thunderbird is made by the people who make firefox browser.  Browsers and email programs are security risks, so I run it inside a firejail sandbox.  firejail and thundbird are both installed on regulus in the normal way.

Another example.
```
ssh -X thefu@regulus "libreoffice" &
```
Or if I already have a terminal on regulus with x11-forwarding (the -X option to ssh), then I'd just run:
```
libreoffice &
```
and a few seconds later the full libreOffice GUI will pop open on my desktop.

Then there is the last option for remote desktops, x2go. That uses the NX protocol which merges highly compressed vnc with ssh tunneling and works much like vnc or rdp, but with 1,000 better security and 2-3x better performance.  I've used x2go from 5 continents to remote into my home desktop. I have control over how much compression gets used, but password-less ssh authentication is used.  Compared to vnc or rdp, it is like night and day.  x2go is day.  Because it uses a full remote desktop, it doesn't work with gnome3 or later.  Gnome3 is too heavy and really wants direct access to a GPU.  x2go works very well with Mate, LXQt, LXDE, XFCE, and KDE setups, however.

Everything I've listed above is F/LOSS, so no commercial license needed.

I feel bad with people from Windows backgrounds come to Linux and are missing this basic knowledge because they've never been exposed to it.  It really is a lack in capability that MS-Windows has.  Plus, if you were to watch me work on my desktop, you probably wouldn't be able to tell which windows were running local and which are remote.  If you watched any long time Unix person, that would be the same. We all do this. It is how we work.

For fun, I've run a remote desktop into a remote desktop into a remote desktop.  A few years ago, when I used Win7 Media Center to record TV shows, I'd use x2go while traveling to remote into my Linux desktop back home, then use rdp from that desktop onto the Win7 machine to enable recording of a TV show I'd forgot to schedule for recording.  Because x2go uses ssh, I was confident in the security of the connection.

Aside:
There are a few Unix tools that everyone should master. Here's a short list:
[LIST]
[*]ssh / scp / sftp
[*]rsync
[*]bash
[/LIST]
**ssh** is freakin' amazing.  It supports encrypted connectivity between systems. Suitable for LAN or internet connections. Use an elliptical ssh-key and no known national security organization anywhere in the world can crack it. Never use password authentication over any untrusted network, including wifi in your home.  ssh can be for remote commands, hoping from system to system to system around the world or configuring stuff on 5-50,000 systems using a tool like ansible. Ansible uses ssh to authenticated connectivity.  ssh is the base way that all my systems communicate.  There are so many capabilities that ssh provides, it has a dedicated book.  [https://www.oreilly.com/library/view/ssh-the-secure/0596008953/](https://www.oreilly.com/library/view/ssh-the-secure/0596008953/), but learning the 20 basic things that ssh can do is normally enough.  A quick example, I use it as a SOCKS5 proxy into my home network when I just want a quick browser VPN, but don't want to startup a full VPN connection.

**rsync** leverages ssh connections to efficiently transfer and maintain copies of files between 1 or more systems.  It is dropbox, but we've had it for 30 yrs.

**bash** is a nice, capable, scripting language for simple needs. Learn your shell, which is probably bash, and working efficiently will skyrocket. When you open a terminal, that text interface is almost always bash accepting commands.

---

### Post by him610 on 2021-08-01
You may want to consider cockpit. [https://cockpit-project.org/]("https://cockpit-project.org/")
```

$ apt show cockpit -a
Package: cockpit
Version: 248-1~ubuntu20.04.1
Priority: optional
Section: universe/admin
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Utopia Maintenance Team <pkg-utopia-maintainers@lists.alioth.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 66.6 kB
Depends: cockpit-bridge (>= 248-1~ubuntu20.04.1), cockpit-ws (>= 248-1~ubuntu20.04.1), cockpit-system (>= 248-1~ubuntu20.04.1)
Recommends: cockpit-storaged (>= 248-1~ubuntu20.04.1), cockpit-networkmanager (>= 248-1~ubuntu20.04.1), cockpit-packagekit (>= 248-1~ubuntu20.04.1)
Suggests: cockpit-doc (>= 248-1~ubuntu20.04.1), cockpit-pcp (>= 248-1~ubuntu20.04.1), xdg-utils
Homepage: https://cockpit-project.org/
Download-Size: 18.9 kB
APT-Sources: http://us.archive.ubuntu.com/ubuntu focal-backports/universe amd64 Packages
Description: Web Console for Linux servers
 The Cockpit Web Console enables users to administer GNU/Linux servers using a
 web browser.
 .
 It offers network configuration, log inspection, diagnostic reports, SELinux
 troubleshooting, interactive command-line sessions, and more.

Package: cockpit
Version: 215-1
Priority: optional
Section: universe/admin
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Utopia Maintenance Team <pkg-utopia-maintainers@lists.alioth.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 63.5 kB
Depends: cockpit-bridge (>= 215-1), cockpit-ws (>= 215-1), cockpit-system (>= 215-1)
Recommends: cockpit-storaged (>= 215-1), cockpit-networkmanager (>= 215-1), cockpit-dashboard (>= 215-1), cockpit-packagekit (>= 215-1)
Suggests: cockpit-doc (>= 215-1), cockpit-pcp (>= 215-1), cockpit-machines (>= 215-1), xdg-utils
Homepage: https://cockpit-project.org/
Download-Size: 18.0 kB
APT-Manual-Installed: yes
APT-Sources: http://us.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
Description: Web Console for Linux servers
 The Cockpit Web Console enables users to administer GNU/Linux servers using a
 web browser.
 .
 It offers network configuration, log inspection, diagnostic reports, SELinux
 troubleshooting, interactive command-line sessions, and more.

```

---

