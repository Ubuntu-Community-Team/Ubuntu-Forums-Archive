---
title: "help &quot;command not found&quot;"
date: 2010-12-03
forum: Programming Talk
---

### Post by yjqzou on 2010-12-03
i just programed a helloworld.c
here is my codes:
#include <stdio.h>

int main(void)
{
  printf("Hello,Linux Programming World!\n");
  return 0;
}
i compile it with command below:
gcc helloworld.c -o helloworld

But when i do 
sudo ./helloworld
here is an error:
"command not found"
PS:i do it in the local directory.
is there someone help?
thanks.

---

### Post by roccivic on 2010-12-03
You shouldn't use sudo...

Do you get an error if you drag-and-drop your executable in the console?

---

### Post by CharlesA on 2010-12-03
Don't use sudo. Also make sure it has execute permission.

---

### Post by yjqzou on 2010-12-04
> **CharlesA said:**
> Don't use sudo. Also make sure it has execute permission.
thank you very much.
i make it have the execute permission with the following command:
sudo chmod +x a.out
then,it can run.

and i found another problem with ubuntu10.10 that wei can change the file's execute permission.
that is:
if i do the following command in ntfs filesystem
sudo chmod +x a.out
there is not any changes.
i must do copy a.out in ext3 filesystem.

---

### Post by yjqzou on 2010-12-04
> **roccivic said:**
> You shouldn't use sudo...

Do you get an error if you drag-and-drop your executable in the console?

thank you very much for your reply.
i had solve this problem.
the detail are in upstair.

---

### Post by CharlesA on 2010-12-04
NTFS partitions do not support linux file permissions.

---

### Post by Vox754 on 2010-12-04
> **yjqzou said:**
> ...

and i found another problem with ubuntu10.10 that wei can change the file's execute permission.
that is:
if i do the following command in ntfs filesystem
sudo chmod +x a.out
there is not any changes.
i must do copy a.out in ext3 filesystem.

As mentioned, NTFS does not natively support Unix permissions.

However, when they are mounted as a "fuse" filesystem, they do get permissions, which remain the same until you unmount the partition.

It seems NTFS partitions that are mounted automatically in Ubuntu 10.10, that is, which do not have an entry in "/etc/fstab", have no execute permissions. If you look at the output of "ls -l" you will see something like
```

-rw-------  file

```

I believe this changed from 10.04. In that version, NTFS did have execute permission by default.

If you mount the partition yourself, or add the appropriate "exec" option to "fstab", it should allow you to run programs
```

sudo mount /dev/sda2 /media/NTFS  # it may work just like this
sudo mount /dev/sda2 /media/NTFS -o exec,umask=022  # or add options as desired

```
```

-rwxr-xr-x  file

```

---

### Post by trent.josephsen on 2010-12-04
This really raises another question, namely, "Why on Earth would you put executables meant to be run on Linux on an NTFS partition?"

Also, you don't need to be root to change permissions on a file in a directory you own.  (Don't use sudo for chmod.)

---

### Post by Vox754 on 2010-12-05
> **trent.josephsen said:**
> This really raises another question, namely, "Why on Earth would you put executables meant to be run on Linux on an NTFS partition?"


Without going into much detail, there are some valid reasons.

For example, if you dual boot, you may want to have access to files from both Linux and Windows, which is possible with FAT and NTFS, and not so easy with Linux filesystems. Drivers for ext2 (ext3, ext4) exist in Windows, I know. But still, NTFS may be simpler, since nothing special needs to be done.

If your code is truly portable, it should compile and run effortlessly in both systems.

Another example is TeXlive, which provides executables for many different architectures in the same tree. Having a common filesystem which many OSes can read, write and execute files from is useful in this case.

Personally, I'm a little uneasy with these new ext4, btrfs, et al. filesystems because I don't know if support for them in Windows can be implemented fully. Not a big deal either, just saying.

---

### Post by unknownPoster on 2010-12-05
> **Vox754 said:**
> 

If your code is truly portable, it should compile and run effortlessly in both systems.



True, but then why would you store Linux ELF files on NTFS partitions or Windows executable on Linux file-system partitions. I only see this being an optimal solution for preparing software packages for distribution.

---

