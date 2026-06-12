---
title: "Getting drive info in java"
date: 2013-10-05
forum: Programming Talk
---

### Post by andrewkrieg on 2013-10-05
Okay, I am working on a security suite, but I need to list all drives and partitions on said drives. The base language is Java, but C/C++ libraries can be loaded.

This is what I have now:
[PHP]
import java.io.File;
for(File f : File.getRoots()) {
    System.out.println("Root: " + f.getName());
}[/PHP]
But it only outputs:
```
Root: /
```

However, I have my home folder on a separate partition, so when I run this:
[PHP]
for(String s : new String[] {"/", "/home"}) {
    System.out.println("Size of " + s + " is " + (new File(s).getTotalSpace() / 1024 / 1024 / 1024) + " GB");
}
[/PHP]
I get this:
```

Size of / is 96 GB
Size of /home is 355 GB

```
Which proves I have 2 partitions

I need the application to detect all partitions so it can scan them. Any help would be appreciated.

ALSO:
File.listRoots() does not list USB drives and such, which I will also need, if you have any advice on that I would be grateful.

THANKS! :D

---

### Post by ofnuts on 2013-10-05
As its name implies, listsRoots() lists roots and not filesystems. If you RTFM:

*A particular Java platform may support zero or more  hierarchically-organized file systems.  Each file system has a  root directory from which all other files in that file  system can be reached.  Windows platforms, for example, have a root  directory for each active drive; UNIX platforms have a single root  directory, namely "/".*

If you security suite has any value it has to be very system-dependent... For Linux the mounted file systems can be found in /etc/mtab. However if you scan everything under "/" you will scan all the filesystems...

---

### Post by andrewkrieg on 2013-10-06
Thank you! very much.

---

