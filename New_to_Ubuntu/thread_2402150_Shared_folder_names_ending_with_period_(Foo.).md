---
title: "Shared folder names ending with period (Foo.)"
date: 2018-09-26
forum: New to Ubuntu
---

### Post by lothian53 on 2018-09-26
Hi,

I have a directory that is a CIFS share from FreeNas. I found that if I create a folder ending in a period, that when I tried to add files or subfolders, I would get a message "mkdir: cannot create directory ‘bar’: No such file or directory"

For example, if I create a folder in the shared directory structure named "Foo.", then when I go and try to add either a directory or a file inside Foo. I get the error message above. I can create folders like this on the local hard drive, and I can sign onto the FreeNAS box and create new folders there ending in period and no problem adding subdirectories.

Is there a known rule about file naming in Ubuntu? 

Thanks

---

### Post by TheFu on 2018-09-26
There are many rules about directory and file names. These are not specific to Ubuntu. They are tied to the file system and to the sharing protocol used.  

There are 3 ways that I know to figure this out.

So, to figure out what is and isn't allowed you can either try it and see what works, or you can go through the documentation for each layer and hope it is correct based on how much that specific project team thinks documentation is important or 3rd, you can go through the source code to REALLY, know what is happening.

The most practical is the try-it method.  But having some general knowledge about what is and isn't allowed will speed that up greatly.

FreeNAS probably uses ZFS for the file system. It also uses a BSD for the OS, not Linux.  My quick research says that ZFS allows any UTF8 characters except / and '\0' because one is the directory separator and the other is how strings are terminated.

CIFS is a file sharing protocol which has multiple implementations.  For example, samba is the most popular, but ZFS has a native implementation internal to ZFS.  It is too buggy to be used on Linux, but I've seen it used on Solaris.  Alfresco (a DMS), also has a CIFS implementation. I've used that too.   Because the main users of CIFS are Windows, it would be expected for the limitations of Windows to apply to the name restrictions.  No :,/,\\, and placement of periods is limited.

For fun, I created a few directories.  ~/fooo./fooo./ using CIFS and the "caja" file manager, I connected to the other machine and created multiple directories through the CIFS interface.  No issues.    So, I would guess that the issue is with the file manager being used. Can't be certain about that, but if you like you can use the smbclient shell program to remove that from the problem.  You can also load other file managers and try each of them.

The 2nd and 3rd levels were created using CIFS.  That's 2 directories and 1 file.
```
$ find fooo.
fooo.
fooo./fooo.
fooo./fooo./test
fooo./fooo./test/ffdsdfs
```

BTW, CIFS isn't case sensitive, so trying to create a directory named foo. when there is a file named FOO. won't work.

Hope this is helpful in some way.

---

### Post by lothian53 on 2018-09-26
Thanks TheFu

I appreciate the feedback.

FreeNAS is on the BSD platform and it hosts the files. I connect to the files via a VM implementation of Ubuntu. I can create files and add directories from the FreeNAS environment without difficulty. I can also do the same from Windows. It seems to be something in Ubuntu that causes me grief. I can create the folder just fine, but when I navigate into it and try to create a file or subfolder that I have  grief. 

I think I will just consider this a lesson learned "Don't create shared folders ending with a period" and move on. It will be fine until some app insists on creating one.

---

### Post by TheFu on 2018-09-26
But I'm not seeing that issue here.

BTW, for Unix-to-Unix file sharing, NFS is the native method, not CIFS. It supports full permissions, users, groups, ACLs, symbolic links, everything you'd expect.

---

### Post by Morbius1 on 2018-09-26
What you want can be done but man it would be convoluted:

Let's start this with a cifs mount ( not a smb / gvfs mount like you would do in a file manager ). As you stated it will not work:
> morbius@mbdg:~$ sudo mount -t cifs //mbdg.local/public /media/Test -o guest,uid=1000
morbius@mbdg:~$ mkdir /media/Test/Foo.
morbius@mbdg:~$ touch /media/Test/Foo./test.txt
touch: cannot touch '/media/Test/Foo./test.txt': No such file or directory

Now let's do this using another option in the mount:
> morbius@mbdg:~$ sudo umount /media/Test
morbius@mbdg:~$ sudo mount -t cifs //mbdg.local/public /media/Test -o guest,uid=1000,nomapposix
morbius@mbdg:~$ mkdir /media/Test/Foo2.
morbius@mbdg:~$ touch /media/Test/Foo2./test.txt
morbius@mbdg:~$


That works ... but ... You and I know that the folder is named Foo2. and we can access it as such because we just created it. But if you look at the mount point in the file manager or do an ls of the mount point Foo2. is displayed as this:
> drwxr-xr-x 2 morbius root    0 Sep 26 14:47  [COLOR=#0000cd]**FHKDT9~B**[/COLOR]
That is called name mangling. You can't fix that from the client. You can only fix that on the server. You would need to add a line in the [global] section of your server:
```
mangled names = no
```
Then restart the samba service.

All in all not worth the trouble. Just don't end files / folders with a dot..

---

### Post by lothian53 on 2018-09-26
Hi Morbius1

That is a great summary. You are right, seems that it is easier to just avoid ending folder names with a dot, but there may be cases where I am not in control of the names and thanks for showing me what  the actual problem is and how to deal with it.

---

