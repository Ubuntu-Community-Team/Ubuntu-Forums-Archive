---
title: "GenISOimage"
date: 2013-06-24
forum: New to Ubuntu
---

### Post by pghud3 on 2013-06-24
while using remastersys and i know its not the fault of the remastersys but of genisoimage is their a way around the file size limit? i get the below message The compressed filesystem is larger than genisoimage allows for a single file. you must try to reduce the amount of data you are backing up. 

Thanks

---

### Post by Fragadelic on 2013-08-04
Add "-comp xz" to the squashfs options in the config file and it will compress the squashfs more.  This might get you under the limit.  Otherwise, try to remove some unwanted icons, images, etc - basically any other things you don't really need.  Check Trash and make sure it is empty and also check root's Trash folder.

---

