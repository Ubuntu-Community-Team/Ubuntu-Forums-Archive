---
title: "compiling c programe"
date: 2009-03-15
forum: Programming Talk
---

### Post by william_arackal on 2009-03-15
when i tried to compile a hello.c program  the out put i get is
gcc: hello.c: No such file or directory
gcc: no input files
 pls any one help me to fix this problem.

the version of gcc is 
gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)

---

### Post by taurus on 2009-03-15
Are you in the same directory that **hello.c** is resided?

```
ls -la
```

---

### Post by william_arackal on 2009-03-16
Yes , in the same directory.

---

### Post by taurus on 2009-03-16
While in that directory where hello.c is, can you post the output of this command?

```
ls -la
```

---

### Post by william_arackal on 2009-03-16
xp@xp-desktop:~$ ls -la
total 744
drwxr-xr-x 44 xp   xp     4096 2009-03-16 21:48 .
drwxr-xr-x  3 root root   4096 2009-02-24 03:10 ..
drwx------  3 xp   xp     4096 2009-02-25 00:15 .adobe
-rw-------  1 xp   xp     3263 2009-03-16 01:51 .bash_history
-rw-r--r--  1 xp   xp      220 2009-02-24 03:10 .bash_logout
-rw-r--r--  1 xp   xp     2940 2009-02-24 03:10 .bashrc
drwxr-xr-x  3 xp   xp     4096 2009-02-24 03:17 .cache
drwx------  3 xp   xp     4096 2009-02-24 11:36 .compiz
drwxr-xr-x  7 xp   xp     4096 2009-03-01 10:27 .config
drwxr-xr-x 13 xp   xp     4096 2009-03-15 20:07 Desktop
-rw-------  1 xp   xp       28 2009-03-16 21:48 .dmrc
drwxr-xr-x  4 xp   xp     4096 2009-03-11 00:11 Documents
-rw-------  1 xp   xp       16 2009-02-24 03:17 .esd_auth
drwxr-xr-x  8 xp   xp     4096 2009-03-16 01:52 .evolution
lrwxrwxrwx  1 xp   xp       26 2009-02-24 03:10 Examples -> /usr/share/example-content
drwxr-xr-x  2 xp   xp     4096 2009-02-25 00:04 .fontconfig
drwx------  5 xp   xp     4096 2009-03-16 21:48 .gconf
drwx------  2 xp   xp     4096 2009-03-16 22:02 .gconfd
drwxr-xr-x 22 xp   xp     4096 2009-03-03 20:55 .gimp-2.4
-rw-r-----  1 xp   xp        0 2009-03-15 20:24 .gksu.lock
drwx------ 13 xp   xp     4096 2009-03-16 01:52 .gnome2
drwx------  2 xp   xp     4096 2009-02-24 03:17 .gnome2_private
drwx------  2 xp   xp     4096 2009-03-16 21:48 .gnupg
drwxr-xr-x  2 xp   xp     4096 2009-03-09 14:09 .gstreamer-0.10
-rw-r--r--  1 xp   xp       96 2009-03-16 21:48 .gtk-bookmarks
dr-x------  2 xp   xp        0 2009-03-16 21:48 .gvfs
-rw-r--r--  1 xp   xp       70 2009-03-16 00:32  hello.c
-rw-------  1 xp   xp      334 2009-03-16 21:48 .ICEauthority
drwxr-xr-x  2 xp   xp     4096 2009-02-24 03:21 .icons
drwxr-xr-x  3 xp   xp     4096 2009-03-01 00:46 linuxstuff
-rw-r--r--  1 xp   xp       23 2009-03-06 23:25 list
drwxr-xr-x  3 xp   xp     4096 2009-02-24 03:17 .local
drwx------  3 xp   xp     4096 2009-02-25 00:15 .macromedia
drwx------  3 xp   xp     4096 2009-03-04 19:11 .metacity
drwx------  4 xp   xp     4096 2009-02-24 03:18 .mozilla
drwxr-xr-x  2 xp   xp     4096 2009-02-24 03:17 Music
drwxr-xr-x  3 xp   xp     4096 2009-03-16 01:52 .nautilus
drwx------  3 xp   xp     4096 2009-03-16 01:49 .openoffice.org2
drwxr-xr-x  2 xp   xp     4096 2009-02-24 03:17 Pictures
-rw-r--r--  1 xp   xp      586 2009-02-24 03:10 .profile
drwxr-xr-x  2 xp   xp     4096 2009-02-24 03:17 Public
drwxr-xr-x  2 xp   xp     4096 2009-02-23 22:15 .pulse
-rw-------  1 xp   xp      256 2009-02-24 03:17 .pulse-cookie
-rw-------  1 xp   xp     4524 2009-03-11 09:28 .recently-used
-rw-r--r--  1 xp   xp   504522 2009-03-16 01:52 .recently-used.xbel
drwx------  2 xp   xp     4096 2009-02-24 03:17 .ssh
-rw-r--r--  1 xp   xp        0 2009-02-24 03:24 .sudo_as_admin_successful
drwxr-xr-x  4 xp   xp     4096 2009-02-25 00:02 .sudoku
drwxr-xr-x  2 xp   xp     4096 2009-02-24 03:17 Templates
drwxr-xr-x  3 xp   xp     4096 2009-03-07 16:57 test
drwxr-xr-x  2 xp   xp     4096 2009-02-24 03:21 .themes
drwx------  4 xp   xp     4096 2009-02-23 22:04 .thumbnails
drwxr-xr-x  4 xp   xp     4096 2009-02-24 23:56 .tomboy
-rw-r--r--  1 xp   xp     5804 2009-02-25 00:58 .tomboy.log
drwxr-xr-x  5 xp   xp     4096 2009-02-27 18:49 .transmission
-rw-r--r--  1 xp   xp      236 2009-03-08 02:34 try
drwxr-xr-x  2 xp   xp     4096 2009-02-24 16:49 .update-manager-core
drwx------  2 xp   xp     4096 2009-03-08 11:47 .update-notifier
drwxr-xr-x  3 xp   xp     4096 2009-03-09 14:16 Videos
drwxr-xr-x  2 xp   xp     4096 2009-02-25 00:58 .wapi
drwxr-xr-x  7 xp   xp     4096 2009-03-16 00:28 webstuff
drwxr-xr-x  4 xp   xp     4096 2009-03-15 20:13 .wine
-rw-------  1 xp   xp      121 2009-03-16 21:48 .Xauthority
-rw-r--r--  1 xp   xp     3077 2009-03-16 21:54 .xsession-errors

---

### Post by taurus on 2009-03-16
What does it look like?

```
cat hello.c
```
I assume you compile it as

```
gcc hello.c
```

---

### Post by william_arackal on 2009-03-16
I did the prog in gedit as follows
#include<stdio.h>
main()
{
  printf("Hello world!\n");
  return 0;

}
to compile gave the command
gcc -o hello hello.c

---

### Post by taurus on 2009-03-16
And you still get the same error message about file not found?

---

### Post by william_arackal on 2009-03-16
yes
gcc: hello.c: No such file or directory
gcc: no input files

---

### Post by taurus on 2009-03-16
```
gcc -o hello ./hello.c
-or-
gcc -o hello ~/hello.c
```

---

### Post by william_arackal on 2009-03-16
xp@xp-desktop:~$ gcc -o hello hello.c
gcc: hello.c: No such file or directory
gcc: no input files
xp@xp-desktop:~$ gcc -o hello ./hello.c
gcc: ./hello.c: No such file or directory
gcc: no input files
xp@xp-desktop:~$ gcc -o hello ~/hello.c
gcc: /home/xp/hello.c: No such file or directory
gcc: no input files

for your information iam using Ubuntu 8.04

---

### Post by taurus on 2009-03-16
How about no output file.

```
gcc hello.c
```

---

### Post by william_arackal on 2009-03-16
xp@xp-desktop:~$ gcc hello.c
gcc: hello.c: No such file or directory
gcc: no input files

---

### Post by Berserker v7 on 2009-03-16
This is indeed most odd as i do it all the time!! just try moving your files from home into some other directory, cd into it and then try to compile. and also, is
```
cat hello.c
```
 working in your home directory?

---

### Post by sujoy on 2009-03-16
now now, you didnt really put in any spaces in the file name did you?

---

### Post by Ruhe on 2009-03-16
> **william_arackal said:**
> xp@xp-desktop:~$ gcc -o hello hello.c
gcc: hello.c: No such file or directory
gcc: no input files
xp@xp-desktop:~$ gcc -o hello ./hello.c
gcc: ./hello.c: No such file or directory
gcc: no input files
xp@xp-desktop:~$ gcc -o hello ~/hello.c
gcc: /home/xp/hello.c: No such file or directory
gcc: no input files

for your information iam using Ubuntu 8.04

This is Linus's revenge for the fact that the computer is called "xp-desktop" ;)

Try to do this:
create file assert_gcc.sh with the following content
[PHP]
#!/bin/sh

mkdir test_dir;
cd test_dir && touch test_program.c;
echo "
#include <stdio.h>

int main() {
printf(\"test\");
return 0;
}
" > test_program.c;

gcc test_program.c -o test_program;
./test_program
[/PHP]

run in console 
```

$chmod +x assert_gcc.sh
$./assert_gcc.sh

```

I've checked this should work, if not, then it's something mystical

---

