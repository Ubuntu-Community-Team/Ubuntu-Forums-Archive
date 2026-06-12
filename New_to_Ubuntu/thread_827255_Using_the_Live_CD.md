---
title: "Using the Live CD"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Sou Portugues on 2008-06-12
So I am using a Live CD of Dapper (6-2006) to try and restore my girlfriends computer. I accidentally deleted the partition, but caught it before we lost the files. I backerd up her whole drive onto my NTFS external, and reformatted and reloaded windows onto her drive (also NTFS, internal to the laptop). What I want to do now is just delete all the info in the NTFS partition of her drive, and replace it with the saved info from my drive.

The problem is this, since this is a live cd, I dont have acess to her drive, or fstab, or mtab, or really anything to do with the way this session operates (not much useful at least). I don't have the ntfs-3g on this disk (too old) and cant burn another live CD, because I am using the only drive, and the drivers for windows to jump online OR burn a cd arent functioning properly

Here is my question:
Is there a way to make her internal drive writeable so I can delete the info and copy over the old info?
Thanks

---

### Post by pytheas22 on 2008-06-12
Provided you have Internet access when using the live CD, you should be able to just download the ntfs driver during the live session:
```

sudo apt-get install ntfs-3g
```

I'm not positive how well the build of the driver for Feisty works, but I know at least that it existed and allows you to read files.  You could also change your sources list to use a later repository to get a better version of the ntfs driver, or build it from source.

You could also try installing Linux onto a USB drive pen since you can't burn a CD.  There are plenty of guides online for doing this with different kind of distributions.  Also I think there's a way (you could do it in Mandriva, at least) to be able to remove the live CD temporarily while you burn CDs in the live session, provided you have at least 512 megabytes of RAM.  I don't know how to do it myself but if you search you should find it.

---

