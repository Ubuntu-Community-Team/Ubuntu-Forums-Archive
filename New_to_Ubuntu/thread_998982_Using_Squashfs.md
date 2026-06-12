---
title: "Using Squashfs?"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by zaarch on 2008-12-01
Hi,

Quick question about using squashfs? After one creates a .sqsh file of some directory, do I delete the original directory or do i have to keep it on the hdd and set up the /etc/fstab to use the .sqsh file for read only purposes ?

Any info will be appreciated!

Thanks,
Zaarch

---

### Post by Achetar on 2008-12-03
*bump*

I would like to know about this too.

---

### Post by chirilas on 2011-05-30
> **zaarch said:**
> Hi,

Quick question about using squashfs? After one creates a .sqsh file of some directory, do I delete the original directory or do i have to keep it on the hdd and set up the /etc/fstab to use the .sqsh file for read only purposes ?

Any info will be appreciated!

Thanks,
Zaarch

When you create a squashfs file of a given directory, say the following scenario: you want to make a squash of directory **/home/user1** and want the squash file to be located in **/home/squashes** and the squash file system file's name is **squash_file_system_file.fs** you do:

```
$cd /home
$mkdir squashes
$cd squashes
$mksquashfs /home/user1 squash_file_system_file.fs
```

this will put the contents of folder **/home/user1** into the file **/home/squashes/squash_file_system_file.fs** without doing anything else to /home/user1. Now you can feel free to delete /home/user1 cause the contents of it will still be in the suashfs file, but probably just empty it and leave it empty so you don't have to recreate it every time at boot. 

In order to make it mount it automatically at boot time, you edit **/etc/fstab** and add the following line in it:

```
/home/squashes/squash_file_system_file.fs  /home/user1       squashfs        ro,defaults     0 0
```

And unless I made some horrible mistake, everything should work out fine =). For your own reading pleasure, here's a very useful link: [http://www.linuxdoc.org/HOWTO/SquashFS-HOWTO/creatingandusing.html]("http://www.linuxdoc.org/HOWTO/SquashFS-HOWTO/creatingandusing.html") where you can read the above and more about how to mount and tweak squashfs files.

Hope this helped,
Stefan

---

