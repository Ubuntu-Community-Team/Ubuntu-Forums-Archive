---
title: "Jar file excutable bit"
date: 2011-11-21
forum: Packaging and Compiling Programs
---

### Post by NerdcoreSteve on 2011-11-21
So, I made this little program and made it a jar file on my windows netbook. Then I tested it on my Ubuntu machine and discovered I had to set the file to be opened as an executable by right clicking on it and changing that permission.

Is there a way for me to set my jar file as executable for the user? Or will everyone who uses this program on an ubuntu machine have to right click on it before they can run it?

---

### Post by Bachstelze on 2011-11-21
It basically depends on how you plan to distribute the file. For example, if you distribute it via a medium formatted with a non-Linux filesystem, like a FAT32 USB key, then it is dependent on the user's system configuration whether the file will be executable "as is" (because those filesystems cannot store this information).

---

### Post by NerdcoreSteve on 2011-11-21
So if I made the jar file on my linux machine would it automatically be set to executable or do I have to do something extra?

---

### Post by Bachstelze on 2011-11-21
As I said, it depends. The "executable" flag is not part of the file, it is stored in the filesystem. This means that if you store the file on a filesystem that does not support it, like FAT32 or NTFS, it will be lost, regardless of what it was on your Linux filesystem.

---

