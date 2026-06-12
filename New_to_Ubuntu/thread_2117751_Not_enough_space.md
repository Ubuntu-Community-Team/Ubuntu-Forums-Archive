---
title: "Not enough space?"
date: 2013-02-19
forum: New to Ubuntu
---

### Post by 101kitty on 2013-02-19
[http://i49.tinypic.com/a3z5go.png](http://i49.tinypic.com/a3z5go.png)

```
Direct Link for Layouts: http://i49.tinypic.com/a3z5go.png
```

---

### Post by bantuvez on 2013-02-19
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)
[https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk](https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk)

---

### Post by 101kitty on 2013-02-19
is there a program i can use, i'm doing everything but its still not working.

```
kitty@ubuntu:~$ cd ~/Downloads/wubi-resize-1.6
bash: cd: /home/kitty/Downloads/wubi-resize-1.6: No such file or directory
kitty@ubuntu:~$ cd ~/Downloads/wubi-resize1.6
bash: cd: /home/kitty/Downloads/wubi-resize1.6: No such file or directory
kitty@ubuntu:~$ cd ~/Downloads/wubi-resize-1.6
kitty@ubuntu:~/Downloads/wubi-resize-1.6$ bash wubi-resize.sh --help
Usage: sudo bash wubi-resize.sh [options] | [size in GB]
       e.g. sudo bash wubi-resize.sh --help (print this message)
       e.g. sudo bash wubi-resize.sh 10 (resize to 10GB)
       e.g. sudo bash wubi-resize.sh --version (print version number)

Increase the wubi virtual disk size  
  -h, --help              print this message and exit
  --version               print the version information and exit
  -v, --verbose           print verbose output
  --max-override          ignore maximum size constraint of 32GB
  --resume                resume previous failure due to copy errors

Note: you have to complete the resize by booting into windows and
renaming the root.disk to OLDroot.disk and new.disk to root.disk
before rebooting. Only delete the old root.disk once you are sure
the resize worked. 

This script will merge separate virtual disks into a single root.disk
(and adjust the /etc/fstab accordingly). 
Host partitions that are FAT32 are not supported.

If the script exits due to rsync copy failures, for example, a corrupt
file, it is possible to correct the problem and then resume the script
without recreating the new virtual disk and recopying everything.
Rerun the script with the --resume option. In this case the size parameter
is ignored, but the script will offer to resize the new disk if too small.
kitty@ubuntu:~/Downloads/wubi-resize-1.6$ sudo bash wubi-resize.sh 10
[sudo] password for kitty: 
wubi-resize.sh: The new size (10 GB) isn't sufficient to hold your
wubi-resize.sh: existing install (18 GB) plus a freespace buffer
kitty@ubuntu:~/Downloads/wubi-resize-1.6$
```

---

### Post by aspireone722 on 2013-02-19
could you expand your question a little?

---

### Post by 101kitty on 2013-02-19
Is there away to install linux though linux and copy all my files over from the current linux os than i'm using?

---

### Post by Mark Phelps on 2013-02-19
You're doing it right, you're just not giving the command enough space.  The existing install claims it is 18GB, you only gave it a size parameter of 10.  Try the command with a value of 28.

---

### Post by 101kitty on 2013-02-19
ok, thank you, i think i got it working.

---

### Post by 101kitty on 2013-02-19
```
kitty@ubuntu:~$ cd ~/Downloads/wubi-resize-1.6
kitty@ubuntu:~/Downloads/wubi-resize-1.6$ bash wubi-resize.sh --help
Usage: sudo bash wubi-resize.sh [options] | [size in GB]
       e.g. sudo bash wubi-resize.sh --help (print this message)
       e.g. sudo bash wubi-resize.sh 10 (resize to 10GB)
       e.g. sudo bash wubi-resize.sh --version (print version number)

Increase the wubi virtual disk size  
  -h, --help              print this message and exit
  --version               print the version information and exit
  -v, --verbose           print verbose output
  --max-override          ignore maximum size constraint of 32GB
  --resume                resume previous failure due to copy errors

Note: you have to complete the resize by booting into windows and
renaming the root.disk to OLDroot.disk and new.disk to root.disk
before rebooting. Only delete the old root.disk once you are sure
the resize worked. 

This script will merge separate virtual disks into a single root.disk
(and adjust the /etc/fstab accordingly). 
Host partitions that are FAT32 are not supported.

If the script exits due to rsync copy failures, for example, a corrupt
file, it is possible to correct the problem and then resume the script
without recreating the new virtual disk and recopying everything.
Rerun the script with the --resume option. In this case the size parameter
is ignored, but the script will offer to resize the new disk if too small.
kitty@ubuntu:~/Downloads/wubi-resize-1.6$ sudo bash wubi-resize.sh 30
[sudo] password for kitty: 
wubi-resize.sh:  A new virtual disk of 30 GB will be created. Continue? (Y/N)
n
wubi-resize.sh: Request aborted
kitty@ubuntu:~/Downloads/wubi-resize-1.6$ sudo bash wubi-resize.sh 50
wubi-resize.sh: The new disk cannot exceed 32 GB unless the
wubi-resize.sh: --max-override option is used (not recommended).
kitty@ubuntu:~/Downloads/wubi-resize-1.6$ sudo bash wubi-resize.sh 30
wubi-resize.sh:  A new virtual disk of 30 GB will be created. Continue? (Y/N)
y
wubi-resize.sh: Creating new virtual disk (new.disk)...
wubi-resize.sh: Formatting new virtual disk as ext4.
wubi-resize.sh: Copying files - this will take some time.
wubi-resize.sh: Please be patient...
wubi-resize.sh: Copying from root (/)
wubi-resize.sh: Copying from /boot
wubi-resize.sh: Copying from /usr
wubi-resize.sh: Copying from /home
rsync: writefd_unbuffered failed to write 4 bytes to socket [sender]: Broken pipe (32)
rsync: write failed on "/tmp/wubi-resize/home/kitty/.thunderbird/0y5x5xuv.default/ImapMail/imap.googlemail.com/[Gmail].sbd/Important": No space left on device (28)
rsync: connection unexpectedly closed (705204 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(605) [sender=3.0.9]
wubi-resize.sh: Copying files failed or was canceled. Return code: 12
wubi-resize.sh: Correct errors and rerun with --resume option
wubi-resize.sh: Please wait - cleaning up...
wubi-resize.sh: Operation aborted
kitty@ubuntu:~/Downloads/wubi-resize-1.6$ --resume
--resume: command not found
kitty@ubuntu:~/Downloads/wubi-resize-1.6$ 
```

how can i fix this?

---

### Post by 101kitty on 2013-02-19
Does anyone not know anything about this?

---

### Post by Mark Phelps on 2013-02-19
I know it's difficult ... but the errors are shown in the command results.

See the error "no space left on device" -- this means there is not enough room in the partition for the expanded size.  My guess is that you have to have enough room for the original (18GB) plus the 30GB (new).

Also the "--resume" option means you add "--resume" to the END of the previous command, it is not a command by itself.

Wubi installations are mean only for trial use, anyway.  IF you plan to use Ubuntu long term, you need to consider an actual partition -- and you will have to shrink an existing NTFS partition in order to make room.

Unless you have a lot invested in the Ubuntu install, your best option would be to remove it (In WINDOWS, like any other program) and either reinstall with a large space allocation or consider installing in a separate partition.

---

### Post by 101kitty on 2013-02-19
Well the only reason i installed it though windows because i don't have any spare money to buy and disk nor a usb drive, is there away to install linux though linux? and i have about 150 free space on this hard drive i made for linux os, i was not aware of it making a v disk, if someone could send me a cd that would be nice.

---

### Post by bcbc on 2013-02-19
You can migrate the Wubi to a partition but it uses the same program to perform the copy (rsync) so you might have similar issues. Generally when rsync fails it is due to corruption. I'd recommend running fsck, which you might be able to do from recovery mode or else use a live DVD/USB to fsck the root.disk.

Either that or make sure your mail client is closed when you run it again (using the --resume option). There's also a way to exclude the folder causing your problem, but that requires you editing the script.

---

