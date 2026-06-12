---
title: "Problem Editing .img file, no space left on device!"
date: 2016-03-12
forum: Packaging and Compiling Programs
---

### Post by ethan31 on 2016-03-12
Hello everyone, I am trying to modify an Android ROM, the system.img folder is in fact an EXT4, so I was able to mount it to a file folder using the command "sudo mount -t ext4 -o loop system.img sys/"This works perfectly fine for inspecting the files, but when I go in to try and edit "text files" and try to save it says that there is no room left on the device.  I went into this further and discovered that the disk space seems to be dynamically allocated. Meaning if I remove a file (23MB, for example) the disk space sjrinks by 23MB and will not allow me to save a file that is just 3.8KB. Is there anyway to fix this issue? Thanks everyone

---

