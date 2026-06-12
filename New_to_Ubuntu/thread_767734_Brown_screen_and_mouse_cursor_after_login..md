---
title: "Brown screen and mouse cursor after login."
date: 2008-04-25
forum: New to Ubuntu
---

### Post by luke949 on 2008-04-25
Hi everyone, I just upgraded to 8.04 from 7.10. When I attempt to log on, all I get is a brown screen and the mouse cursor. I believe GNOME isn't being loaded properly. Can someone please help me with this problem?

Thank you.

---

### Post by Joeb454 on 2008-04-25
Do you have a dedicated graphics card? i.e. Nvidia or Ati, this could be something to do with the issue :)

---

### Post by luke949 on 2008-04-25
No i don't, I just have a intel 945 chipset. It's a Asus 3690 laptop.

---

### Post by Joeb454 on 2008-04-25
Hmmm...how long have you left it before giving up and trying again?

---

### Post by luke949 on 2008-04-25
about 30 minutes.

---

### Post by spiderbatdad on 2008-04-25
This might help: ```
A temporary fix would be to add asus_acpi to /etc/modprobe.d/blacklist, and force asus-laptop to be loaded (by adding it to /etc/modules).
```

[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/141498](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/141498)

---

### Post by luke949 on 2008-04-25
> **spiderbatdad said:**
> This might help: ```
A temporary fix would be to add asus_acpi to /etc/modprobe.d/blacklist, and force asus-laptop to be loaded (by adding it to /etc/modules).
```

[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/141498](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/141498)

Can you please walk me through the steps on doing this? I am a new user to Ubuntu, sorry. :(

---

### Post by spiderbatdad on 2008-04-25
This information is related to hardware detection problem on a similar laptop, and I believe, specific to the previous kernel. However it may help you. I doubt it will do any harm, and you should be able to undo the changes, should they fail to help. 

You will need to get some type of login, so I would suggest recovery mode first. If that fails, you'll need a live cd, and we'll have to try to mount your root file system.

From the terminal prompt of your login, you should have this symbol #. 
Do. ```
nano /etc/modprobe.d/blacklist
```

anywhere in the list of modules, insert the line:
asus_acpi

you can also add a line like:
# blacklisted by me

The # is a comment regarding the change.

Use ctrl-o to write the changes to the file, and hit enter to confirm the file name. Ctrl-x to exit.

Next edit the /etc/modules file:

```
nano /etc/modules
```

add the line:

asus-laptop

save...confirm...exit

Reboot.

If you cant get a login with recovery mode, post back and I or someone will try to help you mount your file system from the live cd.

---

### Post by luke949 on 2008-04-25
Hmmmm... still no good. Any other suggestions?

---

### Post by spiderbatdad on 2008-04-25
You mean you edited both files, and got no better result?

Perhaps read the output of dmesg (run in a terminal) and look for suggestions regarding boot parameters, like: "try using lapic" or "try the option acpi=off."

---

### Post by PmDematagoda on 2008-04-25
When you reach the GDM login screen, press Session and then select the GNOME Fail Safe option, then try logging in.

---

### Post by Joeb454 on 2008-04-25
Are you sure the CD burnt correctly? Can you check it for defects (it's one of the boot options)

---

### Post by luke949 on 2008-04-25
Yes I edited both files and I got no results after a reboot. I typed dmesg in terminal and I'm unsure what to find. Again, I apologize for my inferior skills in Ubuntu. :(

---

### Post by luke949 on 2008-04-25
> **PmDematagoda said:**
> When you reach the GDM login screen, press Session and then select the GNOME Fail Safe option, then try logging in.

I did that and internal error window popped up saying "failed to initialize HAL!". But I am logged in and im able to browse through things without internet.

---

### Post by luke949 on 2008-04-25
> **Joeb454 said:**
> Are you sure the CD burnt correctly? Can you check it for defects (it's one of the boot options)

I am not using the Live CD.

---

### Post by PmDematagoda on 2008-04-25
> **luke949 said:**
> I did that and internal error window popped up saying "failed to initialize HAL!". But I am logged in and im able to browse through things without internet.

Then try executing:-
```
sudo /etc/init.d/hal start
```

Also, how do you connect to the internet?

---

### Post by spiderbatdad on 2008-04-25
It may be a problem with hal in a race with gdm.lol

This may fix:```
sudo mv /etc/rc2.d/S20dbus /etc/rc2.d/S12dbus
```

Please read this entire report first, in order to decide for yourself if this looks like what you want to do. [https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/25931](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/25931)
I am not an expert.

---

### Post by luke949 on 2008-04-25
> **PmDematagoda said:**
> Then try executing:-
```
sudo /etc/init.d/hal start
```

Also, how do you connect to the internet?

Ok, the response I got back was:
 * Starting Hardware abstraction layer hald

and I use a wireless connection.

---

### Post by PmDematagoda on 2008-04-25
> **luke949 said:**
> Ok, the response I got back was:
 * Starting Hardware abstraction layer hald

and I use a wireless connection.

It seems that HAL has started, did you now check Network Manager if it has detected your wireless chipset?

---

### Post by luke949 on 2008-04-25
> **PmDematagoda said:**
> It seems that HAL has started, did you now check Network Manager if it has detected your wireless chipset?

I went to Network Tools and the Network Device is: Loopback Interface (lo). I am unsure as to whether or not what this means.

---

### Post by luke949 on 2008-04-25
> **spiderbatdad said:**
> It may be a problem with hal in a race with gdm.lol

This may fix:```
sudo mv /etc/rc2.d/S20dbus /etc/rc2.d/S12dbus
```

Please read this entire report first, in order to decide for yourself if this looks like what you want to do. [https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/25931](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/25931)
I am not an expert.

I decided not to execute this command, I am not getting any hanging issues when browsing through files. Thank you for the heads up.

---

### Post by luke949 on 2008-04-26
Does anyone have any other suggestions?

---

### Post by spiderbatdad on 2008-04-26
Lost sight of your issue. Is it still a login issue and failure to initialize HAL, or is it now a wireless issue?

---

### Post by luke949 on 2008-04-26
I can log into failsafe mode, but the error still popups and I am not getting any internet through wireless connection or in wired connection.

---

### Post by spiderbatdad on 2008-04-26
going to need some info on your wireless card: ```
sudo lshw -C net
```

The issue with HAL may yet be solved by the previous bug report, but would require you verify the rc.d files exist in your installation. That report deals with initializing HAL before gdm tries to start. I think that's the problem there.

---

### Post by luke949 on 2008-04-26
I get this in response:

*-network:1
description: Wireless interface
product: AR2413 802.11bg NIC
vendor: Atheros Communications INC.
physical id: 2 
bus info: pci@0000:06:02.0
logical name wifi0
version: 01
serial: 00:19:7d:d7:2f:8e
width: 32 bits
clock 33MHz
capabilities: pmbus_master cap_list logical ethernet physical wireless

configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.2) latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g




Sorry for my slow response, I had to type this all out since I have no way of copying from one my laptop to this computer :(

---

### Post by spiderbatdad on 2008-04-26
Try runing```

sudo modprobe ath_pci
```

You may need to use the madwifi drivers available for this card. Sorry I can't be of more help with this card. Surely there are some posts...maybe google ubuntu AR2413

---

### Post by encompass on 2008-04-26
I don't think that is the issue... it's prbably gnome...
Can you try selecting a session when you login?
For example failsafe gnome...
type your username...
then press F10...
select change session... choose fail safe gnome or something else....
Does it login?
if not... restart X with ctrl-alt-backspace and try to do a login as normal...
anything?
If not... we could even try to clean out your settings and see if that is the issue.
But lets get the report from this first.

---

### Post by luke949 on 2008-04-26
> **encompass said:**
> I don't think that is the issue... it's prbably gnome...
Can you try selecting a session when you login?
For example failsafe gnome...
type your username...
then press F10...
select change session... choose fail safe gnome or something else....
Does it login?
if not... restart X with ctrl-alt-backspace and try to do a login as normal...
anything?
If not... we could even try to clean out your settings and see if that is the issue.
But lets get the report from this first.

Yes I can log into failsafe GNOME.

---

### Post by encompass on 2008-04-26
Read the entire post before doing anything....
I had a very similar issue...
Ends up if you move all your data into another place... for example...
you have your /home/username/ directory right?  now in there is a bunch of files which contain all your settings...
if you take every hidden file and directory and move it into a directory like this...
```

mkdir ~/backupCheck/
mv ~/.* ~/backupCheck/

```
and then restart your computer and try to login again... does it work?
if not.. then there is something that I can't figure out for you. :(
If it does work... then it's probably in something from those files you moved... you can slowly move one after another to find which one it is... but odds are it's your .gconf or .gnome and probably something in there.
Now you may lose some settings.  But at least your going to be back up and running again.  Most of the settings you may loose... if this works... are things like... your passwords for wireless connections and a few other things.  But they aren't something you can setup again.

---

