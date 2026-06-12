---
title: "System &quot;hangs&quot; after installing Nvidia driver"
date: 2011-10-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Yumi on 2011-10-02
Just installed the Nvidia driver from xswat. Last command I issued was "Sudo nvidia-xconfig". After this I restarted the system and now -

normal boot into black screen with no reaction. No key combination seems to do anything

boot into recovery mode and it hangs at "Loading initial ramdisk ...." again with no key working.

Any advice how to get out of this?

Michael

---

### Post by Harry33 on 2011-10-02
> **Yumi said:**
> Just installed the Nvidia driver from xswat. Last command I issued was "Sudo nvidia-xconfig". After this I restarted the system and now -

normal boot into black screen with no reaction. No key combination seems to do anything

boot into recovery mode and it hangs at "Loading initial ramdisk ...." again with no key working.

Any advice how to get out of this?

Michael

There is no Nvidia graphics driver in the ppa:ubuntu-x-swat/x-updates PPA for Oneiric.
For Oneiric a good working driver can be found in the official Oneiric repos.
Do not use the one in xorg-edgers.

---

### Post by MAFoElffen on 2011-10-02
> **Harry33 said:**
> There is no Nvidia graphics driver in the ppa:ubuntu-x-swat/x-updates PPA for Oneiric.
For Oneiric a good working driver can be found in the official Oneiric repos.
Do not use the one in xorg-edgers.
Good info.  As the OP's request was to be able to get going again... These instructions:

Get to your Grub boot menu.
Press "e" to change to edit mode.
Arrow down to the linux kernel noot line (starting with "linux")
Arrow right to where it says "quiet splash"
Replace that text with "--verbose text"
Press <cntrl><x> to boot.
Kernel will boot to TTY Text Console.
Log In.
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg/conf.old
sudo reboot

```
On boot, use same Grub edit instructions to insert "nomodeset" as a boot kernel switch to be able to boot VESA graphics with your nvidia card.

---

### Post by Yumi on 2011-10-03
Thank you, that worked perfectly! I am back in.

But the cause has not been identified. It also happens when the driver is installed from the main repositories.

Previously installed from x-swat following the explicit instructions for Oneiric here: [http://www.multimediaboom.com/install-nvidia-driver-ubuntu-1-04-11-10-ppa/]("http://www.multimediaboom.com/install-nvidia-driver-ubuntu-1-04-11-10-ppa/").

Michael

---

### Post by Harry33 on 2011-10-03
Like I said, in that Ubuntu-X-Swat/X-Updates PPA there is no nvidia drivers for Oneiric.
You have probably installed something for Natty Narwhal.
So the warning goes:
```

**Do not mix the sources.**

```

Here are all nvidia drivers from the PPA:

> 
  nvidia-graphics-drivers - 280.13-0ubuntu1~natty~xup1 brandonsnider 2011-08-02 Published Natty
  nvidia-graphics-drivers - 280.13-0ubuntu1~maverick~xup1 brandonsnider 2011-08-02 Published Maverick
  nvidia-graphics-drivers - 280.13-0ubuntu1~lucid~xup1 brandonsnider 2011-08-02 Published Lucid
  nvidia-graphics-drivers-173 - 173.14.27-0ubuntu1 albertomilone 2010-07-25 Published Lucid
  nvidia-graphics-drivers-173 - 173.14.16-0ubuntu2 bryce 2009-04-23 Published Jaunty
  nvidia-graphics-drivers-180 - 185.18.14-0ubuntu1 albertomilone 2009-06-15 Published Jaunty
  nvidia-graphics-drivers-96 - 96.43.18-0ubuntu1	albertomilone 2010-07-25 Published Lucid
  nvidia-graphics-drivers-96 - 96.43.10-0ubuntu2	bryce 2009-04-23 Published Jaunty
  nvidia-settings - 280.13-0ubuntu1~natty~xup1 brandonsnider 2011-08-02 Published Natty
  nvidia-settings - 280.13-0ubuntu1~maverick~xup1 brandonsnider 2011-08-02 Published Maverick
  nvidia-settings - 280.13-0ubuntu1~lucid~xup1 brandonsnider 2011-08-02 Published Lucid


---

### Post by MAFoElffen on 2011-10-03
> **Harry33 said:**
> Like I said, in that Ubuntu-X-Swat/X-Updates PPA there is no nvidia drivers for Oneiric.
You have probably installed something for Natty Narwhal.
So the warning goes:
```

[SIZE=3][COLOR=Red]**Do not mix the sources.**[/COLOR][/SIZE]

```
+1
LMAO!!! So true...

---

### Post by Yumi on 2011-10-05
Has nothing to do with the sources. The same thing happens when the nvidia-current driver is installed from the Oneiric repositories.

Michael

---

### Post by dino99 on 2011-10-05
open synaptic
disable xswat ppa
update
purge nvidia* packages
purge jockey* packages

reinstall: nvidia-current, nvidia-settings, jockey-gtk

reboot
and check driver activation: sudo jockey-gtk

---

### Post by Yumi on 2011-10-05
:oops:  Please do not hit me and accept my sincerest apologies! I followed the instructions and it still is not working.

The cause is that there is no Nvidia chip in this notebook! Its a Intel system. I have a couple of other systems with Nvidia and just failed to appreciate the difference.

Sorry

Michael

---

### Post by Harry33 on 2011-10-05
> **Yumi said:**
> :oops:  Please do not hit me and accept my sincerest apologies! I followed the instructions and it still is not working.

The cause is that there is no Nvidia chip in this notebook! Its a Intel system. I have a couple of other systems with Nvidia and just failed to appreciate the difference.

Sorry

Michael

Well, the problem is solved.
That is OK.

---

