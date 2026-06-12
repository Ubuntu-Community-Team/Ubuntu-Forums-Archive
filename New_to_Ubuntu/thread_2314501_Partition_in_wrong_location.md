---
title: "Partition in wrong location"
date: 2016-02-21
forum: New to Ubuntu
---

### Post by Billy_Tingles on 2016-02-21
I cannot change the location of a partition.  Its located in a user account that I deleted and cant figure out how to move it.  I also can't find a way to change the permissions on said partition.

---

### Post by deadflowr on 2016-02-21
Where is it located, currently?
Post as much information about how you set it up as possible, please.

---

### Post by yancek on 2016-02-21
Open a terminal and run the command:  sudo mount
Post the output and indicate which partition you are referring to.

---

### Post by grahammechanical on 2016-02-22
I think you mean that a user created a partition and since you deleted that user you cannot write to the partition to store files on it or delete any of the files on it. Is this a better explanation? It is an explanation that I can understand. But this "partition in the wrong location" is beyond my understanding and needs some explanation.

Open the File Manager. In the left pane there should be a list of partitions. Mount/open the partition by clicking on it. The contents of the partition should appear in the right pane. Right click the background of the right pane and from the menu select Properties and then open the Permissions tab.

It is in the permissions tab that we can change permissions not only of folders & files but also of the partition itself and we can do it with a graphical user interface. But, at the moment we do not have the authority to change any permissions because we are working as a standard user. We need to open the File Manager with administrator authority. But before we explain how to do that we need to know what it is you can or cannot do.

Regards

---

