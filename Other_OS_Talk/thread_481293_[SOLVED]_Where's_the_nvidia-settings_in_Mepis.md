---
title: "[SOLVED] Where's the nvidia-settings in Mepis?"
date: 2007-06-22
forum: Other OS Talk
---

### Post by FuturePilot on 2007-06-22
I'm using the 9631 driver from the Mepis repos,  but there seems to be no nvidia-settings. If I type nvidia-settings in the terminal all I get is command not found. So where are these nvidia-settings?

---

### Post by dannyboy79 on 2007-06-22
did you install it yet? if not
sudo aptitude install nvidia-settings
then if it doesn't create a menu item, you can always create your own or just use the terminal like you've been trying.

---

### Post by FuturePilot on 2007-06-22
I checked in Synaptic but there is no package nvidia-settings:-k

---

### Post by igknighted on 2007-06-22
Its based on Dapper.  If you remember, dapper didn't have the same nvidia settings that edgy and beyond have.  The command was something longer with two hyphens, I don't exactly remember it right now, but if you look in the wiki for some dapper nvidia how tos I'm sure you will find it.

---

### Post by FuturePilot on 2007-06-22
I already have it enabled, but I need to set some stuff with the configuration tool. I'm looking for the thing in the attached image. And it didn't come with the driver like it should have, and it's not an extra package in the repos. Well if it is, I can't find it. :(

---

### Post by igknighted on 2007-06-22
> **FuturePilot said:**
> I already have it enabled, but I need to set some stuff with the configuration tool. I'm looking for the thing in the attached image. And it didn't come with the driver like it should have, and it's not an extra package in the repos. Well if it is, I can't find it. :(

no, I know exactly what you mean.  But that tool was not called nvidia-settings in dapper IIRC.  I'm not sure if the GUI was included in the Dapper package either actually, you may need to use the CLI version.

EDIT: I looked it up, the command I spoke of was "nvidia-glx-config".  I think nvidia-settings may only have been in Edgy.  The other thing to consider, does mepis use sudo?  If not, use "su -" instead of "su" to become root in order to get access to that command.  Like I mentioned before, nvidia-glx-settings may not have the GUI, you might need to use the CLI options, but it should work for you.

---

### Post by FuturePilot on 2007-06-22
nvidia-glx-config
bash: nvidia-glx-config: command not found

:(

---

### Post by FuturePilot on 2007-06-22
Ah ha! Found the solution. I needed to add a Dapper repo to the list.
[http://www.mepislovers.org/forums/showthread.php?t=8252]("http://www.mepislovers.org/forums/showthread.php?t=8252")
Remove it afterwards
:D

---

### Post by dannyboy79 on 2007-06-23
> **FuturePilot said:**
> Ah ha! Found the solution. I needed to add a Dapper repo to the list.
[http://www.mepislovers.org/forums/showthread.php?t=8252]("http://www.mepislovers.org/forums/showthread.php?t=8252")
Remove it afterwards
:D

Wait what????? I use Fiesty and I have nvidia-settings! I didn't add no Dapper repo.

---

### Post by FuturePilot on 2007-06-23
Well the Mepis people must have removed it from the driver package, because that's why I was surprised it wasn't included with the driver. Ubuntu includes it with the driver. I even check the size of the packages and in Feisty the 9631 driver is a little over 4 MB and in Mepis it's around 3.5 MB. Don't know what the point of removing it form the package was though.

---

### Post by igknighted on 2007-06-23
> **FuturePilot said:**
> Well the Mepis people must have removed it from the driver package, because that's why I was surprised it wasn't included with the driver. Ubuntu includes it with the driver. I even check the size of the packages and in Feisty the 9631 driver is a little over 4 MB and in Mepis it's around 3.5 MB. Don't know what the point of removing it form the package was though.

Perhaps to fit onto the live CD?  IIRC the nvidia driver is included on there (at least on 6.5)

---

