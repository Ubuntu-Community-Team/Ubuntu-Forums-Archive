---
title: "Possible to copy a link?"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by NormR2 on 2008-05-04
Is it possible to copy a link and not the file linked to?
When I create a link to a file using ln -s <path-to-file> <link>
and then try to copy the link file: <link> above, the linked to file is copied, not the link file.

Console log follows:

norm@norm-desktop:~$ ls -l
total 60
drwxr-xr-x  2 norm norm 4096 2008-05-03 09:06 Desktop
drwxr-xr-x  2 norm norm 4096 2008-05-04 08:50 Documents
lrwxrwxrwx  1 norm norm   26 2008-04-24 06:54 Examples -> /usr/share/example-content
drwxr-xr-x  2 norm norm 4096 2008-05-04 08:48 ForTests
lrwxrwxrwx  1 norm norm   17 2008-05-04 08:46 L2testfile -> ForTests/testfile
drwxr-xr-x 10 norm norm 4096 2008-04-28 12:06 nautilus-scripts
drwxr-xr-x  2 norm norm 4096 2008-05-03 15:01 Testing
drwxr-xr-x 34 norm norm 4096 2008-05-03 09:36 Tutorial
drwxr-xr-x  4 norm norm 4096 2008-05-03 12:14 Work
 ...
norm@norm-desktop:~$ cat L2testfile
this is a test file.

>>See above. L2testfile is a link that'd I'd like to copy to another folder

>> Now try to copy the link file to another directory:

norm@norm-desktop:~$  sudo cp L2testfile /home/java/L2testfile

>> Now go to target and see what we have:

norm@norm-desktop:~$ cd /home/java/
norm@norm-desktop:/home/java$ ls -l
total 4
lrwxrwxrwx 1 java java 26 2008-05-04 08:39 Examples -> /usr/share/example-content
-rw-r--r-- 1 root root 21 2008-05-04 08:51 L2testfile
norm@norm-desktop:/home/java$ cat L2testfile
this is a test file.
norm@norm-desktop:/home/java$ 

copy (cp) copied the file, not the link!!!

>> here is the source file data:

norm@norm-desktop:/home/java$ cd ~
norm@norm-desktop:~$ cd ForTests
norm@norm-desktop:~/ForTests$ ls -l
total 4
-rw-r--r-- 1 norm norm 21 2008-05-04 08:48 testfile
norm@norm-desktop:~/ForTests$ 


Thanks,
Norm

---

### Post by tdrusk on 2008-05-04
hmm. I don't know how much help I can be but...

right click on the desktop and create a launcher that launches to a location.

that MIGHT help...
sorry

---

### Post by glennric on 2008-05-04
Use the following:
```
cp -P L2testfile /home/java/L2testfile
```

---

### Post by NormR2 on 2008-05-04
I tried cp with -P and got the following results. It looks like a link was copied but the link doesn't appear to work when I try using it with the cat command to display the file.

What am I doing wrong?

Norm

Console file follows:

>> try copying with the -P option to copy only the link file, not the file

>> first show what's there

norm@norm-desktop:~$ ls -l
total 60
 ...
drwxr-xr-x  2 norm norm 4096 2008-05-04 08:48 ForTests
lrwxrwxrwx  1 norm norm   17 2008-05-04 08:46 L2tf -> ForTests/testfile
 ...

>> now try copying the file

norm@norm-desktop:~$ sudo cp -P L2tf /home/java/L2tf

>> go see what happened

norm@norm-desktop:~$ cd /home/java/
norm@norm-desktop:/home/java$ ls -l
total 4
lrwxrwxrwx 1 java 1001 26 2008-05-04 08:39 Examples -> /usr/share/example-content
-rw-r--r-- 1 norm norm 21 2008-05-04 08:48 L2testfile
lrwxrwxrwx 1 root root 17 2008-05-04 10:20 L2tf -> ForTests/testfile

>> The L2tf displayed above by ls was colored with RED letters in a black background???

>> looks ok. Is it a good link?? Try showing the file:

norm@norm-desktop:/home/java$ cat L2tf
cat: L2tf: No such file or directory

>>  What happened?  File not found???

>> go back and look at the source for the copy:

norm@norm-desktop:/home/java$ cd ~
norm@norm-desktop:~$ cat L2tf
this is a test file.

>> Source Looks ok.  What's wrong with the cp -P ???

norm@norm-desktop:~$

---

### Post by NormR2 on 2008-05-05
What does a file displayed by ls -l that has RED letters in a black background mean?

---

