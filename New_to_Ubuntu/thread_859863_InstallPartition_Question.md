---
title: "Install/Partition Question"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by KizzleEvolve on 2008-07-15
I'm trying to install Ubuntu on a second hard drive in my PC. The first is my primary drive(c: ) with XP on it the second is intended to be used for Ubuntu and a partition for storage. I set up the second partition using Partition Manager and had intended it to be for the Ubuntu install. When I went to install Ubuntu I found which partition was the correct one from the size of it and set it to /ext3 this is where I ceased to be able to find what to do. Needless to say Ubuntu failed to install and here I am.

Thanks in advance for the help.

---

### Post by ozzyprv on 2008-07-15
Without being an expert I will try to help you.

Ubuntu has to be installed in a /ext3 type of file system. The mount point has to be "/" (without the quotes).

Does that help?

---

### Post by Inxsible on 2008-07-15
In addition to ozzy's reply,

you will also have to create another partition for swap.

It would also be advisable to create another partition for the home drive mounted at /home

Here are two great links that give you an illustrated walk-through of the installation process

[Partitioning]("http://www.psychocats.net/ubuntu/partitioning")   [Installing]("http://www.psychocats.net/ubuntu/installing")

---

