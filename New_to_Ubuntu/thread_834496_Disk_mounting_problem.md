---
title: "Disk mounting problem"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by groeswenphil on 2008-06-19
Anybody help?

My disk has three partitions thusly.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9585    76991481    7  HPFS/NTFS
/dev/sda2            9586       10801     9767520   83  Linux
/dev/sda3           10802       19190    67384642+  83  Linux
/dev/sda4           19191       19457     2144677+  82  Linux swap / Solaris
Note: sector size is 4096 (not 512)


Now.........I can access all of the partitions. My XP partition even loads automatically on startup.
Problem is, two pieces of software, Amarok and Picasa won't read my XP or my Ubuntu storage partition directly through their own filing systems.
I can go to a file anywhere on my computer and say for instance; right click and open with Amarok.
It's only a little niggle, but I'd like these applications to be able to catalogue my media and at the moment, they won't.


Any advice?
Phil

---

### Post by Duck2006 on 2008-06-19
For mounting win partitions.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

For mounting linux partitions.

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by Victormd on 2008-06-19
Check the link on my signature.
That's how I set mine up and Amarok can access my mp3s on my windows partition without any problems.

---

### Post by logos34 on 2008-06-19
> **groeswenphil said:**
> but I'd like these applications to be able to catalogue my media and at the moment, they won't

And you're sure you have Amarok configured correctly?

>Settings>configure amarok>collection>check the windows drives/partitions (under '**media**'?)
x 'scan folders recursively'
sqlite is the default

>Tools>rescan collection

---

