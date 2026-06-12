---
title: "Shell script to copy all php,javascript and css files"
date: 2010-08-26
forum: Programming Talk
---

### Post by ivikas on 2010-08-26
Hello all,

            I have a php development folder say 'abcwebsite'.This  folder contains all php files,javascript files,css files.Inside the main website directory that is (abcwebsite)all other files are in separate sub-directory like JavaScript files in js folder,css files in css folder and so on. This folder structure should be maintained in the directory copy.

I need to copy all THESE FILES(without losing the directory structure and without copying all other files like images and other files) with a three day snapshot type in different folders like this.

abcwebsite_Current

abcwebsite_1DayOld 

abcwebsite_2DayOld

This should rotate as days roll on.

Please tell a way to achieve this,any idea or web link will be highly appreciated.

Thanks in advance.

---

### Post by Some Penguin on 2010-08-26
Simple with find/tar/xargs.

```

myid@myhost /tmp/foo $ mkdir bar
myid@myhost /tmp/foo $ mkdir wombat
myid@myhost /tmp/foo $ touch bar/copy.me
myid@myhost /tmp/foo $ touch wombat/copy.this.too
myid@myhost /tmp/foo $ touch bar/nocopy
myid@myhost /tmp/foo $ touch bar/okay.you.can.copy.this 
myid@myhost /tmp/foo $  find . -name copy\* -o -name okay\* | xargs tar -cvf blah.tar
./wombat/copy.this.too
./bar/copy.me
./bar/okay.you.can.copy.this
myid@myhost /tmp/foo $ tar -tvf blah.tar
./wombat/copy.this.too
./bar/copy.me
./bar/okay.you.can.copy.this
myid@myhost /tmp/foo $ cd ..
myid@myhost /tmp/foo $ mkdir bar
myid@myhost /tmp/foo $ cd bar
myid@myhost /tmp/foo $ tar -xvf ../foo/blah.tar
./wombat/copy.this.too
./bar/copy.me
./bar/okay.you.can.copy.this

```

---

### Post by DaithiF on 2010-08-26
Hi,
at the risk of going off-topic, why not use a revision control system (subversion, git, bzr, etc...)?  Then you could go back to ANY point in time, and you wouldn't have to re-invent the wheel like this.

---

### Post by ivikas on 2010-08-26
hello all,

        Iam aware of the versioning system.But most of the designers and developers are not comfortable with the subversion system commands like the check in ,checkouts....also knows there's a GUI for windows like tortoiseSVN but don't fine one for Linux client.
So this is entirely a needed one.Pls if you could help me a way out.

Thanks

---

