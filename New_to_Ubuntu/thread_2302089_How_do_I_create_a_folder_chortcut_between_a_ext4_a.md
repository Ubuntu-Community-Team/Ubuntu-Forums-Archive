---
title: "How do I create a folder chortcut between a ext4 and fat32 partition?"
date: 2015-11-07
forum: New to Ubuntu
---

### Post by kd0mlv on 2015-11-07
Hello all. I'm both new to Ubuntu and the forum so please pardon my ignorance. I am currently running Ubuntu 14.04 and have it duel booted with Windows 7 and also some other partitions on one hard drive. I have been experimenting with creating short cut folders between my several different partitions and ran into a problem. When I try to create a short cut from partition formatted with fat32 to my Ubuntu (ext4) partition using the "make link" option, I get an error message that reads: "the target does not support symbolic link." Is there a way to get around this error? Thank you guys so much! Stay frosty,  Jordan

---

### Post by TheFu on 2015-11-07
Yes. Use a Linux file system.
Also, the proper name is "symbolic link" - some file systems support it and some do not. FAT32 does not.

---

### Post by Morbius1 on 2015-11-07
I'm not sure what you are trying to do.

You can create a link to the fat32 partition from the linux partition:
> tester1@vubuntu1404:~$ ln -s /DataF/TestFolder /home/tester1/Public
tester1@vubuntu1404:~$ ls -al /home/tester1/Public
total 8
drwxrwxrwx  2 tester1 tester1 4096 Nov  7 14:58 .
drwxr-xr-x 18 tester1 tester1 4096 Nov  7 14:57 ..
[COLOR=#0000cd]lrwxrwxrwx  1 tester1 tester1   17 Nov  7 14:58 TestFolder -> /DataF/TestFolder[/COLOR]
What you cannot do is the opposite:
> tester1@vubuntu1404:~$ ln -s /home/tester1/Music /DataF
ln: failed to create symbolic link &#8216;/DataF/Music&#8217;: Operation not permitted

DataF is a FAT32 partition and TestFolder is a directory on that partition.

---

