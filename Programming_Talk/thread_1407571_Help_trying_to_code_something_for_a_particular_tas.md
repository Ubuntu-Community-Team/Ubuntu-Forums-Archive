---
title: "Help trying to code something for a particular task"
date: 2010-02-15
forum: Programming Talk
---

### Post by sarang on 2010-02-15
I was trying to create something that would serve the following purpose:

I like taking pictures and I'd like to archive my original picture files to a particular folder and then set them all to be read-only / immutable so that image editing software cannot save changes to the original images. 

I could write a script that copies images from my memory card to the archive folder and changes permissions, but I want something that's more transparent, something like a umask for a directory: I should be able to copy files into the archive directory as a regular user using any tool - gui or command or remotely or whatever and as soon as the files are copied, they should have permissions set to read-only for non-root users.

One way I can think of is to use the inotify mechanism of recent kernels to monitor my archive folder and set permissions on new files. Do you folks have a better idea? If not, what would be the easiest way of implementing the inotify thing?

---

### Post by meastwood on 2010-02-16
Hi this may help.

First install 'inotify-tools' package - it is available in Ubuntu.

Created a test dir and a test file to show default perms.

```
mark@ub-desktop:~/test1$ touch photo1.png
mark@ub-desktop:~/test1$ ls -al
total 16
drwxr-xr-x  2 mark mark  4096 2010-02-16 19:03 .
drwxr-xr-x 64 mark mark 12288 2010-02-16 19:02 ..
**-rw-r--r--  1 mark mark     0 2010-02-16 19:03 photo1.png**
```

***Watch script:***
```
#!/bin/sh

dir_to_watch="/home/mark/test1"

# Watch for files created in test1 directory
# When a create event is received pass file name to while loop
inotifywait -mq -e create --format %f $dir_to_watch | while read file
do
   # change perms on the file
   chmod 440 $dir_to_watch"/$file"
done 
```

**Run script:**
mark@ub-desktop:~$ ./ch_perms.sh


**In another window:**
mark@ub-desktop:~/test1$ touch photo2.png
mark@ub-desktop:~/test1$ touch "photo 3 .png"

mark@ub-desktop:~/test1$ ls -al
total 16
drwxr-xr-x  2 mark mark  4096 2010-02-16 19:05 .
drwxr-xr-x 64 mark mark 12288 2010-02-16 19:05 ..
-rw-r--r--  1 mark mark     0 2010-02-16 19:03 photo1.png
[B]-r--r-----  1 mark mark     0 2010-02-16 19:04 photo2.png
-r--r-----  1 mark mark     0 2010-02-16 19:05 photo 3 .png[/B]

You would probably want to set something like 'ch_perms.sh' to run in the background, run from startup and also add some error checking.

---

