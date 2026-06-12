---
title: "user jobs"
date: 2013-06-23
forum: New to Ubuntu
---

### Post by deanie44 on 2013-06-23
Hi everyone.  I have successfully configured a directory in the storage groups of mythtv.  I would like to create a user job so that all the tv shows of Castle that i record be copy to that directory.  i have read many articles, but I do not understand how to type the command.  How do I type a command for the tv show to be copied to /media/Mythtv Recordings/Castle.  Any help will be appreciated.  mary

---

### Post by 2F4U on 2013-06-23
The general format of the copy command would be

cp /source_folder/file_name /destination_folder

So, in your case

cp /source_folder/Castle* /media/Mythtv\ Recordings/Castle

This assumes that the recordings begin with Castle, else add a different substring before *. The character "\" in the destination path is needed because the name of the folder has a blank in it.

---

### Post by deanie44 on 2013-06-23
2F4U, thank you for answering my post.  This maybe a stupid question, but what is the source folder?  mary

---

### Post by howefield on 2013-06-23
> **deanie44 said:**
> This maybe a stupid question, but what is the source folder?  mary

Your starting folder, the one you are copying from..

---

### Post by dino99 on 2013-06-23
> **deanie44 said:**
> 2F4U, thank you for answering my post.  This maybe a stupid question, but what is the source folder?  mary

its saying: copy FROM (original download files folder) TO (destination folder)
the source folder is the one you have chosen to download the files

---

### Post by deanie44 on 2013-07-07
Hi howefield.  I have been trying to get this user job to execute, but will not run.  Here is how i have it written:

copy to sdb4
cp/var/lib/mythtv/recordings/test*/media/sdb4/test*
is that the correct way to write it?  The sdb4 is a partition.

---

### Post by howefield on 2013-07-07
No it isn't.

You need a space between the command and the source, then between the source and the destination.

```
cp /var/lib/mythtv/recordings/test* /media/sdb4/test
```

This assumes that you want to copy all files in the recordings folder that start with test and copy it to /media/sdb4/test/.

If you get an error in the terminal when you run the command, screenshot it and post it here.

---

### Post by deanie44 on 2013-07-07
Hi Howefield.  I am not using the terminal.  It is a user job in mythtv backend. I would like to have all my recordings to be copied to sdb4.  How would I set that to be executed.  thank you.  deanie44

---

