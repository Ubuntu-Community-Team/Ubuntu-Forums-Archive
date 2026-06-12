---
title: "Failed to start Load Kernel Modules - CDEmu and vhba problems"
date: 2017-03-26
forum: New to Ubuntu
---

### Post by zappologia on 2017-03-26
Hi everybody,

in these days I was trying to install the .iso images loader software CDEmu.

After installing it on Ubuntu 16.04 I was not able to start the daemon because of an error notified me by the software with a window, so I decided to uninstall it form my PC.

Uninstalled the software, by removing the packages:
gcdemu
vhba-dkms
libmirage10
cdemu-daemon
 cdemu-client

Unfortunately, during the first reboot, I read the following error:


[[COLOR=#ff0000]FAILED[/COLOR]] Failed to start Load Kernel Modules
See 'systemctl status systemd-modules-load.service' for details


After some researches on system files I found that the problem was the **vhba** module.
How to fix it?

After uninstalling all the CDEmu software, including the vhba module, a file remains on your PC causing this error.
Just delete it through the command:

[B][I]sudo rm /etc/modules-load.d/vhba.conf
[/I][/B]then, as you prefere,[B][I]
sudo reboot
[/I][/B]

That's it!
simone

---

