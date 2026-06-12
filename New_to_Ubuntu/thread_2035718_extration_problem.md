---
title: "extration problem"
date: 2012-07-31
forum: New to Ubuntu
---

### Post by Hasan55 on 2012-07-31
hi guys, can anyone help me to solve this problem. the problem is when i am trying to extract tarball in the terminal then nothing happen.

when i gave command for example :-

hasan@Hasan-desktop:~$ cd /home/hasan/Desktop
hasan@Hasan-desktop:~/Desktop$ 

then  Desktop$ comes but when i used  command like as :-

hasan@Hasan-desktop:~$ cd /home/hasan/Desktop/rhythmbox-0.13.3
bash: cd: /home/hasan/Desktop/rhythmbox-0.13.3: No such file or directory
hasan@Hasan-desktop:~$ 

then rhythmbox does not come in terminal command as extraction  . what should  i do ...........:( can anyone  help me . thank you.

---

### Post by mlentink on 2012-07-31
What do you want to extract, and where is it? Normally you would use the 'tar' command for extracting files.

If you use:
```
hasan@Hasan-desktop:~$ cd /home/hasan/Desktop/rhythmbox-0.13.3
```it will fail for three reasons: 
1- cd is used to _**C**_hange to a _**D**_irectory 
2- you are already IN the directory /home/hasan/Desktop
3- rhythmbox-0.13.3 is most likely not a directory, but a file

Might I also point out that Rhythmbox is installed as a standard?

Please see 
```
man tar
```
for usage of the tar command

---

### Post by Elfy on 2012-07-31
Thread closed. Please do not post duplicates, it dilutes community effort.

You've already got this as a thread [http://ubuntuforums.org/showthread.php?t=2003948](http://ubuntuforums.org/showthread.php?t=2003948)

---

