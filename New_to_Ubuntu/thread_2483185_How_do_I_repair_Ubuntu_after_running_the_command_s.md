---
title: "How do I repair Ubuntu after running the command: sudo rm /*"
date: 2023-01-22
forum: New to Ubuntu
---

### Post by jay1232 on 2023-01-22
While I was trying to remove files from a SD card from the same directory, I ran `sudo rm /*` and now Ubuntu isn't working.
when i restarted i get the error: kernel panic attempted to kill init.


I'm new to Linux. What should I do now? I dont want to loose my data.

---

### Post by ActionParsnip on 2023-01-22
Just reinstall. It'll be quicker

---

### Post by #&amp;thj^% on 2023-01-22
> **ActionParsnip said:**
> Just reinstall. It'll be quicker

+1 No need fiddling around with trying to fix this, that would be ill advised.

---

### Post by ajgreeny on 2023-01-22
I hope you have backups of all your personal files particularly if you did not have a separate /home or /data partition, or they as well as your OS will be completely lost.

---

### Post by QIII on 2023-01-22
Just so you know:  What you did was removed all files from the root directory, or /.

Your installation is toast.

You did have backups of your important files, right?  By fortunate happenstance, you may be able to recover those, since you didn't use the recursive flag.

Also, if you own the directory or the permissions allow you to read/write, there is no need to use sudo.  That, by itself, would have kept you from damaging your installation without warning.

To remove files from the current working directory, use

```
rm <somefile>.<someextension>
```

No slash!

Or to empty all files in the current working directory, use

```
rm *.*
```

No slash!
 
If you want to delete the contents of a directory inside your current working directory, say useless_files, use:

```
rm useless_files/*.*
```

No leading slash! 

If you want to empty a directory other than your current directory, use the fully qualified path.

```
rm /<fully>/<qualified>/<directory>/<somefielname>.<someextension>
```

If you use that leading slash, you need to fully qualify the path

Outside your home directory or any directory you own, you will need to use sudo.

---

### Post by Impavidus on 2023-01-23
Wait, if you didn't use the -r option, that command would have removed all files from the root directory, but not the directories, nor any files in those directories. That means it only removed a couple of symlinks. On my Ubuntu:```
bin -> usr/bin/
lib -> usr/lib/
lib32 -> usr/lib32/
lib64 -> usr/lib64/
libx32 -> usr/libx32/
sbin -> usr/sbin/
```Restore those symlinks and you should be fine. Use a live disk to get access to the filesystem. You should be able to do it from the busybox prompt too. I never had to use that one myself though.

With the -r option, that would have removed all mounted files and directories on your system. No way to fix that, other than reinstall and recover your documents from backups (assuming your backup drive wasn't mounted).

---

### Post by monkeybrain20122 on 2023-01-23
In addition to everything said above, why did you use "sudo" to remove stuffs in the sd card? You only use sudo when you have to alter things at the system level (like installing software system wide) For the normal user there is very little reason where you have to remove stuffs in the system manually. 

sudo (or becoming root in some other distros) should not be abused, I notice many tech blogs do that, they are doing task that could be achieved completely without elevated permission yet somehow they want to put in "sudo". It annoys me to no end.

---

### Post by jay1232 on 2023-01-23
Yes i already did that and its working.
Thanks for the feedback though

---

### Post by TheFu on 2023-01-23
> **QIII said:**
>  
```
rm *.*
```


*.* is a DOS thing. DOS treats extensions separately.  Unix doesn't care.  Extensions on Unix systems are for humans, very useful to us, but the OS doesn't care.

* or *.* are nearly the same.   But since Unix doesn't really care about extensions at the OS level, * matches all files and directories, whereas *.* matches all files and directories that have a non-leading period in their names.

Different shells (bash, csh, tsch, zsh, psh, fish, .... ) have slightly different pattern matching, so YMMV.  
[https://www.linuxjournal.com/content/pattern-matching-bash](https://www.linuxjournal.com/content/pattern-matching-bash) explains, perhaps more clearly.  

A handy table stolen from the link above:
```
  Pattern          Description
*               Match zero or more characters
?               Match any single character
[...]           Match any of the characters in a set
?(patterns)     Match zero or one occurrences of the patterns (extglob)
*(patterns)     Match zero or more occurrences of the patterns (extglob)
+(patterns)     Match one or more occurrences of the patterns (extglob)
@(patterns)     Match one occurrence of the patterns (extglob)
!(patterns)     Match anything that doesn't match one of the patterns (extglob)
```

extglob is for extended globs, which are really just regex. More on extended globbing: [https://www.linuxjournal.com/content/bash-extended-globbing](https://www.linuxjournal.com/content/bash-extended-globbing)

When ever I see people doing things like 
```
ls *.jpg
```
I know they could just as easily use
```
ls *jpg
```
without the '.'  Every character saved is useful towards efficiency.

For any non-toy/play system, be certain to have daily, automatic, versioned, backups.  Also, I suspect everyone has wiped an OS at least once.  Think I've done it 3 times over the decades and just yesterday, I deleted some files - the wrong files - while trying to merge 2 similar, but not identical directories with content. I removed the files from the wrong directory and because that area is only "scratch space", it isn't part of any backups. Oooops.  Those files are gone. I'll never get them back, unless I pull the 300GB IDE disk from a shelf somewhere that has all the originals from 15 yrs ago.  Not gonna happen, though I do have a good idea where that HDD is.

---

### Post by #&amp;thj^% on 2023-01-23
And always check first, as TheFu points out we all have had a disaster at one point.
I'll always use:
```
echo rm /*
rm /bin /boot /dev /etc /home /initrd.img /initrd.img.old /lib /lib32 /lib64 /libx32 /media /mnt /opt /proc /root /run /sbin /srv /sys /tank /tmp /usr /var /vmlinuz /vmlinuz.old

```
Just to see what getting removed.

---

### Post by math492m on 2023-01-30
i would just reinstall

---

### Post by math492m on 2023-01-30
but it depens, on how much acces you still have.

---

