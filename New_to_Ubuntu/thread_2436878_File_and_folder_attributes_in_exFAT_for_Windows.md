---
title: "File and folder attributes in exFAT for Windows"
date: 2020-02-14
forum: New to Ubuntu
---

### Post by gagorial on 2020-02-14
Please, could you help me to assign files or folders attributes at an USB drive for Windows?


I has used fatattr but it does not works with exFAT, do you know another tool for do this? I would prefer a graphic user interface whether it is possible.


Sincerely.

---

### Post by TheFu on 2020-02-14
Non-native file systems don't support permissions under any Unix-like OS.
Permissions, owner, group and any ACLs can only be set through mount option.  There are many posts in these forums about this with specific solutions - "***fstab mount permissions exfat***" is what I'd search.

Sorry, I don't know any GUI tool that does mounting in a way I would trust not to break or have terrible performance.

---

### Post by gagorial on 2020-02-14
I am not referring to assign attributes for Ubuntu or any other Linux distribution; I am referring attributes as hidden, read-only&#8230; I require a tool for Windows machines, but I would prefer do the task on Linux, no on Microsoft Windows. I use exFAT for compatibility and to write files over 4GB.

---

### Post by yancek on 2020-02-15
Have you installed the hfs utilities on Ubuntu?  I'm not aware of any Linux system that has them installed in a default system. 

[https://askubuntu.com/questions/332315/how-to-read-and-write-hfs-journaled-external-hdd-in-ubuntu-without-access-to-os](https://askubuntu.com/questions/332315/how-to-read-and-write-hfs-journaled-external-hdd-in-ubuntu-without-access-to-os)

---

### Post by TheFu on 2020-02-15
> **yancek said:**
> Have you installed the hfs utilities on Ubuntu?  I'm not aware of any Linux system that has them installed in a default system. 

[https://askubuntu.com/questions/332315/how-to-read-and-write-hfs-journaled-external-hdd-in-ubuntu-without-access-to-os](https://askubuntu.com/questions/332315/how-to-read-and-write-hfs-journaled-external-hdd-in-ubuntu-without-access-to-os)
Yancek - looks like you meant to post this to a different thread.  We're talking about the MS-DOS attrib command for exFAT file here.  At least I thought we were.  

I did a little research and found **mattrib** and **chattr**, but don't think ether will help on exFAT.  mattrib might - seems it does work on vfat stuff, but I didn't see anything about exFAT.

I would probably just write a powershell script and do it on Windows.  I assume the OP tried just naming the files **.filename** already?  That should force exFAT to choose a different name, one that is valid. Probably won't work. Just brainstorming ideas.

---

### Post by yancek on 2020-02-15
> Yancek - looks like you meant to post this to a different thread 

Certainly does, not sure how that happened but I'll see if I can find the other thread?

---

### Post by gagorial on 2020-02-15
Yes, I know that it is possible to hide an folder or file for Linux adding a "." before the name of file or folder and also it is possible creating a text file named .hidden with a list of names from files and folders that I want o requiere to hide.

:) A lot fo thanks for your support.
I am sorry if I do not give the right meaning, I apologise for my english, I know that it is not enough good.

---

