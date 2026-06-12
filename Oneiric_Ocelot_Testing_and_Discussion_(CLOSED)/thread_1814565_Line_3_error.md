---
title: "Line 3 error"
date: 2011-07-29
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by rv65 on 2011-07-29
E: Type 'x-swat/x-updates/ubuntu' is not known on line 3 in source list /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-oneiric.list

Keep getting this error since I've purged that PPA. I had to due to the nvidia 280 driver not working on my setup. Any help would be great.

---

### Post by seeker5528 on 2011-07-29
Rename or delete the ubuntu-x-swat-x-updates-oneiric.list file.

If you added the PPA using normal methods it should only contain information related to the one PPA.

The official repositories should all be in '/etc/apt/sources.list' so any *.list files in '/etc/apt/sources.list.d/' shoud be OK to delete.

Later, Seeker

---

### Post by rv65 on 2011-07-29
Thanks for your help, that worked out great. :)

---

