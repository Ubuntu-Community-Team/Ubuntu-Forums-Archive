---
title: "File Copy Behavior w/o File Locks"
date: 2016-08-09
forum: New to Ubuntu
---

### Post by mossyrock on 2016-08-09
It's my understanding that, without additional software, Linux doesn't have a concept of locks on open files.

I'm creating a cron job that will periodically copy all files in a Linux directory (call it the "source" directory) to some other Linux directory (call it the "destination" directory), remove the files in the "source" directory, and then do some things with the files in the "destination" directory.

The "source" directory is a writable, networked share accessible by several Windows machines.  

The Windows machines will write files to this "source" directory periodically, but the timing and length of time required to do the copy is unpredictable.

I am wondering what will happen if the cron job executes and a file in the "source" directory is in the process of being created, i.e., it is being written by a Windows machine and the process ***isn't complete***.

What is Ubuntu's copy command behavior in this circumstance?  Will it wait, skip over the file, or copy an incomplete file?
Likewise, what is the behavior when the remove command is executed and it encounters a file in the process of being written?

Thanks.

---

### Post by SeijiSensei on 2016-08-09
I typically use a "semaphore" file in cases like this.  Can the Windows processes include a command that writes a file to shared resource, say lock.txt, at the beginning of each run?  Then the Linux job could look for the presence of that file before executing the copy and delete it when the copy has finished. If the lock file is present, the script could either "sleep" or just wait until the next cron cycle comes around.

If the files are being written to a Samba share, you have access to more fine-grained locking.  See [https://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/locking.html](https://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/locking.html) for details.  I don't know how to check for an oplock from the Linux side though.  You might be able to handle this by putting the shared resource on a Windows machine and using CIFS to mount it to Linux.  There may then be a way to make Linux CIFS acknowledge the locks imposed by Windows, or it may just do so automatically.  This is just speculation on my part.  I wasn't too successful consulting the CIFS mount page: [https://www.samba.org/samba/docs/man/manpages-3/mount.cifs.8.html](https://www.samba.org/samba/docs/man/manpages-3/mount.cifs.8.html)

There is also a suite of programs in Ubuntu to manage file locking.  Take a look at "[man lockfile-create]("http://linux.die.net/man/1/lockfile-create")" for starters.  I don't know if Samba acknowledges these locks though.  Also, since the files are being created from Windows, Linux locking may not help.

---

### Post by mossyrock on 2016-08-09
SeijiSensi,

Thanks for your reply.  Yes, it is a Samba share.  Thanks also for the links - I'll study this info to see if Samba can help me here.

I was also thinking that I might have to use a "semaphore" technique.  This might be the simplest approach.

---

