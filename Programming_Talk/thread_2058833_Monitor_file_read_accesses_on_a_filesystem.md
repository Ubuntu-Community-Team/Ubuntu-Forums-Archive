---
title: "Monitor file read accesses on a filesystem"
date: 2012-09-16
forum: Programming Talk
---

### Post by Asmodai on 2012-09-16
I'm trying to monitor all read accesses on a particular file system. It seems that fanotify was created for this purpose - however, it only tells me that there was an access in the first place, but not the offset, nor how many bytes were read.
Is there a way to get this information with fanotify or is there another way?

---

