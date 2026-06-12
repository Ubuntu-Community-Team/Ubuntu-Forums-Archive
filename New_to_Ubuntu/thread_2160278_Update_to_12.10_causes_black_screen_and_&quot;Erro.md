---
title: "Update to 12.10 causes black screen and &quot;Error inserting nvidia_current&quot;"
date: 2013-07-06
forum: New to Ubuntu
---

### Post by SpriteGoblin on 2013-07-06
Hi,

I have recently installed Ubuntu 12.04 on my [Sony Vaio VGN-NW11s]("http://www.sony.co.uk/support/en/product/VGN-NW11S_S/specifications") using the [Windows Installer]("http://www.ubuntu.com/download/desktop/install-ubuntu-with-windows") (the laptop came with Windows 7 a while ago..). Since then I have setup my development environment without any problem until I tried to upgrade to Ubuntu 12.10. After the update had completed it rebooted and now, when Ubuntu loads the screen turns purple for a few seconds and then it goes completely black (even if left for 20mins+).

I will list the steps I followed to get into command line mode incase anyone else has a similar issue (apologies if its a little obvious):
[LIST]
[*]In the Windows Boot Manager, select "Ubuntu" then hold down "shift."
[*]In the GNU Grub Menu, select "Advanced options for Ubuntu".
[*]In the next menu, select "Ubuntu, with Linux 3.5.0-36-generic (recovery mode)". This will load a proper old-school menu.
[*]When the Recovery Mode menu loads, select "resume".
[*]In command line, enter the username and password when prompted.
[/LIST]

Here is what I have tried so far:
[LIST]
[*]Running 'startx' causes the following error:
[/LIST]
[INDENT=2]FATAL: Error inserting nvidia_current (/lib/modules/3.5..0-36-generic/updates/dkms/nvidia_current.ko): No such device

Fatal server error:
no screens found
(EE)
Please consult the The X.Org Foundation support[/INDENT]
[INDENT=3]at [http://wiki.x.org](http://wiki.x.org)[/INDENT]
[INDENT=2] for help.
(EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
(EE)
Server terminated with error (1). Closing log file.
xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error[/INDENT]

[LIST]
[*]Running 'more "/var/log/Xorg.0.log" | grep error' shows:
[/LIST]
[INDENT=2](WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[227.326] (EE) NVIDIA: system's kernel log for additional error messages.
[227.326] (EE) Failed to load module "nvidia" (module-specific error, 0)
Fatal server error:[/INDENT]

Please can someone help me resolve this issue. 

I am new to Ubuntu however I'm a developer and I'm no stranger to the command line so any potential solutions are welcome.

SpriteGoblin1101

---

### Post by SpriteGoblin on 2013-07-07
Hi,

I gave up and re-installed Ubuntu 12.04. :( It looks like 12.10 no longer supports my graphics card.

Thanks anyway.

SpriteGoblin1101

---

