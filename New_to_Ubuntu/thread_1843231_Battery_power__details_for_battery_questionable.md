---
title: "Battery power / details for battery questionable"
date: 2011-09-13
forum: New to Ubuntu
---

### Post by Cramir on 2011-09-13
When i display the detailed information about the battery i use i get the information that the battery whould be full at 10,6 while the Design for the battery is displayed for 39,6. The value allways stays at 10,6 W even if i change the battery for a older one which has certainly less power. Hence i ask: How can these values be reset? Or do you think its a hardware problem?

using Natty Narwhal, toshiba portegé m400 1,83 dual core cpu

---

### Post by 2F4U on 2011-09-13
You could look into /proc/acpi/battery/BAT0/info (that is the path on my laptop, your path might be slightly different). This file contains a "design capacity" and a "last full capacity" as well as a "design voltage". The way I understand it, the "design" values are those that the device had when it was new, so they are never changing.

---

### Post by Cramir on 2011-09-13
Those are exactly the values i was talking about, the last full capacity stays allways the same no matter if i use a old or relatively new battery. How is that possible? Anyways i do not believe that only 20 percent of design capacity are the maximum a relativly new battery can reach, dont you?

---

