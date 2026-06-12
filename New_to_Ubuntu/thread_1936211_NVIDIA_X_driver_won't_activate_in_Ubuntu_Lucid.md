---
title: "NVIDIA X driver won't activate in Ubuntu Lucid"
date: 2012-03-05
forum: New to Ubuntu
---

### Post by Bumpalot on 2012-03-05
Video Card: Nvidia GTX 550 Ti 64bit
Have previously used this sucessfuly for several months, but had a crash & reinstalled.

Install procedure: 
sudo apt-get update && sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings
Installed successfully
Hardware Drivers - reports installed & active

On reboot, nvidia screen not active

Opened System/Admin/Nvidia X Server Settings
Message "You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

bump@bumpyputer:~$ sudo apt-get install nvidia-settings
[sudo] password for bump: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-settings is already the newest version.
nvidia-settings set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
bump@bumpyputer:~$

bump@bumpyputer:~$ nvidia-xconfig
Using X configuration file: "/etc/X11/xorg.conf".
ERROR: Unable to write to directory '/etc/X11'.
bump@bumpyputer:~$ 

Am at a loss - need suggestions please.

---

### Post by MG&amp;TL on 2012-03-05
Does the "additional drivers" not supply anything?

As for the xconfig bit, "as root" in ubuntu means "tack sudo on the front". 

```
sudo nvidia-xconfig
```

should work.

---

### Post by Bumpalot on 2012-03-05
I did this previously:
bump@bumpyputer:~$ sudo nvidia-xconfig
[sudo] password for bump: 

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

Opened System/Administration/Nvidia X Server Settings
Same Msg:  You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

---

### Post by Bobhuber on 2012-03-05
> **Bumpalot said:**
> I did this previously:
bump@bumpyputer:~$ sudo nvidia-xconfig
[sudo] password for bump: 

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

Opened System/Administration/Nvidia X Server Settings
Same Msg:  You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.
Did you reboot after doing this?

---

### Post by Bumpalot on 2012-03-06
Yes - 3 times up to this date - get same message.

---

### Post by Bumpalot on 2012-03-06
Have solved this myself. Thanks guys!

---

### Post by critin on 2012-03-06
> Have solved this myself. Thanks guys!

Please explain how you solved it!

---

