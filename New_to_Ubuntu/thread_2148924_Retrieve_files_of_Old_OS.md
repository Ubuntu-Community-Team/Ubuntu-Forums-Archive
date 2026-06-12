---
title: "Retrieve files of Old OS"
date: 2013-05-27
forum: New to Ubuntu
---

### Post by adityaharish on 2013-05-27
I have installed Ubuntu 12.04 over another version of Ubuntu i.e I have two ubuntu Os's with same version number.

Now, I can only login into the new version, I cannot see the old version . This is what I get when I run 

[I]sudo fdisk -l
[/I]
 The Output is :
 
   Device Boot      Start         End      Blocks   Id  System
 /dev/sda1    *        2048   577941500   288969726+  83  Linux
 /dev/sda2        577941502   976771071   199414785    5  Extended
 /dev/sda5        968568832   976771071     4101120   82  Linux swap / Solaris
 /dev/sda6        577941504   968568831   195313664   83  Linux 


So, Please help me in retreiving the files of  my old OS . 
I think /dev/sda1  is my old one & /dev/sda6 is my new one.

---

### Post by sudodus on 2013-05-27
You are probably right, but if you mount all partitions that you can mount and run ```
df
``` and post the output within code tags
like this

[noparse]```
output
```[/noparse]
 
to get output like this
 
```
output
```

it will be easier to read (columns will remain as columns) and be sure your data is there.

-o-
   
Normally you can mount a partition with the file browser. Just click on its icon in the left panel. Anyway, after mounting the files and directories should be available for reading, copying, backup ...

---

### Post by adityaharish on 2013-05-28
The command is 
code :
            df

The Output is :
Code :
[B]shraddesh@shraddesh-Samsung-Desktop-System:~$ df
Filesystem     1K-blocks       Used    Available Use% Mounted on
/dev/sda1        284435028 3897312  266089232   2%    /
udev                          2007612                 4        2007608   1%   /dev
tmpfs              805968        796          805172   1%    /run
none                   5120                 0               5120   0%    /run/lock
none                          2014912              80       2014832   1%    /run/shm
/dev/sda1    284435028 3897312 266089232   2%   /media/home
/dev/sda6    192247388 2460520 180021188   2%   /home
shraddesh@shraddesh-Samsung-Desktop-System:~$ [/B]

---

### Post by deadflowr on 2013-05-28
You only have one Operating System.

/dev/sda1 is the OS
/dev/sda2 is an extended partition. It holds the logical partition which are
/dev/sda5 is your swap partition
/dev/sda6 is your home partition.

So it's no wonder you can't boot a different system.

If you had files on the old, which is /dev/sda1 then they might be gone forever.
It really depends on how you install the new system.
Give us a run down of how you installed the second time.

---

### Post by sudodus on 2013-05-28
> **deadflowr said:**
> You only have one Operating System.

/dev/sda1 is the OS
/dev/sda2 is an extended partition. It holds the logical partition which are
/dev/sda5 is your swap partition
/dev/sda6 is your home partition.

So it's no wonder you can't boot a different system.

If you had files on the old, which is /dev/sda1 then they might be gone forever.
It really depends on how you install the new system.
Give us a run down of how you installed the second time.

+1

I agree with the analysis of *deadflowr*. The old files might be gone forever. It depends on how you installed the second time.

If you formatted /dev/sda1 and/or /dev/sda6, everything is gone. Otherwise many files are overwritten, but those old files with unique names should stay. So there is a chance that your private files, documents, pictures etc might be possible to find the normal way with the file browser.

-o-

If there are some very valuable files, that were not backed up, you can look for them with ***PhotoRec***, that can find files from the data on the disk, without any directory or file name. But it means a lot of work.

---

### Post by adityaharish on 2013-05-28
Thanks all .. I'll se what I can I do to get the old versions...

---

