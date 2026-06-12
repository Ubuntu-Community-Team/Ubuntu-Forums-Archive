---
title: "Screen sharing using command line"
date: 2021-04-26
forum: New to Ubuntu
---

### Post by sul on 2021-04-26
Hi,

I recently installed Ubuntu LTS 20.04.02 and was able to turn on Screen Sharing under Settings using the GUI--works well.  However, is there a way to do this using command line, rather than GUI?

thank you,

-sul

---

### Post by kckit on 2021-04-26
never mind

---

### Post by ActionParsnip on 2021-04-26
Did you resolve the issue? If so can you please share the solution as it may help others

---

### Post by TheFu on 2021-04-26
Use **x2go** if you want a remote desktop. [https://wiki.x2go.org/doku.php/doc:usage:desktop-sharing](https://wiki.x2go.org/doku.php/doc:usage:desktop-sharing)

Use **tmux** or **screen** if you want to share a terminal with other people.
[https://www.howtoforge.com/sharing-terminal-sessions-with-tmux-and-screen](https://www.howtoforge.com/sharing-terminal-sessions-with-tmux-and-screen)

---

### Post by sul on 2021-04-27
no resolution as yet.  I am still waiting on an answer to the question.

---

### Post by sul on 2021-04-27
thanks for the tip.  x2go client is very unstable on windows 10.  session opens a black screen and simply closes--no error message is displayed.

---

### Post by scorp123 on 2021-04-28
> **sul said:**
> thanks for the tip.  x2go client is very unstable on windows 10.  

Can't confirm this at all, I use it daily.  Did you properly configure both sides (e.g. "**x2goserver**" is installed + running on the Linux side) and e.g. select a desktop environment that's installed on the Linux side?

---

### Post by scorp123 on 2021-04-28
> **sul said:**
>  However, is there a way to do this using command line, rather than GUI? 

Totally **NOT RECOMMENDED** method because this relies on an unsafe and easy hackable protocol (VNC), but if you have the GNOME desktop you can try this command:
```
/usr/lib/vino/vino-server --display=:0
```

It should default to the settings you have defined previously, e.g. when you activated it using the desktop.

---

### Post by sul on 2021-04-28
> **scorp123 said:**
> Totally **NOT RECOMMENDED** method because this relies on an unsafe and easy hackable protocol (VNC), but if you have the GNOME desktop you can try this command:
```
/usr/lib/vino/vino-server --display=:0
```

It should default to the settings you have defined previously, e.g. when you activated it using the desktop.

Thank you but no joy for me.  it results in error:

```
Unable to init server: Could not connect: Connection refused
Cannot open display: :0
```

I'm using ssh (putty) on my windows pc.  Looks like vino requires logging into the desktop environment of the physical machine for this command to work.  Unfortunately, this doesn't help my situation.

-sul.

---

### Post by TheFu on 2021-04-28
> **sul said:**
> Thank you but no joy for me.  it results in error:

```
Unable to init server: Could not connect: Connection refused
Cannot open display: :0
```

I'm using ssh (putty) on my windows pc.  Looks like vino requires logging into the desktop environment of the physical machine for this command to work.  Unfortunately, this doesn't help my situation.

-sul.

With x2go, you don't need putty.  Also, the x2goclient accepts pointing at a profile, which can be configured using ssh-keys (use the x2go version, not putty's version) for trusted connections.  I've never used Win10, but on prior versions, x2go was solid for weeks.  I'd be surprised if that wasn't still the situation. Leads me to think there is an issue on your system or a fundamental misunderstanding about how things need to be setup.  

After using x2go, very few people would want to return to using RDP or VNC-based tools if they don't have other mandates. x2go is much faster and can be tuned for the speed of the network and both systems.

---

### Post by sul on 2021-04-28
> **scorp123 said:**
> Can't confirm this at all, I use it daily.  Did you properly configure both sides (e.g. "**x2goserver**" is installed + running on the Linux side) and e.g. select a desktop environment that's installed on the Linux side?

Thanks.  I followed instructions carefully on x2go wiki.  I'm on a default install of ubuntu 20.04 LTS with Gnome desktop and so I'm selecting GNOME on the client.  The client goes through the motions of authenticating with the server and opens a black window followed by a splash screen that looks like a large X2GO sign for about a second and then the window simply closes.

Thanks!

-s.

---

### Post by TheFu on 2021-04-28
Gnome3 is very bloated and really, really, wants direct hardware access to the GPU, IME.  Best to use **any** other DE or just use a Window Manager setup instead.  Other DEs - XFCE, LXQt, KDE, Mate, Cinnamon, .... 

Also, in the profile for the connection inside the x2go-client, ensure that the DE/WM used is selected.
Also, it is best to have ssh-keys already setup between the client and the server before using x2go. This will allow password-less connections, except to unlock the ssh keys first thing in the morning.

---

### Post by sul on 2021-04-28
> **TheFu said:**
> Gnome3 is very bloated and really, really, wants direct hardware access to the GPU, IME.  Best to use **any** other DE or just use a Window Manager setup instead.  Other DEs - XFCE, LXQt, KDE, Mate, Cinnamon, .... 

Also, in the profile for the connection inside the x2go-client, ensure that the DE/WM used is selected.
Also, it is best to have ssh-keys already setup between the client and the server before using x2go. This will allow password-less connections, except to unlock the ssh keys first thing in the morning.

Thanks!  I appreciate the advice.  Unfortunately, at this time I prefer something that works well with Gnome3.  Hopefully x2go will get there someday soon--I think it's got a lot of promise otherwise.

best-

-s

---

### Post by TheFu on 2021-04-28
> **sul said:**
> Thanks!  I appreciate the advice.  Unfortunately, at this time I prefer something that works well with Gnome3.  Hopefully x2go will get there someday soon--I think it's got a lot of promise otherwise.

best-

-s

Doubtful.  **It is a gnome issue, not x2go.**  Actually, I just setup a minimal 21.04 gnome system 3 days ago. With Spice protocol, it flies, but spice only works for KVM VMs, not on physical hardware.  I'll try x2go ...
```
sudo apt install x2goserver
```
from an 18.04 x2goclient ...   the connection worked, but there was a GUI failure. Looks like Wayland is the problem. Confirmed.  Seems wayland doesn't like x2go. Disabled wayland [https://linuxconfig.org/how-to-enable-disable-wayland-on-ubuntu-20-04-desktop](https://linuxconfig.org/how-to-enable-disable-wayland-on-ubuntu-20-04-desktop) and my WM login works, but Gnome still does not.

If you are set on Gnome3 ... **Screen Sharing** is clearly running a program with some options. .desktop files are the normal way for menu programs. Those are just text files. Find the one used in the menu, look inside for the command.  I couldn't find that program on 21.04 and don't know how to use gnome DE to figure it out. sorry for my ignorance.
```
$ locate .desktop |grep -i shari
/etc/xdg/autostart/org.gnome.SettingsDaemon.Sharing.desktop
/usr/share/applications/gnome-sharing-panel.desktop
```
is all I found. Alas, I have a minimal install.
[https://help.gnome.org/users/gnome-help/stable/sharing-desktop.html.en](https://help.gnome.org/users/gnome-help/stable/sharing-desktop.html.en)

---

### Post by scorp123 on 2021-04-28
> **TheFu said:**
>  If you are set on Gnome3 ... **Screen Sharing** is clearly running a program with some options. 

See my post above. GNOME is using "vino", which is essentially a VNC server.

```
 > apt info vino
Package: vino
Version: 3.22.0-5ubuntu2.2
Priority: optional
Section: gnome
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 414 kB
Depends: libavahi-client3 (>= 0.6.16), libavahi-common3 (>= 0.6.16), libavahi-glib1 (>= 0.6.16), libc6 (>= 2.15), libcairo2 (>= 1.10.0), libgcrypt20 (>= 1.8.0), libglib2.0-0 (>= 2.37.3), libgnutls30 (>= 3.6.12), libgtk-3-0 (>= 3.0.0), libice6 (>= 1:1.0.0), libjpeg8 (>= 8c), libminiupnpc17 (>= 1.9.20140610), libnotify4 (>= 0.7.0), libsecret-1-0 (>= 0.7), libsm6, libx11-6, libxdamage1 (>= 1:1.1), libxext6, libxfixes3, libxtst6, zlib1g (>= 1:1.1.4), dconf-gsettings-backend | gsettings-backend
Recommends: gvfs
Suggests: gnome-control-center
Breaks: gnome-control-center (<< 1:3.13.2)
Homepage: https://wiki.gnome.org/Projects/Vino
Task: ubuntu-desktop, ubuntu-budgie-desktop
Download-Size: 126 kB
APT-Manual-Installed: no
APT-Sources: http://ch.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages
Description: VNC server for GNOME
 VNC is a protocol that allows remote display of a user's desktop. This
 package provides a VNC server that integrates with GNOME, allowing you
 to export your running desktop to another computer for remote use or
 diagnosis.
```

```
> dpkg -L vino
/.
/usr
/usr/lib
/usr/lib/systemd
/usr/lib/systemd/user
/usr/lib/systemd/user/vino-server.service
/usr/lib/vino
/usr/lib/vino/vino-server
/usr/share
/usr/share/applications
/usr/share/applications/vino-server.desktop
/usr/share/doc
/usr/share/doc/vino
/usr/share/doc/vino/AUTHORS
/usr/share/doc/vino/NEWS.gz
/usr/share/doc/vino/README
/usr/share/doc/vino/changelog.Debian.gz
/usr/share/doc/vino/copyright
/usr/share/glib-2.0
/usr/share/glib-2.0/schemas
/usr/share/glib-2.0/schemas/org.gnome.Vino.enums.xml
/usr/share/glib-2.0/schemas/org.gnome.Vino.gschema.xml
```

And you can trigger it from the command line if you are already logged in, otherwise you'll run into an error about display :0 :
```
/usr/lib/vino/vino-server --display=:0
```

The package list mentions a "vino-server.service" for "systemd". Content of that file looke like this:
```
[Unit]
Description=Vino VNC server

[Service]
Type=dbus
BusName=org.gnome.Vino
ExecStart=/usr/lib/vino/vino-server
Restart=on-abnormal
```

That thing doesn't work though. But maybe it would be possible to get it working? I don't know.

There used to be instructions around the web like this one:
[https://www.jakeyoon.com/2008/11/19/enable-vino-vnc-server-for-login-manager-gdm-in-ubuntu/]("https://www.jakeyoon.com/2008/11/19/enable-vino-vnc-server-for-login-manager-gdm-in-ubuntu/")

... that would show you how to manually enable "vino-server" for GDM. But as far as I know GNOME was changed a lot and those instructions very likely no longer work.

So I wonder if there's a new way to get "vino-server" to work?

The other traditional way to have your GDM/ LightDM inside a VNC session would be to get "x11vnc" to work, as per:
[https://help.ubuntu.com/community/VNC/Servers#Have_x11vnc_automatically_start_in_Ubuntu]("https://help.ubuntu.com/community/VNC/Servers#Have_x11vnc_automatically_start_in_Ubuntu")

Again, not sure if those instructions still work.

---

### Post by scorp123 on 2021-04-28
> **sul said:**
> Thanks!  I appreciate the advice.  Unfortunately, at this time I prefer something that works well with Gnome3. 

I will very likely be heavily criticised for this ... but are commercial + free-for-private-use solutions an option for you? I think at this point something like **AnyDesk** would be easier for you to use.

**[COLOR="#FF0000"]Warning:[/COLOR]** 

please be aware that AnyDesk makes **[COLOR="#FF0000"]every of your computers it is installed on _REACHABLE_ on the Internet.[/COLOR]** In other words: People getting hacked, scammed and having their bank account, Amazon account etc. invaded is not unheard of. [COLOR="#FF0000"]**Your firewall WILL NOT protect you**[/COLOR] in this case because AnyDesk is designed to work around firewalls.

But yes, sure ... it is super easy to use.

Security advice you absolutely must follow so you don't get hacked via AnyDesk:

[LIST]
[*]never ever share any of your AnyDesk ID's with anyone!! (forum posts, screenshots, social media, etc. )
[*]select strong + complex passwords that are very hard to guess (use a "password generator" if need be!)
[*]Enable 2-Factor Authentication. The mechanism is there, it just needs to be enabled. Don't skip this!!
[/LIST]

With that out of the way:

AnyDesk installation via DEB repository:
[http://deb.anydesk.com/howto.html]("http://deb.anydesk.com/howto.html")

All commands listed there need to be executed as "root", e.g. you have to use "sudo" with every command they list above.

General installation instructions:
[https://support.anydesk.com/Installation]("https://support.anydesk.com/Installation")

Information that Wayland needs to be disabled for AnyDesk:
[https://support.anydesk.com/AnyDesk_on_Linux]("https://support.anydesk.com/AnyDesk_on_Linux")

The most important part:  2-Factor Authentication.  **[COLOR="#FF0000"]DON'T SKIP THIS.[/COLOR]**
[https://support.anydesk.com/Two-Factor_Authentication]("https://support.anydesk.com/Two-Factor_Authentication")

But yes, this is super easy to use and it works with GNOME 3.x too.

Now I need to wash my hands, I feel dirty :neutral:

---

