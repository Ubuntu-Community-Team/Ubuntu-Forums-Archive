---
title: "Protect launcher from user deletion"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by tedw on 2008-11-20
How do I prevent that a user deletes a launcher on his own desktop ? 

As root I have set the LaunchTask.desktop file on the user Desktop to r--r--r-- but still the user can delete it. 

Any tips would be appredciated.

tedw

---

### Post by Pro-reason on 2008-11-20
Did you make sure it was owned by root too?

---

### Post by tedw on 2008-11-21
Yes, indeed !

ls -la /home/username/Desktop   

shows -r--r--r-- root root ...

Thanks for the suggestion.

tedw

---

### Post by tedw on 2009-01-14
Anyone else had this problem or know of a solution ?

Is it perhaps a bug ??

tedw

---

### Post by jerome1232 on 2009-01-14
I believe it's actually the directory's permissions that determines this.

ie if ~/Desktop is owned as rwxr-xr-x root root then users can see and list files inside the directory and will not be able to delete file inside of it, but if a user has write premisions to the directory, then they can delete files inside that directory.

hopefully this bit of chowning/rm'ing gives you an idea of what I mean.

example:

```
jeremy@direbane:~/test$ ls -ld ~/test
drwxr-xr-x 2 jeremy jeremy 4096 2009-01-13 23:27 /home/jeremy/test
jeremy@direbane:~$ cd test
jeremy@direbane:~/test$ ls -l
total 120
-rw-r--r-- 2 jeremy jeremy 56725 2009-01-12 17:25 file
-rw-r--r-- 2 jeremy jeremy 56725 2009-01-12 17:25 hardlink.file
-rw-r--r-- 1 jeremy jeremy     0 2009-01-12 17:21 otherfile
lrwxrwxrwx 1 jeremy jeremy     4 2009-01-12 17:23 softlink.file -> file
jeremy@direbane:~/test$ sudo chown root: file
[sudo] password for jeremy: 
jeremy@direbane:~/test$ ls -l
total 120
-rw-r--r-- 2 root   root   56725 2009-01-12 17:25 file
-rw-r--r-- 2 root   root   56725 2009-01-12 17:25 hardlink.file
-rw-r--r-- 1 jeremy jeremy     0 2009-01-12 17:21 otherfile
lrwxrwxrwx 1 jeremy jeremy     4 2009-01-12 17:23 softlink.file -> file
jeremy@direbane:~/test$ rm file
rm: remove write-protected regular file `file'? y
jeremy@direbane:~/test$ ls -l
total 60
-rw-r--r-- 1 root   root   56725 2009-01-12 17:25 hardlink.file
-rw-r--r-- 1 jeremy jeremy     0 2009-01-12 17:21 otherfile
lrwxrwxrwx 1 jeremy jeremy     4 2009-01-12 17:23 softlink.file -> file
jeremy@direbane:~/test$ ln hardlink.file file
jeremy@direbane:~/test$ ls -l
total 120
-rw-r--r-- 2 root   root   56725 2009-01-12 17:25 file
-rw-r--r-- 2 root   root   56725 2009-01-12 17:25 hardlink.file
-rw-r--r-- 1 jeremy jeremy     0 2009-01-12 17:21 otherfile
lrwxrwxrwx 1 jeremy jeremy     4 2009-01-12 17:23 softlink.file -> file
jeremy@direbane:~/test$ sudo chown root: ../test/
jeremy@direbane:~/test$ ls -ld ~/test
drwxr-xr-x 2 root root 4096 2009-01-13 23:27 /home/jeremy/test
jeremy@direbane:~/test$ ls -l
total 120
-rw-r--r-- 2 root   root   56725 2009-01-12 17:25 file
-rw-r--r-- 2 root   root   56725 2009-01-12 17:25 hardlink.file
-rw-r--r-- 1 jeremy jeremy     0 2009-01-12 17:21 otherfile
lrwxrwxrwx 1 jeremy jeremy     4 2009-01-12 17:23 softlink.file -> file
jeremy@direbane:~/test$ rm file
rm: remove write-protected regular file `file'? y
rm: cannot remove `file': Permission denied
jeremy@direbane:~/test$ sudo chown jeremy: file
jeremy@direbane:~/test$ ls -l
total 120
-rw-r--r-- 2 jeremy jeremy 56725 2009-01-12 17:25 file
-rw-r--r-- 2 jeremy jeremy 56725 2009-01-12 17:25 hardlink.file
-rw-r--r-- 1 jeremy jeremy     0 2009-01-12 17:21 otherfile
lrwxrwxrwx 1 jeremy jeremy     4 2009-01-12 17:23 softlink.file -> file
jeremy@direbane:~/test$ rm file
rm: cannot remove `file': Permission denied
```

---

