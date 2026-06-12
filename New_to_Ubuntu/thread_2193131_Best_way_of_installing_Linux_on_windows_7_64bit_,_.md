---
title: "Best way of installing Linux on windows 7 64bit , Dual Boot."
date: 2013-12-11
forum: New to Ubuntu
---

### Post by gloriasea8 on 2013-12-11
Hello Everyone ,
I would really like to install Ubuntu/Linux on my windows 7 64bit pc with views as going fully Linux in future...anyway I downloaded the installer version 12.04.3 & it asked me to partition so I chose 25 and of it went for a while but t the end an error popped up and it just won't install. 
I know other people who have done it easily on xp and vista but windows 7 is more tricky and I am not the most technically knowledgeable. 
I wonder if anyone can point me to the most likely to install and or best version for windows 7 64 bit .
Help greatly needed and much appreciated , Thanks.

---

### Post by oldfred on 2013-12-11
Almost all Windows 7 systems use all 4 primary partitions. And then you cannot install any more partition. You have to delete one primary and make it be  an extended partition. And inside the one extended partition you can have an unlimited number of logical partitions.

Post this from terminal in live installer.
sudo parted -l

       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
This suggests removing system partition and making c: the bootable partition. But has details on all alternatives
[http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-installed/td-p/742019](http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-installed/td-p/742019)

Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

