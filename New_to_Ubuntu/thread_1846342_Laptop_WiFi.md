---
title: "Laptop WiFi"
date: 2011-09-18
forum: New to Ubuntu
---

### Post by McQue on 2011-09-18
All,

Noobie here.  Just installed Ubuntu 10.04 on my Dell Inspiron 1501.  WiFi did not come up so found howto at:

[http://www.ubuntu1501.com/2007/01/fixing-wifi-on-dell-1501.html](http://www.ubuntu1501.com/2007/01/fixing-wifi-on-dell-1501.html)

Had a more experienced friend help me and all went well, but on final reboot before "Step 5" I do not have the WiFi light and "Fn" + "F2" does not bring up the light and the "iwlist scanning" command produces the following:
```
root@mcque-lt:/home/mmcque# iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

```How do I now debug this?

All help appreciated!

Thanks!

McQUE

---

### Post by Lisiano on 2011-09-18
```
rfkill list all
```
Should show you if your WiFi card is blocked by a switch (Somewhere on the laptop itself) or by software. If software. Just type```
sudo rfkill unblock wifi
```
Also. Please take a look at System -> Administration -> Additional Drivers. Your WiFi driver might be listed there. Just pop in your Ubuntu CD, mark it using Software Sources in Administration and let it install the driver from the CD.

EDIT: DO NOT FOLLOW THAT GUIDE AS IS. That guide is outdated! Some practices shown in that guide are harmful for your Ubuntu experience!
Do not use sudo to start graphical applications. Only use gksu or gksudo for Gnome or kdesu or kdesudo for KDE. Using sudo for graphical applications will cause a lot of problems later on.
Using ndiswrapper is a last-resort method, most WiFi drivers are available from the CD or already installed from the Get-go.
Manually deleting files is a.. Excuse me for my language. Dumb idea. Use the Package manager instead, it deletes everything related to the application except for the configuration files. If you wish to remove them as well, use "purge" instead of "remove" (apt-get) or "Complete remove" instead of "Remove" (Synaptic)

---

### Post by McQue on 2011-09-18
Lisiano,

Thanks for the commands, but all the answers from the list are "no" and no change after running your second command.

My friend help with the install and we used ndiswrapper-1.56, but not sure if that is compatible with 10.04.

Which version do you suggest?

Always getting "Device not Ready" from the Network Manager pop-out, when trying to look for WiFi.

Thanks!

McQUE

---

### Post by Lisiano on 2011-09-18
I suggest not using ndiswrapper. For starters post the output of ```
lspci
``` so we know what adapter you have. If you know the model, also say it.

EDIT: It seems from the guide you posted above you have a BCM43xx. Try following this [http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

---

### Post by McQue on 2011-09-18
Lisianoi,

My friend and I ran command"

lspci | grep -i network

and got:

Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

I believe this was the controller specified in the HOWTO, and the build went OK, but nothing yet. 

We have the computer setup on his network hub (wired) so trying to debug through that.

If you want to go interactive with this, he set me up for irc.freenode.net with the #ubuntu channel, so can use that, if you like.

Thanks!

McQUE

---

### Post by wildmanne39 on 2011-09-18
Hi, uninstall ndiswrapper then run this command please:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
then disconnect your wired connection and restart your computer and it should be working if not post the results of this command here please;
```
lsmod
```
Thank you

---

### Post by Lisiano on 2011-09-18
I have resolved the issue with the OP in IRC, the fix was using System -> Administration -> Additional Drivers.

---

### Post by McQue on 2011-09-18
Lisiano,

Thanks for your help on irc.freenode.net.  We found the Ubuntu Driver list and our driver was there.  We activated and then the "Fn" + F2" started working and now we are editing the /etc/interfaces file to set up the default SSID login.

Thanks again!

McQUE

---

### Post by Lisiano on 2011-09-18
As I said on IRC. There is no need to edit /etc/interfaces. Just set it up using Network Manager. /etc/interfaces is mostly edited under server installations (No GUI).

---

