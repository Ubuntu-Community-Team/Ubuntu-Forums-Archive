---
title: "Command Line beginner"
date: 2012-05-22
forum: New to Ubuntu
---

### Post by seeker.k3 on 2012-05-22
I have a feeling there might be something wrong with this question, but here goes. I'm taking my first steps with the command line, and I want to be able move into different volumes (and move files to volumes). I've made partitions on my hard drive for storage, which is different from the partition for Xubuntu and my home directory (and I've got a dual boot with Win7). Is there any way to change directories to get on to a different partition?
Thanks as always.

---

### Post by mastablasta on 2012-05-22
here is a nice free e-book: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)
 
i think cd is change directory.
 
i am more of a gui person. perhaps you could explore the option of midnight commander a gui tool that works in terminal.
 
also here are nice cheat sheets: [http://alinuxblog.wordpress.com/2008/08/23/10-must-have-linux-not-only-cheat-sheet/](http://alinuxblog.wordpress.com/2008/08/23/10-must-have-linux-not-only-cheat-sheet/)

---

### Post by kmyram on 2012-05-22
> **seeker.k3 said:**
> I'm taking my first steps with the command line, and I want to be able move into different volumes (and move files to volumes).

A soft start would be to use **Midnight Commander** ([FONT="Courier New"]sudo apg-get install mc[/FONT]) and get a good feel for your folder structure.
MC has some nice builtin tools for moving files, directories and much more. It's quick to move around in even the most complex structures IMHO and I couldn't live without it :)

/Kasper

---

### Post by swamyuefa on 2012-05-22
> **mastablasta said:**
> here is a nice free e-book: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)
 
i think cd is change directory.
 
i am more of a gui person. perhaps you could explore the option of midnight commander a gui tool that works in terminal.
 
also here are nice cheat sheets: [http://alinuxblog.wordpress.com/2008/08/23/10-must-have-linux-not-only-cheat-sheet/](http://alinuxblog.wordpress.com/2008/08/23/10-must-have-linux-not-only-cheat-sheet/)

thanks for the book buddy

---

### Post by cortman on 2012-05-22
> **seeker.k3 said:**
> I have a feeling there might be something wrong with this question, but here goes. I'm taking my first steps with the command line, and I want to be able move into different volumes (and move files to volumes). I've made partitions on my hard drive for storage, which is different from the partition for Xubuntu and my home directory (and I've got a dual boot with Win7). Is there any way to change directories to get on to a different partition?
Thanks as always.

Extra partitions are always mounted in /media. So if I have a partition mounted as "winstuff", I would type

```
cd /media/winstuff
```

To change directories to it.
For info on the command line see the link in my signature.
Good luck!

---

### Post by buzzingrobot on 2012-05-22
There's an excellent sticky on command line use at the very top of this forum.

Partitions are mapped to directories.  When you installed, if you created a "/dev/mymusic" partition, a "cd /mymusic" should get you there.

---

### Post by seeker.k3 on 2012-05-23
A gui person---hmmm?

Thanks for all this helpful information.

Just one follow up question, though: the other volumes aren't initially present in /media when I use the CLI, but I can solve that (for the purpose of the exercise) by clicking on each volume in file manager, and then accessing them using the CLI. How can make them there using the CLI?

Cheers

---

### Post by nothingspecial on 2012-05-23
Assuming that the partitions are ntfs, then first you need to create a directory to mount them to with mkdir, eg

```
sudo mkdir /media/windows /media/shared
```

Then you need to know which dev/sd?? they have been assigned, to do this type ```
sudo fdisk -l
```

Under the device feild at the beginning of each line you will see /dev/sd??

Then mount them like so

```
sudo mount -t ntfs /dev/sd?? /media/windows
sudo mount -t ntfs /dev/sd?? /media/shared
```

---

### Post by mastablasta on 2012-05-23
mount command mounts other media volumes.
 
use 
 
```
 
man mount

``` 
 
to see the usage for the command.
 
i think other filetypes (such as NTFS) would need to be mounted to a point.
 
[http://linux.about.com/od/commands/a/blcmdl8_mountx.htm](http://linux.about.com/od/commands/a/blcmdl8_mountx.htm)
 
unmount would, well, unmount it :-)

---

### Post by seeker.k3 on 2012-05-23
I'm very grateful for your help.
Thanks all.

---

