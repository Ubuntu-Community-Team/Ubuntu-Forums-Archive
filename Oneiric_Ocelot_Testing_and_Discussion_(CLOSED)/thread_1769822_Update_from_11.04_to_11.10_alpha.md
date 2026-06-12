---
title: "Update from 11.04 to 11.10 alpha"
date: 2011-05-28
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by mscout2004 on 2011-05-28
Went to get the newest development release using the code "update-manager -d" and I get the following error:

```
W:Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources  404  Not Found
, W:Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

```So it will not let me finish the update.

---

### Post by linuxman94 on 2011-05-28
Go into software sources, click on the other software tab and uncheck the independent listings.  Then it should work.  Just a note, Oneiric is not in alpha stage yet and many things are broken. Do not use it in your production environment, use a virtual machine or install it separately.

---

### Post by mscout2004 on 2011-05-28
thx linuxman94, that solved the issue. I dont use this on a main pc the one I am trying to update is my testing pc to help do debugging work for a software company.

---

### Post by NormanFLinux on 2011-05-29
I'd wait until the second beta or release candidate to install 11.10. GNOME 3 is still buggy and if they can get it stable by the time the major features are frozen, it'll be an accomplishment!

---

### Post by cariboo on 2011-05-29
> **NormanFLinux said:**
> I'd wait until the second beta or release candidate to install 11.10. GNOME 3 is still buggy and if they can get it stable by the time the major features are frozen, it'll be an accomplishment!

That's the reason why this forum is here, to find and report bugs, if you want stable and mostly bug free, use the LTS version.

---

