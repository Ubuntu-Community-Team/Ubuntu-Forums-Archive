---
title: "Compiz - avant window navigator"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by Dadsgé on 2008-10-08
I installed compiz, then i installed the avant window navigator
no problems so far, i already have this for 2 day
but suddenly none of them both seems to work anymore
i uninstalled the AWN but compiz still doesnt work...

and if i boot my system it gives me a whole list, at the end it says
'error while booting
pres Ctrl+D to boot system
root@hannes-laptop: $'

rather strange, cause i rebooted my system many times after installing these appl

the only other thing i did is a fix to make my hotkeys, camera,... work
> sudo apt-get install module-assistant eeepc-acpi-source
sudo m-a a-i eeepc-acpi
sudo sh -c 'echo eeepc-acpi >>/etc/modules'

can someone help me with this problem?

greetz
Dadsgé

---

### Post by SpenceMakesSense on 2008-10-08
what happens when you type in a terminal
```
 compiz --replace
```

---

### Post by Dadsgé on 2008-10-08
just gives:

> Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2592 (rev 04) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 


trying compiz:
> Desktop effects could not be enabled.

---

### Post by SpenceMakesSense on 2008-10-08
did u double check to see if your graphics card is still installed?

---

### Post by Dadsgé on 2008-10-08
and how do I check that?

---

### Post by nothingspecial on 2008-10-08
In your menus. System > administration > Hardware Drivers

---

