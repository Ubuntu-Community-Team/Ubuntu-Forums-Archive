---
title: "Systems programming in unix, validating the super block my checking the magic number?"
date: 2012-03-05
forum: Programming Talk
---

### Post by venom104 on 2012-03-05
[B]
[/B]

                   Here is my code [http://pastebin.com/F6SnCrHL](http://pastebin.com/F6SnCrHL)

here is how you generate a fake file system

dd if=/dev/zero of=ext2Test1.bin bs=4096 count=1024
Approach one (Tak's scenic route)
do the following as root
losetup /dev/loop0 ext2Test1.bin
mke2fs /dev/loop0
mkdir /media/fake
mount /dev/loop0 /media/fake
Approach two (I5)
/sbin/mkfs.ext2 -F -b 4096 ext2Test1.bin # -b controls the block size -i for inode size
mkdir /media/fake
(as root) mount ext2Test1.bin /media/fake
mkdir /media/fake/testdir
touch /media/fake/testdir/testfile
... # do more stuff to the fake FS
cd # make sure you are not in the mounted fake FS
umount /media/fake
Tak's scenic route
losetup -d /dev/loop0


Now the question I have is regarding the magic number. I understand that it's at offset 1080 ( [http://superuser.com/questions/239088/whats-a-file-systems-magic-number-in-a-super-block](http://superuser.com/questions/239088/whats-a-file-systems-magic-number-in-a-super-block)  ), but what I'm doing isn't working. My program is outputting garbage,  from what I can tell, it has to deal with the read operation.

How can I fix my program to get the magic number?


Note: it goes pretty well without saying that you need to be running a  UNIX like OS for this to work. You also run the program by doing this  /pathtoprogram/programname /pathto(.bin)file

---

