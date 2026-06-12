---
title: "how to remove the light display manger from the ubuntu 13.10 logon screen"
date: 2013-10-20
forum: New to Ubuntu
---

### Post by rburkartjo on 2013-10-20
any ideas. really stupid to have added that option to the logon screen. tks

---

### Post by Jonathan Precise on 2013-10-20
Which DM do you want? GDM? XDM (probably not)? KDM? LXDM (probably)...

Example: LXDM

```
sudo apt-get install lxdm
```

In the [FONT=Courier New]Do you want to continue? [Y/n]: [/FONT] prompt, [SIZE=4]**MAKE SURE UBUNTU-DESKTOP IS NOT SET FOR DELETION**[/SIZE], then put in Y to continue.

A colored text prompt will appear, which will ask you to choose the default DM Choose gdm or "Gnome Display Manager" or similar option.

Wait.............

DONE!!!

[HR][/HR]

If you already have the DM installed, then [FONT=Courier New]dpkg-reconfigure ***display-manager-package-name***[/FONT]

Example: GDM

```
dpkg-reconfigure gdm
```

A colored text prompt will appear, which will ask you to choose the default DM Choose gdm or "Gnome Display Manager" or similar option.

Wait...............

DONE!!!

---

### Post by steeldriver on 2013-10-20
I think the OP is referring to this bug ["Light Display Manager" is offered as login option]("https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/1235785")

The suggested workaround is to add the lightdm account to the list of hidden-users explicitly by editing your /etc/lightdm/lightdm.conf file i.e.

```
[UserAccounts]
minimum-uid=500
**hidden-users**=nobody nobody4 noaccess [COLOR=#0000ff]**lightdm**[/COLOR]
hidden-shells=/bin/false /usr/sbin/nologin
```

---

### Post by rburkartjo on 2013-10-20
tks. steel that didnt work but tks  lightdm session still is displayed at logon. joha i ran sudo dpkg-reconfigure gdm and changed it to gdm. sure 
fix for lightdm appearing on logon screen will be released.

---

### Post by rburkartjo on 2013-11-07
at least on my end the ldm problem was fixed up updates.

---

### Post by cessanfrancisco on 2013-11-08
I had that problem when I first installed Ubuntu 13.10.  I noticed it but didn't think much of it.

Then I had some other issues that required a fresh re-install.  Note:  When I first installed Ubuntu 13.10, on a Lenovo Z530, I installed under a BIOS setting called, "Other OS" which is described by BIOS as "Pure Legacy Mode."

So when I reinstalled I used the "Win8 64bit" setting instead, which is described, again by BIOS, as "Pure UEFI Mode."  Once I did that, no more "Light Display Manager" at log-in screen.  

Odd, huh?

---

