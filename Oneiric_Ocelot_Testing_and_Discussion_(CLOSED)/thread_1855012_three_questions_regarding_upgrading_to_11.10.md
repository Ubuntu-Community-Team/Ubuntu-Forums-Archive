---
title: "three questions regarding upgrading to 11.10"
date: 2011-10-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by liherb on 2011-10-05
I want to upgrade my ubuntu from 10.10 to 11.10. I have three specific questions regarding upgrading.  1. Will my personal documents and pictures stored under /HOME be wiped out during upgrading? Or they will stay there.  2. I have some configuration mess in my current 10.10 version, e.g. the wireless connection was not available any more after my installing some software. Will these configuration errors be automatically carried over to 11.10 after upgrading? Or it will be fixed automatically?  3. Is there any advantage just format the disk completely and install the new version? I heard someone call this &quot;clean installation&quot;, just wondering how cleaner it would be. (I will do my backup first for this method.)   Any thoughts would be appreciated. Thanks.

---

### Post by cariboo on 2011-10-05
The question I have, is do you have a separate /home/$USER directory? If so then backup your important files.

With all the changes in this version, many of the configuration in your home directory may not work properly. I'd suggest a clean install, including formatting your home directory.

---

### Post by oldos2er on 2011-10-05
You can't update directly from 10.10 to 11.10, you would need to go from 10.10 -> 11.04 -> 11.10. I think a clean install of 11.10 would be easier, personally.

Do you have /home on its own partition? Upgrading (as opposed to a clean new installation) shouldn't touch anything in /home, but I would backup any sensitive data first.

---

### Post by philinux on 2011-10-05
> **cariboo907 said:**
> The question I have, is do you have a separate /home/$USER directory? If so then backup your important files.

With all the changes in this version, many of the configuration in your home directory may not work properly. I'd suggest a clean install, including formatting your home directory.

+1 that. However, I think I'll just delete all app config files. Leave stuff like conky and bash* etc. 

I'll backup firefox bookmarks and start with a clean profile But I reckon I'll leave .evolution.

---

