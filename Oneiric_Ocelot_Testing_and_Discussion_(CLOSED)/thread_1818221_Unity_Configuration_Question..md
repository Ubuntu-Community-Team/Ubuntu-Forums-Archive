---
title: "Unity Configuration Question."
date: 2011-08-04
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Xgen on 2011-08-04
I noticed that the option to show devices was added to the Compiz Unity Experimental section. Also, under Dconf-->Desktop-->Unity-->Devices there is a heading for favorites on the Launcher. Using this, would it be possible to only show mounted flashdrives and what information would I add?

---

### Post by mc4man on 2011-08-04
The short answer would be no and therefore, nothing
The plugin option is applied to all devices.

 The dconf key reflects the UUID of what devices(drives) you've chosen to show when not mounted. (Keep in launcher 
Removable media is excluded here from being kept

```
// "Keep in launcher" item
  if (DevicesSettings::GetDefault().GetDevicesOption() == DevicesSettings::ONLY_MOUNTED
      && drive && !g_drive_is_media_removable (drive))
```

---

