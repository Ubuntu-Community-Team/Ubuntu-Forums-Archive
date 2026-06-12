---
title: "Disabling Guest Session.. Security / Privacy risk"
date: 2011-09-14
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by alanrburns on 2011-09-14
Hi I'm hoping this is quick and easy.

Is there a way to disable Guest Session (in the GUI) in Oneiric
i found the below... but it makes no sense because there is no (System > Administration > Users and Groups) in Unity

[http://www.linuxbsdos.com/2010/10/18/guest-session-and-guest-user-accounts-in-ubuntu/](http://www.linuxbsdos.com/2010/10/18/guest-session-and-guest-user-accounts-in-ubuntu/)

 the Users and Groups graphical management utility (System > Administration > Users and Groups)

Thanks :)

---

### Post by cariboo on 2011-09-14
Aside from a permission problem right now, what security issues do think the guest account creates. I would think if you are worried about security, you'd want others that use your computer to use the guest account instead of your main account.

To disable the guest account login, on lightdm, open /etc/lightdm/lightdm.conf and set the guest account o false:

```
[GuestAccount]
enabled=false
username=guest
setup-script=/usr/share/lightdm/guest-session/guest-session-setup.sh
cleanup-script=/usr/share/lightdm/guest-session/guest-session-cleanup.sh
```

---

### Post by clanlaw on 2011-09-15
All I see in /etc/lightdm/lightdm.conf is

```
[SeatDefaults]
greeter-session=unity-greeter
user-session=ubuntu
```

---

### Post by mrkennie on 2011-09-17
I've had a quick glance at the source code and I can't seem to find anything to that would indicate that guest sessions are configurable right now. I've asked the same question on LP ([https://answers.launchpad.net/lightdm/+question/171471](https://answers.launchpad.net/lightdm/+question/171471)) but I'm not holding my breath on this one.

It does seem to pose a problem though, I guess the only solution for now is to switch back to gdm until lightdm becomes configurable (again?).

---

### Post by wrffr on 2011-09-19
> **cariboo907 said:**
> Aside from a permission problem right now, what security issues do think the guest account creates. I would think if you are worried about security, you'd want others that use your computer to use the guest account instead of your main account.

What "others that use my computer"?  The only people who have permission to use my various computers have their own accounts.

I certainly don't appreciate the default configuration allowing anyone who sits down at my computer to login and run arbitrary code without even going through the trouble to reboot and mess with the grub command line.  

Allowing login with no password by default is a stupid idea that unnecessarily widens the attack surface.

---

### Post by yooozy on 2011-09-19
> **clanlaw said:**
> All I see in /etc/lightdm/lightdm.conf is

```
[SeatDefaults]
greeter-session=unity-greeter
user-session=ubuntu
```
same here!
is there another way?

---

### Post by mrkennie on 2011-09-22
> **wrffr said:**
> What "others that use my computer"?  The only people who have permission to use my various computers have their own accounts.

I certainly don't appreciate the default configuration allowing anyone who sits down at my computer to login and run arbitrary code without even going through the trouble to reboot and mess with the grub command line.  

Allowing login with no password by default is a stupid idea that unnecessarily widens the attack surface.

Indeed. I believe the only alternative is ```
dpkg-reconfigure gdm
``` Select GDM then ```
apt-get remove gdm-guest-session
```

Shame because lightdm looks pretty slick.

---

### Post by jbicha on 2011-09-22
Here's my /etc/lightdm/lightdm.conf and guest is disabled with this:

```

[SeatDefaults]
greeter-session=unity-greeter
user-session=ubuntu
allow-guest=false

```

---

### Post by mrkennie on 2011-09-22
> **jbicha said:**
> Here's my /etc/lightdm/lightdm.conf and guest is disabled with this:

```

[SeatDefaults]
greeter-session=unity-greeter
user-session=ubuntu
allow-guest=false

```

Yup, that works. Would be nice if documentation existed for it though.

---

### Post by mrkennie on 2011-09-23
Turns out I never looked at the source properly. There's an example config in there which includes the following:
```

#
# General configuration
#
# start-default-seat = True to always start one seat if none are defined in the configuration
# greeter-user = User to run greeter as
# minimum-display-number = Minimum display number to use for X servers
# minimum-vt = First VT to run displays on
# user-authority-in-system-dir = True if session authority should be in the system location
# guest-account-script = Script to be run to setup guest account
# log-directory = Directory to log information to
# run-directory = Directory to put running state in
# cache-directory = Directory to cache to
# xsessions-directory = Directory to find X sessions
# xgreeters-directory = Directory to find X greeters
#
[LightDM]
#start-default-seat=true
#greeter-user=lightdm
#minimum-display-number=0
#minimum-vt=7
#user-authority-in-system-dir=false
#guest-account-script=guest-account
#log-directory=/var/log/lightdm
#run-directory=/var/run/lightdm
#cache-directory=/var/cache/lightdm
#xsessions-directory=/usr/share/xsessions
#xgreeters-directory=/usr/share/xgreeters

#
# Seat defaults
#
# xserver-command = X server command to run
# xserver-layout = Layout to pass to X server
# xserver-config = Config file to pass to X server
# xdmcp-manager = XDMCP manager to connect to
# xdmcp-port = XDMCP UDP/IP port to communicate on
# xdmcp-key = Authentication key to use for XDM-AUTHENTICATION-1 (stored in keys.conf)
# greeter-session = Session to load for greeter
# greeter-hide-users = True to hide the user list
# user-session = Session to load for users
# allow-guest = True if guest login is allowed
# guest-session = Session to load for guests (overrides user-session)
# session-wrapper = Wrapper script to run session with
# display-setup-script = Script to run when starting a greeter session (runs as root)
# greeter-setup-script = Script to run when starting a greeter (runs as root)
# session-setup-script = Script to run when starting a user session (runs as root)
# session-cleanup-script = Script to run when quitting a user session (runs as root)
# autologin-guest = True to log in as guest by default
# autologin-user = User to log in with by default (overrides autologin-guest)
# autologin-user-timeout = Number of seconds to wait before loading default user
# autologin-session = Session to load for automatic login (overrides user-session)
# exit-on-failure = True if the daemon should exit if this seat fails
#
[SeatDefaults]
#xserver-command=X
#xserver-layout=
#xserver-config=
#xdmcp-manager=
#xdmcp-port=177
#xdmcp-key=
#greeter-session=example-gtk-gnome
#greeter-hide-users=false
#user-session=default
#allow-guest=true
#guest-session=UNIMPLEMENTED
#session-wrapper=lightdm-session
#display-setup-script=
#greeter-setup-script=
#session-setup-script=
#session-cleanup-script=
#autologin-guest=false
#autologin-user=
#autologin-user-timeout=0
#autologin-session=UNIMPLEMENTED
#exit-on-failure=false

#
# Seat configuration
#
# Each seat must start with "Seat:".
# Uses settings from [SeatDefaults], any of these can be overriden by setting them in this section.
#
#[Seat:0]

#
# XDMCP Server configuration
#
# enabled = True if XDMCP connections should be allowed
# port = UDP/IP port to listen for connections on
# key = Authentication key to use for XDM-AUTHENTICATION-1 or blank to not use authentication (stored in keys.conf)
#
# The authentication key is a 56 bit DES key specified in hex as 0xnnnnnnnnnnnnnn.  Alternatively
# it can be a word and the first 7 characters are used as the key.
#
[XDMCPServer]
#enabled=false
#port=177
#key=

#
# VNC Server configuration
#
# enabled = True if VNC connections should be allowed
# port = TCP/IP port to listen for connections on
#
[VNCServer]
#enabled=false
#port=5900
```

Of course, allow-guest is in there :oops:

---

