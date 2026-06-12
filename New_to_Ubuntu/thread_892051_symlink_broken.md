---
title: "symlink broken"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by wgato on 2008-08-16
I made a symbolic link in my home directory to a shared directory on a windows machine using 'ln -s'' last night.
Typing 'ls' in my home directory showed the link and I didnt do anything else with it at the time.  But now I cant use the files and when I look at my home directory in gnome file browser it shows 'link (broken)'.

what could be the cause of a broken link?

---

### Post by Gamma746 on 2008-08-16
> **wgato said:**
> what could be the cause of a broken link?

You linked to something that isn't there any more.  Could you post the output of ```
ls -l
```

---

### Post by wgato on 2008-08-16
its still there though, i can use it on the windows machine like normal.

me@ubuntu:/home/me/Music$ ls -l yppah
lrwxrwxrwx 1 me me 57 2008-08-16 00:42 yppah -> yppah /

thanks for taking the time to answer!

---

### Post by Rolcol on 2008-08-16
Broken link means that the destination doesn't exist.  Are you sure the destination of the link is mounted?

---

### Post by wgato on 2008-08-17
me@ubuntu:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/sda3 on /home type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
//windowsmachine/elements (e) on /mnt/Elements type cifs (rw,mand)



The last line above shows the directory /mnt/Elements.  The yppah directory is in //windowsmachine/elements (e)/yppah.

I can cd into /mnt/Elements/yppah from ubuntu.
I can also use the files fine from the windows machine they are located on, i.e. that havent been moved.

On the windowsmachine both the "elements (e)" and yppah directories are shared.



I am thinking unlinking and trying to ln -s might be a good idea but am not sure how to unlink.

---

### Post by unutbu on 2008-08-17
You can remove links just like you remove a regular file. It will not remove the file or directory it is pointing to. It will only remove the symbolic link. You can use a GUI like Nautilus, or type
```

rm ~/Music/yppah

```> 
lrwxrwxrwx 1 me me 57 2008-08-16 00:42 yppah -> yppah /

This says that the symbolic link at /home/me/Music/yppah is pointing to a directory called "yppah ". Notice the space after yppah. The space makes your computer think "yppah" (the symbolic link) is different than "yppah " (the directory). But you have no directory called "yppah ", and this is why the gnome file browser (nautilus?) says "link (broken)'.

You can redirect the link without removing it first by using the -f flag:
```

cd ~/Music
ln -sf /mnt/Elements/yppah yppah
```

---

### Post by wgato on 2008-08-17
whew, thats it!

thanks!

---

### Post by clockworkpc on 2011-03-03
Check out this tip by johnraff:

[http://ubuntuforums.org/showthread.php?p=10518170#post10518170]("http://ubuntuforums.org/showthread.php?p=10518170#post10518170")

---

