---
title: "error: no such partition&quot; followed by &quot;Grub rescue&quot;"
date: 2013-08-08
forum: New to Ubuntu
---

### Post by Stefan416 on 2013-08-08
I am in need of a great amount of help.  my setup is i dual boot windows 7 with ubuntu. I went and turned my computer on . the menu came up with witch partition i wanted to start up into. and accidentally hit windows recovery . so i hit exit to get out of it and the computer restarted but now i get (error: no such partition" followed by "Grub rescue")  What do i need to do so boot back into windows. Can anybody help me please. i've looked around but not sure which thing to try.



stefan

---

### Post by Stefan416 on 2013-08-08
never mind got it

---

### Post by oldfred on 2013-08-09
It seems many systems immediately restore partition table when you boot recovery mode, but not Windows boot loader. Or you have erased all new partitions in partition table.

You may be able to restore partitions with testdisk. It normally can find all the old versions of partitions you had on drive and if nothing was written into Linux partitions you also may recover them. 
Best if you know old partition layout as testdisk finds all changes and you have to choose the version you had and no partitions can overlap. If you made a lot of changes it can get confusing.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

      
 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

Best to make Windows recovery CD so you can repair Windows and remove  recovery entry from grub menu.

---

### Post by Stefan416 on 2013-08-09
awsome thanks for the help i've got it working again

---

