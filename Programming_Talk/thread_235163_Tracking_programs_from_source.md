---
title: "Tracking programs from source"
date: 2006-08-12
forum: Programming Talk
---

### Post by ironfistchamp on 2006-08-12
Ok bear with me here because I may be talking complete rubbish. I thought it would be good to have some kind of program or something that kept a record of all the apps installed from source. Perhaps made a readable list of dependencies, maybe checked what depended on it, made it easy to remove the source apps aswell. I install loads of things from source and I always forgetting what it is and where it is. Maybe a little thing at compile time. Is this a good idea. Is it even possible? Or am I talking out of my arse yet again.

Thanks for any feedback

Ironfistchamp

---

### Post by cwaldbieser on 2006-08-12
> **ironfistchamp said:**
> Ok bear with me here because I may be talking complete rubbish. I thought it would be good to have some kind of program or something that kept a record of all the apps installed from source. Perhaps made a readable list of dependencies, maybe checked what depended on it, made it easy to remove the source apps aswell. I install loads of things from source and I always forgetting what it is and where it is. Maybe a little thing at compile time. Is this a good idea. Is it even possible? Or am I talking out of my arse yet again.

Thanks for any feedback

Ironfistchamp

If you use checkinstall, it will create a .deb package out of your source installation.  That way, it is integrated with the normal package system, so you can uninstall it easilly, browse what you have installed, etc.

---

### Post by ironfistchamp on 2006-08-13
Thats brilliant I shall check it out asap. Thanks

---

