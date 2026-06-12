---
title: "Permission Denied"
date: 2012-01-01
forum: Programming Talk
---

### Post by vanangamudi on 2012-01-01
[-( I cannot help myself.... tried and tired of compiling and executing in Code::Blocks , Anjuta, Command-line tools. I'm using Ubuntu 10.10...
[IMG]https://lh3.googleusercontent.com/-88Su3Wo-JOQ/TwCeb8xj6YI/AAAAAAAAAPc/SdFLcUG1itQ/s800/Screenshot.png[/IMG]

---

### Post by samjh on 2012-01-01
Have you got the correct permissions to run foo?

Do this:
```
ls -l /media/Projects/C/foo/foo/bin/Debug/foo
```

The output will show something like [FONT="Courier New"]-rwxrwxr-x[/FONT].  If you see no [FONT="Courier New"]x[/FONT] anywhere in that part, it means the file has no permission to run under your current login name or login group.

You will need to do this to give it permission:
```
chmod +x /media/Projects/C/foo/foo/bin/Debug/foo
```

---

### Post by sisco311 on 2012-01-01
Also some file systems (FAT, NTFS) do not support Unix/Linux file permissions. So, you can't change the permissions of individual files located on such file systems. You can only set the permissions for all files and directories at mount time.

Oh, also make sure that the partition is not mounted with the noexec mount option.

```
sudo fdisk -l
mount
```

---

### Post by Petrolea on 2012-01-01
As sisco311 already said, it's probably the file system. Your path starts in /media, where devices like USB flash drives are located and I guess that whatever the device is, it doesn't use a file system that supports Unix's file permissions. 

It could also be that you simply don't have permissions to run that file, but I doubt that (maybe you created the file as root and can't run it as normal user?).

---

