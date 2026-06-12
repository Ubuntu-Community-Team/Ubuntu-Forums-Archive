---
title: "Create an ext2 or ext3 iso from directory in bash"
date: 2008-01-25
forum: Programming Talk
---

### Post by thehigherentity on 2008-01-25
I'm trying to create an iso files from a directory on my computer.
I know i can do this with the following command

$ mkisofs -r /media/backup/foo > foo.iso

However I want to create an iso with a ext2 or ext3 file system?
I have tried the following but had no luck

$ mkfs -t ext3 /media/backup/foo > foo.iso

If someone could point me in the right direction that would be great.

:)
Ste

---

### Post by jeffus_il on 2008-01-25
mkisofs makes an iso filesystem, so it can't be another type of filesystem as well.

What do you want to achieve?

---

### Post by rosegarden78 on 2008-01-25
Interesting...thanks.

---

### Post by thehigherentity on 2008-01-25
I have created a bash script that takes 2 inputs
1) a directory
2) an iso file name

what it does then is creates and encrypts the iso from the directory contents.

basically it does the following command.

$  mkisofs -r "${DIR}" | aespipe -e aes256 > "${ISO}"

Because of the directory contents and file sizes I would like to ad an option to just ext2 or ext3 file system to the script. this is where i run into problems is doesn't seem possible to do that in a single line like i can with mkisofs? 

I know i can create an iso by using dd and then formating it with the required file system using mkfs -t ext3 or mkfs -t ext2, then I can encrypt it through /dev/loop0

However I was hoping there was a way i could just do all that in one line like I can with the iso9660 format above?

thanks for any help you can give.
Ste

---

