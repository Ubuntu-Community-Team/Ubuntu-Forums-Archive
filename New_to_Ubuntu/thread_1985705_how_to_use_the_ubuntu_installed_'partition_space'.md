---
title: "how to use the ubuntu installed 'partition space' ?"
date: 2012-05-23
forum: New to Ubuntu
---

### Post by abijosh on 2012-05-23
1. I have a 200 GB as a single partition C: in my lap.. 

2. I have installed ubuntu in the same partition C: using windows installer. 

3. I have used 30 GB of space for ubuntu; which is the max in the windows installer.. 

4. Other than that 30GB in the partition I dont have access to other free space or the files in the partition C: while using ubuntu.. but i am free to use the other partitions.. D: E: F:

5. I have no problem while using win 7.. 

Now my question is .. is there any possibility that i can use the remaining space in C: and access the files in it while using ubuntu??

---

### Post by mlentink on 2012-05-23
I am not sure I understand precisely what you're asking. Do you want to store files e.g. in your windows 'My Documents'-folder? That shoudl be entirely possible.

Please be aware that installing ubuntu using the windows installer (Wubi, as it is commonly referred to) does _not_ create any partitions. It simply creates a windows-file, in which it stores a virtual 'partition' to run ubuntu. The 30GB may welle be a windows limit, I do not know. But otherwise you should be able to access all windows files, just as you would when installing in a real partition.

---

### Post by abijosh on 2012-05-23
> **mlentink said:**
> I am not sure I understand precisely what you're asking. Do you want to store files e.g. in your windows 'My Documents'-folder? That shoudl be entirely possible.

s you are right.. thats wat i'm asking for .. :)

---

### Post by westie457 on 2012-05-23
To see the Windows files from Ubuntu installed via WUBI you need to open the File Browser - Nautilus - and find the /host folder. From there you will be able to access all Windows files.

Be careful where you write files to and delete files from in Windows. It is very easy to accidentally remove something important from the main Windows Folder.

---

### Post by abijosh on 2012-05-24
easy.. :) thanks

---

### Post by Mark Phelps on 2012-05-24
Since C: is most likely your OS partition, while it's generally OK to read files from there while inside Ubuntu, it's also generally a BAD idea to make changes to files from there while inside Ubuntu. Make changes to files or directories inside a Windows OS partition from Ubuntu (outside) risks corrupting the Windows filesystem and rendering that OS unbootable.

If you want to actually share files between the two OS's, a better solution is to move the files to one of the other partitions.

---

### Post by mlentink on 2012-05-24
> **Mark Phelps said:**
> Since C: is most likely your OS partition, while it's generally OK to read files from there while inside Ubuntu, it's also generally a BAD idea to make changes to files from there while inside Ubuntu. Make changes to files or directories inside a Windows OS partition from Ubuntu (outside) risks corrupting the Windows filesystem and rendering that OS unbootable.

If you want to actually share files between the two OS's, a better solution is to move the files to one of the other partitions.


Hmm. So you think ntfs-3g is unstable or insecure? Haven't experienced any problems with it so far.

---

### Post by wilee-nilee on 2012-05-24
> **mlentink said:**
> Hmm. So you think ntfs-3g is unstable or insecure? Haven't experienced any problems with it so far.

It is not that it is unstable or insecure, it is that you are modifying a non running OS, not a good policy with windows although some have no problems.

The standard advice for a dualboot is to have the OS's in actual seperate partitions and have a shared NTFS they both have access to.

A wubi is for trying out ubuntu in lieu of a partitioned install.

Some though may have limitations that do not allow this such as a work computer not being allowed to modify the HD as one example.

If this is your computer, and you like ubuntu transfer the wubi to a partition make a shared NTFS and call it a day.

Here is what the wubi designer says about it, and the transfer wiki.

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)

[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

---

### Post by mlentink on 2012-05-24
> **wilee-nilee said:**
> It is not that it is unstable or insecure, it is that you are modifying a non running OS, not a good policy with windows although some have no problems.
I would think that changing files in a *running* (Windows) OS is even more dangerous, as you don't know  what Windows is doing.
> **wilee-nilee said:**
> If this is your computer, and you like ubuntu transfer the wubi to a partition make a shared NTFS and call it a day. Agreed , and this is also my setup. Though I haven't experienced problems writing to the W7 partition either.

---

### Post by abijosh on 2012-05-26
I am not going to mess up with system files anyhow.. thanks for the advice..

---

