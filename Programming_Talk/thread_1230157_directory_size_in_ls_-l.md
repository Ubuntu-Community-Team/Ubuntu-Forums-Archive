---
title: "directory size in ls -l"
date: 2009-08-03
forum: Programming Talk
---

### Post by bilol on 2009-08-03
Hi all,

```
dhiman@dhiman-desktop:~$ ls -ls
total 6952
   8 -rwxr-xr-x 1 dhiman dhiman    7797 2009-06-17 13:49 a.out
   4 -rw-r--r-- 1 dhiman dhiman     378 2009-06-19 17:43 cin.sh
   4 drwxr-xr-x 2 dhiman dhiman    4096 2009-07-31 17:20 Desktop
 108 -rw-r--r-- 1 dhiman dhiman  104604 2009-07-10 13:58 dkTestPrint.pdf
   4 drwxr-xr-x 2 dhiman dhiman    4096 2009-07-30 16:41 Documents
  80 drwxr-xr-x 2 dhiman dhiman   77824 2009-07-13 12:38 dpkg-repack130709
   0 lrwxrwxrwx 1 dhiman dhiman      26 2009-05-07 18:50 Examples -> /usr/share/example-content
   4 -rw-r--r-- 1 dhiman dhiman      66 2009-05-11 17:02 hello.c
   4 drwxr-xr-x 2 dhiman dhiman    4096 2009-05-07 18:52 Music
   4 drwx------ 2 dhiman dhiman    4096 2009-07-30 12:15 MyDownloads
   4 -rw-r--r-- 1 dhiman dhiman      85 2009-07-31 15:49 myfl
   4 drwx------ 2 dhiman dhiman    4096 2009-07-31 17:21 OS
   4 drwxr-xr-x 2 dhiman dhiman    4096 2009-06-11 13:08 Photos
   4 drwxr-xr-x 4 dhiman dhiman    4096 2009-06-10 15:17 Pictures
   4 drwxr-xr-x 2 dhiman dhiman    4096 2009-05-07 19:03 Public
   4 drwxr-xr-x 3 dhiman dhiman    4096 2009-06-04 12:17 ramkrishna
   4 drwxr-xr-x 2 dhiman dhiman    4096 2009-05-07 19:03 Templates
   4 -rw-r--r-- 1 dhiman dhiman      14 2009-07-31 16:06 urfl
   4 drwxr-xr-x 2 dhiman dhiman    4096 2009-06-01 14:41 Videos
6696 -rw-r--r-- 1 dhiman dhiman 6841784 2009-07-27 20:26 wget-log
```


The 6th field signifies the byte count of the files.What does it signify for directories? 
Why is it 4096 for the directory Desktop and 77824 for the directory dpkg-repack130709?
Can't get exact information by googling.
Need your help....

---

### Post by lvleph on 2009-08-03
I believe it is the size of the file that represents the folder. Try the following and you will see what I mean.

```
vi Desktop
```

---

### Post by Greyed on 2009-08-03
Close, it is the size of theblocks dedicated to the index of files in the directory.  It will always be a multiple of if your blocksize.  IE, 1 block can index up to x files.  After that another block needs to be dedicated to the directory index more files.

Editing a directory does nothing.  In the case of vim it is opening the directory for you and presenting it in a manner that allows you to select a file to edit.  It is not showing you what is actually stored there.

---

### Post by bilol on 2009-08-03
Hi,
Desktop is a directory,so vi Desktop is not working. 
For the sake of clarity I did the following:
```
dhiman@dhiman-desktop:~$ cd Desktop
dhiman@dhiman-desktop:~/Desktop$ ls -l
total 84
-rw-r--r-- 1 dhiman dhiman  1636 2009-08-03 12:18 dirsize
-rw-r--r-- 1 dhiman dhiman  1628 2009-08-03 12:18 dirsize~
-rwx------ 1 dhiman dhiman 33468 2009-02-11 14:22 dkEmails.htm
-rw------- 1 dhiman dhiman   105 2009-07-27 12:33 downldCommand
-rw-r--r-- 1 dhiman dhiman   739 2009-07-27 11:34 letter ~
-rw-r--r-- 1 dhiman dhiman 11896 2009-07-09 17:17 links.ods
-rw-r--r-- 1 dhiman dhiman  4446 2009-06-04 16:44 mts~
-rw-r--r-- 1 dhiman dhiman  2071 2009-06-04 16:56 mts1~
-rw-r--r-- 1 dhiman dhiman  1018 2009-06-08 13:50 mymts~
-rw-r--r-- 1 dhiman dhiman   813 2009-06-26 13:15 prosad~

```

Please help.....

---

### Post by Greyed on 2009-08-03
He meant vim.

```

" ============================================================================
" Netrw Directory Listing                                        (netrw v132)
"   /home/grey/Desktop
"   Sorted by      name
"   Sort sequence: [\/]$,\.h$,\.c$,\.cpp$,*,\.o$,\.obj$,\.info$,\.swp$,\.bak$,\~
"   Quick Help: <F1>:help  -:go up dir  D:delete  R:rename  s:sort-by  x:exec
" ============================================================================
../
.directory
Galaxy Online.desktop
Galaxy Online.lnk
Yohoho! Puzzle Pirates.desktop*

```

But as I said, that has no bearing as to what is actually stored in the directry structure nor relevant to the size reported by ls.

---

### Post by bilol on 2009-08-03
Thanks Greyed,
Is it possible to calculate the aforesaid 6th field of a directory by listing its content.I mean, is it possible to compute the 6th field of the the directory,say Desktop, by seeing the result below: 
```
dhiman@dhiman-desktop:~$ cd Desktop/
dhiman@dhiman-desktop:~/Desktop$ ls -ls
total 84
 4 -rw-r--r-- 1 dhiman dhiman  1636 2009-08-03 12:18 dirsize
 4 -rw-r--r-- 1 dhiman dhiman  1628 2009-08-03 12:18 dirsize~
36 -rwx------ 1 dhiman dhiman 33468 2009-02-11 14:22 dkEmails.htm
 4 -rw------- 1 dhiman dhiman   105 2009-07-27 12:33 downldCommand
 4 -rw-r--r-- 1 dhiman dhiman   739 2009-07-27 11:34 letter ~
12 -rw-r--r-- 1 dhiman dhiman 11896 2009-07-09 17:17 links.ods
 8 -rw-r--r-- 1 dhiman dhiman  4446 2009-06-04 16:44 mts~
 4 -rw-r--r-- 1 dhiman dhiman  2071 2009-06-04 16:56 mts1~
 4 -rw-r--r-- 1 dhiman dhiman  1018 2009-06-08 13:50 mymts~
 4 -rw-r--r-- 1 dhiman dhiman   813 2009-06-26 13:15 prosad~

```
thanks in advance...

---

### Post by ghostdog74 on 2009-08-03
if you want to calculate the size of the directory, you can use du. man du for usage.

---

### Post by bilol on 2009-08-03
Thanks..
> if you want to calculate the size of the directory, you can use du. man du for usage. 
But my point is not to know the directory size, rather to calculate the 6th field of ls -ls coming against a particular directory, by seeing that directory content.
How can it be done?
Thanks in advance.

---

### Post by bilol on 2009-08-03
Thanks for all your suggestion and answers,but still I have doubts.
Let me give you the following output:
```
dhiman@dhiman-desktop:~$ ls -ls /media/EduDocu/EduDocu/
total 121
  0 drwxrwxrwx 1 root root      0 2009-05-14 15:21 codeDoc
  0 drwxrwxrwx 1 root root      0 2009-07-06 14:10 DKode
  4 drwxrwxrwx 1 root root   4096 2009-05-14 15:21 DKode_old
104 -rwxrwxrwx 1 root root 103712 2009-05-29 10:04 DKontacts.pdf
  0 drwxrwxrwx 1 root root      0 2009-07-06 14:24 Images
  0 drwxrwxrwx 1 root root      0 2009-05-14 15:26 ISI_PLP
  1 -rwxrwxrwx 2 root root    272 2009-07-01 15:13 libtest_out.txt
  4 -rwxrwxrwx 1 root root   1509 2009-06-17 13:48 linreg1.c
  0 drwxrwxrwx 1 root root      0 2009-05-14 15:38 linuxSetups
  0 drwxrwxrwx 1 root root      0 2009-07-01 14:17 Miscellaneous
  8 -rwxrwxrwx 1 root root   5564 2009-06-01 09:50 PCAultimate.m
  0 drwxrwxrwx 1 root root      0 2009-07-01 14:16 Topics
  0 drwxrwxrwx 1 root root      0 2009-05-14 15:13 UBUNTU

```
Can you explain why the 6th field of codeDoc is 0,DKode is 0 and DKode_old is 4096 by analyzing the following output:

```
dhiman@dhiman-desktop:~$ ls -ls /media/EduDocu/EduDocu/codeDoc
total 208
36 -rwxrwxrwx 1 root root 33792 2009-02-26 16:34 clc1.doc
36 -rwxrwxrwx 1 root root 36864 2009-02-18 12:57 clc.doc
28 -rwxrwxrwx 1 root root 26112 2009-02-19 16:37 firstPCPCA.doc
28 -rwxrwxrwx 1 root root 27648 2009-02-19 16:47 function PC.doc
44 -rwxrwxrwx 1 root root 44544 2009-03-23 15:24 function WX.doc
20 -rwxrwxrwx 1 root root 20480 2009-02-13 14:02 Hi.doc
16 -rwxrwxrwx 1 root root 15310 2009-02-18 13:59 PCA.rar

dhiman@dhiman-desktop:~$ ls -ls /media/EduDocu/EduDocu/DKode
total 0
0 drwxrwxrwx 1 root root 0 2009-07-06 14:10 C
0 drwxrwxrwx 1 root root 0 2009-07-06 17:16 MatLab

dhiman@dhiman-desktop:~$ ls -ls /media/EduDocu/EduDocu/DKode_old
total 7
4 -rwxrwxrwx 1 root root 679 2009-03-02 16:18 arr1.sh
1 -rwxrwxrwx 1 root root 596 2009-03-02 14:11 bubble.sh
0 drwxrwxrwx 1 root root   0 2009-05-14 15:21 c
1 -rwxrwxrwx 1 root root  66 2009-03-31 14:09 hi.c
0 drwxrwxrwx 1 root root   0 2009-05-14 15:20 html
0 drwxrwxrwx 1 root root   0 2009-05-14 15:21 java
1 -rwxrwxrwx 1 root root  59 2009-03-02 16:28 loop.sh
0 drwxrwxrwx 1 root root   0 2009-05-14 15:21 steganography
1 -rwxrwxrwx 1 root root  35 2008-12-15 13:45 test.c
1 -rwxrwxrwx 1 root root  79 2009-03-02 14:10 testing.sh


```
please help....

---

### Post by Greyed on 2009-08-03
More importantly why would you want to?

It is somewhat possible but not really practical.  The size of the index is related to the number of files in the directory and I believe it's sub directories.  However I don't think there's an exact limit.  IE, 200 files can be indexed in 1 block but 201 files would expand into a second block.  Although that may be the case since the structure would be static.  Regardless, *why* is this needed?  In close to 2 decades of using Unix-like systems I've never come across a case where I needed to know  the number of blocks the directory index would take up based on the number of files/subdirs in the directory.

---

### Post by bilol on 2009-08-03
OK greyed, I understand.
Now in the following output total size is given 7.But I am getting 9 by summing up the individual size!
4+1+0+1+0+0+1+0+1+1=9.
```
dhiman@dhiman-desktop:~$ ls -ls /media/EduDocu/EduDocu/DKode_old
total 7
4 -rwxrwxrwx 1 root root 679 2009-03-02 16:18 arr1.sh
1 -rwxrwxrwx 1 root root 596 2009-03-02 14:11 bubble.sh
0 drwxrwxrwx 1 root root   0 2009-05-14 15:21 c
1 -rwxrwxrwx 1 root root  66 2009-03-31 14:09 hi.c
0 drwxrwxrwx 1 root root   0 2009-05-14 15:20 html
0 drwxrwxrwx 1 root root   0 2009-05-14 15:21 java
1 -rwxrwxrwx 1 root root  59 2009-03-02 16:28 loop.sh
0 drwxrwxrwx 1 root root   0 2009-05-14 15:21 steganography
1 -rwxrwxrwx 1 root root  35 2008-12-15 13:45 test.c
1 -rwxrwxrwx 1 root root  79 2009-03-02 14:10 testing.sh
  
```
Please explain.
Thanks in anticipation....

---

### Post by bilol on 2009-08-03
I got it. The following output clarifies it.I suppose, here the mounted media EduDocu(type NTFS) has default block size of 512 bytes,whereas in ext3 it is 4096 bytes.
```
dhiman@dhiman-desktop:~$ ls -lsh /media/EduDocu/EduDocu/DKode_old
total 7.0K
4.0K -rwxrwxrwx 1 root root 679 2009-03-02 16:18 arr1.sh
1.0K -rwxrwxrwx 1 root root 596 2009-03-02 14:11 bubble.sh
   0 drwxrwxrwx 1 root root   0 2009-05-14 15:21 c
 512 -rwxrwxrwx 1 root root  66 2009-03-31 14:09 hi.c
   0 drwxrwxrwx 1 root root   0 2009-05-14 15:20 html
   0 drwxrwxrwx 1 root root   0 2009-05-14 15:21 java
 512 -rwxrwxrwx 1 root root  59 2009-03-02 16:28 loop.sh
   0 drwxrwxrwx 1 root root   0 2009-05-14 15:21 steganography
 512 -rwxrwxrwx 1 root root  35 2008-12-15 13:45 test.c
 512 -rwxrwxrwx 1 root root  79 2009-03-02 14:10 testing.sh

```
Now the sum is 7=4+1+0+1/2+0+0+1/2+0+0+1/2+1/2

---

### Post by movieman on 2009-08-03
As far as I'm aware directories are never compacted (unless you move the files to a new directory and delete the old one), so you can't tell the size of the directory from the number of files it currently contains because it might have previously contained 30,000 files which were then deleted.

---

### Post by bilol on 2009-08-05
Thanks movieman....
But the thing that I am really getting confused is the following:
```
dhiman@dhiman-desktop:~$ cd /media/EduDocu/EduDocu/
dhiman@dhiman-desktop:/media/EduDocu/EduDocu$ ls -lshd codeDoc DKode DKode_old 
   0 drwxrwxrwx 1 root root    0 2009-05-14 15:21 codeDoc
   0 drwxrwxrwx 1 root root    0 2009-07-06 14:10 DKode
4.0K drwxrwxrwx 1 root root 4.0K 2009-05-14 15:21 DKode_old
```

How can the size of the directory(codeDoc) be 0 ,though it is  non-empty.
For further assistance I am providing the following information:
```
dhiman@dhiman-desktop:/media/EduDocu/EduDocu$ ls -lsh codeDoc DKode DKode_old 
codeDoc:
total 208K
36K -rwxrwxrwx 1 root root 33K 2009-02-26 16:34 clc1.doc
36K -rwxrwxrwx 1 root root 36K 2009-02-18 12:57 clc.doc
28K -rwxrwxrwx 1 root root 26K 2009-02-19 16:37 firstPCPCA.doc
28K -rwxrwxrwx 1 root root 27K 2009-02-19 16:47 function PC.doc
44K -rwxrwxrwx 1 root root 44K 2009-03-23 15:24 function WX.doc
20K -rwxrwxrwx 1 root root 20K 2009-02-13 14:02 Hi.doc
16K -rwxrwxrwx 1 root root 15K 2009-02-18 13:59 PCA.rar

DKode:
total 0
0 drwxrwxrwx 1 root root 0 2009-07-06 14:10 C
0 drwxrwxrwx 1 root root 0 2009-07-06 17:16 MatLab

DKode_old:
total 7.0K
4.0K -rwxrwxrwx 1 root root 679 2009-03-02 16:18 arr1.sh
1.0K -rwxrwxrwx 1 root root 596 2009-03-02 14:11 bubble.sh
   0 drwxrwxrwx 1 root root   0 2009-05-14 15:21 c
 512 -rwxrwxrwx 1 root root  66 2009-03-31 14:09 hi.c
   0 drwxrwxrwx 1 root root   0 2009-05-14 15:20 html
   0 drwxrwxrwx 1 root root   0 2009-05-14 15:21 java
 512 -rwxrwxrwx 1 root root  59 2009-03-02 16:28 loop.sh
   0 drwxrwxrwx 1 root root   0 2009-05-14 15:21 steganography
 512 -rwxrwxrwx 1 root root  35 2008-12-15 13:45 test.c
 512 -rwxrwxrwx 1 root root  79 2009-03-02 14:10 testing.sh

```
Thanks in anticipation.....

---

### Post by movieman on 2009-08-06
If you're looking at files in /media, presumably that's a non-native file system, like a CD or FAT USB stick?

Linux native file systems such as ext3 should never show a directory size of zero bytes.

---

### Post by johnl on 2009-08-06
Do you need to 'calculate' this value from the files, or do you just need to retrieve the value?  You can get the size of a directory (or any other 'file') with 'stat':

```

#include <stdlib.h>
#include <stdio.h>
#include <sys/stat.h>

/* usage: ./a.out <list of files...> */
int main(int argc, char* argv[])
{
    int i;
    struct stat buf;
    for(i = 1; i < argc; ++i) {
        if (!stat(argv[i], &buf)) {
            printf("%s: %ld bytes\n", argv[i], buf.st_size);
        } else {
            printf("%s: failed to stat\n", argv[i]);
        }
    }

    return 0;
}

```

---

