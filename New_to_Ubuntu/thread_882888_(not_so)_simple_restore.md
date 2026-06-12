---
title: "(not so) simple restore"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by Piddell on 2008-08-07
My upgrade from 6.06 to Heron was causing some issues, so I was advised to do an install from scratch......  You can just see where this is going!

I installed simple backup and restore as they had 5 stars on the add remove application list (I did try keep but could not get anything working there)

So I thought I had a nice backup, but the "simple" restore program fails to see the backed up file as real.
"no backups found in the target directory"
it is pointing to the correct location!

Looking at the file now it shows ?files and is owned by root. 

a little worried I tried the following
[email]root@fuzzylogic:/media/disk-1/2008-07-30_16.42.05.385930.phill-desktop.ful[/email]# ls
excludes  files.tgz  fprops  packages
[email]root@fuzzylogic:/media/disk-1/2008-07-30_16.42.05.385930.phill-desktop.ful[/email]# ls -l
total 38753636
-rw-r----- 1 root ssh         221 2008-07-30 16:42 excludes
-rw-r----- 1 root ssh 39642857472 2008-07-31 07:48 files.tgz
-rw-r----- 1 root ssh     2054166 2008-07-30 16:43 fprops
-rw-r----- 1 root ssh       40960 2008-07-30 16:42 packages
[email]root@fuzzylogic:/media/disk-1/2008-07-30_16.42.05.385930.phill-desktop.ful[/email]# 

so it LOOKS like there are a bunch of files inside, but how do I extract the useful bits?

Thanks

Phill

---

### Post by Piddell on 2008-08-08
bump ;-)

---

### Post by Tha-Fox on 2008-08-08
I'm also interested. I've done my backups with sbackup and if they are useless, I'd like to know it before something terrible happens.

---

### Post by rbmorse on 2008-08-08
I have restored files from a sbackup store successfully using interface at system > Administration > Simple Backup Restore. 

It was some time ago and I don't remember much beyond it worked as expected except locating the files I needed was a chore. Someone ought to write an sbackup interface for Beagle.

---

### Post by Piddell on 2008-08-09
having a look at the backup files they were owned by root, so I chown'd it back to me and made it fully read/write etc. 
If I try and copy or do anything with the files I just get permission denied errors.

 ls -l
total 10732
drwxrwxrwx   2 phill phill    4096 2008-07-30 16:43 2008-07-30_16.42.05.385930.phill-desktop.ful
drwxrwxrwx   2 phill phill    4096 2008-08-01 10:25 2008-08-01_10.23.37.509779.phill-desktop.ful
drwxr-xr-x   2 phill phill    4096 2008-05-30 12:59 alpacas
drwxr-xr-x   2 phill phill    4096 2008-07-25 09:02 appledene

Am I heading in the wrong direction here?

---

### Post by sdennie on 2008-08-09
I frequently use the simple backup restore feature and have never had any problems.  Is it possible that your problem is related to mount options or something of that nature?  Regardless, simple backup uses tar to store things so, assuming the data is not corrupt, you can always grab things out of the backup manually.  To see what's in the backup, try:

```

tar tvf files.tgz

```

To extract a particular file:

```

tar xvf files.tgz path/to/file

```

I don't have my backup SD card around but, I assume those commands will work just fine.

---

### Post by Piddell on 2008-08-10
Thanks Vor,
I still don't get it, I'm getting permission errors, not corruption errors.
same error on the other files.
I just noticed Root is the owner 
so I changed it back to me, and can list all the files just fine

So in theory I could extract all the files I wanted, but I don't know where to put the ones I'm interested in!  Passwords and emails mainly.  can I just copy everything out and all will be well?  Or am I in danger of having to start again?

Phill

---

