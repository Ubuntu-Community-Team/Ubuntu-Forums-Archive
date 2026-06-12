---
title: "dd command for creating single file."
date: 2016-01-04
forum: New to Ubuntu
---

### Post by gardenair on 2016-01-04
hi,
      I want to learn dd command ,it is really very interesting ,quick to create a large file.I want to create a single file which should be of size 1GB (location is /mnt/music)  using dd command.
please guide me how can i create it.

---

### Post by ian-weisser on 2016-01-05
Well, you read the manpage, and then you search these forums for examples, and then you try it on a sample file or disk partition.
dd is not recommended for beginners.

WARNING: dd will happily destroy your system and overwrite all your data. It does exactly what you tell it to do, heedless of your intent or typos.

---

### Post by yetimon_64 on 2016-01-05
> **gardenair said:**
> hi,
      I want to learn dd command ,it is really very interesting ,quick to create a large file.I want to create a single file which should be of size 1GB (location is **/mnt/music**)  using dd command.
please guide me how can i create it.

dd = data destroyer  (if a mistake occurs it will be one nasty affair if dd lives up to its usual reputation ;))

Is that a music collection (collection of multiple files) you want to put into a single file ? If so I'd suggest you tarball the music folder with the "tar" command. It can be compressed further to a single tar.gz file if compression is needed. Once again, check the man page for usage and if it suits we can answer further if needed.

> WARNING: dd will happily destroy your system and overwrite all your  data. It does exactly what you tell it to do, heedless of your intent or  typos.          
+1, Ohh yeah, that is spot on advice OP.

---

### Post by gardenair on 2016-01-05
actually I have created a quota on my partition and I want to check by the command that it works or it eat my whole partition.
Yes man page is best to learn :)

---

### Post by sudodus on 2016-01-05
> **gardenair said:**
> hi,
      I want to learn dd command ,it is really very interesting ,quick to create a large file.I want to create a single file which should be of size 1GB (location is /mnt/music)  using dd command.
please guide me how can i create it.


> **ian-weisser said:**
> Well, you read the manpage, and then you search these forums for examples, and then you try it on a sample file or disk partition.
dd is not recommended for beginners.

WARNING: dd will happily destroy your system and overwrite all your data. It does exactly what you tell it to do, heedless of your intent or typos.

+1 

> **gardenair said:**
> actually I have created a quota on my partition and I want to check by the command that it works or it eat my whole partition.
Yes man page is best to learn :)

These statements tell me that you are no beginner, or at least, soon you will be no beginner :-)

Learning linux usually involves destroying some systems. Therefore it is a good idea to make ***regular backups*** of everything, that you really want to keep. And you should not rely on a backup unless you have tested it. That said it is 'less dangerous' to use dd to write to a regular file (compared to writing to a block device). And now you want to write to a regular file, I suggest the name 'blank' (because it contains only zeros).

```
dd if=/dev/zero of=/mnt/music/blank bs=1M count=1K
```

will create a file with the size 1 G (1 gibibyte, base 2). Depending on the permissions you might need root privileges (use sudo)

```
sudo dd if=/dev/zero of=/mnt/music/blank bs=1M count=1K
```

but use sudo only when necessary, because it makes things more dangerous.

***Edit:*** OOPS: The join date tells me that you joined these forums before I did :oops:

---

### Post by oldfred on 2016-01-05
More info on dd, and even an extra space in command can destroy entire system.

 Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

---

### Post by matt_symes on 2016-01-05
Hi

> **gardenair said:**
> hi,
      I want to learn dd command ,it is really very interesting ,quick to create a large file.I want to create a single file which should be of size 1GB (location is /mnt/music)  using dd command.
please guide me how can i create it.

You want to allocate space for a file quickly ? Forget dd and look into ```
fallocate
```

```
matthew-xu-16-04:/home/matthew:1 % time fallocate -l 1G test.file
fallocate -l 1G test.file  0.00s user 0.00s system 3% cpu 0.132 total
matthew-xu-16-04:/home/matthew:1 % ls -lh test.file 
-rw-rw-r-- 1 matthew matthew 1.0G Jan  5 16:55 test.file
matthew-xu-16-04:/home/matthew:1 % 
```

You can then format the file or whatever you want to it.

Why do you want to create files quickly ?

**EDIT:**
> 
actually I have created a quota on my partition and I want to check by the command that it works or it eat my whole partition.
Yes man page is best to learn 

Somehow i missed this post so you've already answered my question.

Kind regards

---

### Post by sudodus on 2016-01-05
Thanks for the tip about ***fallocate***, *matt_symes* :-)

---

### Post by nerdtron on 2016-01-06
> **matt_symes said:**
> 
You want to allocate space for a file quickly ? Forget dd and look into ```
fallocate
```

```
matthew-xu-16-04:/home/matthew:1 % time fallocate -l 1G test.file
fallocate -l 1G test.file  0.00s user 0.00s system 3% cpu 0.132 total
matthew-xu-16-04:/home/matthew:1 % ls -lh test.file 
-rw-rw-r-- 1 matthew matthew 1.0G Jan  5 16:55 test.file
matthew-xu-16-04:/home/matthew:1 % 
```



Thanks for the tip! It's even easier to remember. You rock! :guitar:

---

### Post by matt_symes on 2016-01-06
Hi

fallocate can be really useful. 

One of the many ways i have used it in the past is to create a temporary swap file on a separate partition or drive if I'm about to run some swap intensive work.

```
matthew-xu-16-04:/home/matthew:0 % fallocate -l 1G swap.tmp
matthew-xu-16-04:/home/matthew:0 % sudo mkswap swap.tmp
[sudo] password for matthew:
Setting up swapspace version 1, size = 1024 MiB (1073737728 bytes)
no label, UUID=571a6b2a-428d-4353-8c59-10a960e12e39
matthew-xu-16-04:/home/matthew:0 % sudo chmod 600 swap.tmp
matthew-xu-16-04:/home/matthew:0 % sudo chown root:root swap.tmp
matthew-xu-16-04:/home/matthew:0 % sudo swapon swap.tmp
matthew-xu-16-04:/home/matthew:0 % swapon -s
Filename                                Type            Size    Used    Priority
/dev/sda3                               partition       3745788 283744  -1
/home/matthew/swap.tmp                  file            1048572 0       -2
matthew-xu-16-04:/home/matthew:0 % sudo swapoff swap.tmp
matthew-xu-16-04:/home/matthew:0 % 
```

Kind of a digression from the OP's query but i hope it'll help somebody out.

Kind regards

---

