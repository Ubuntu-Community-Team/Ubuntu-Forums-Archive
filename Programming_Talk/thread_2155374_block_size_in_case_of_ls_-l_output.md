---
title: "block size in case of ls -l output"
date: 2013-06-18
forum: Programming Talk
---

### Post by IAMTubby on 2013-06-18
Hello,
I understand that when you do a **ls -l**, the size portion lists the size in terms of **blocks**
However, I wanted to know what's the size of this block in terms of b or Kb etc.
So I read the manpage and I learnt of the **-h** option.
Comparing the 2 outputs, which are 105265 blocks and 103K, does that mean that 1block == (105265/103) == 1021K.


Just asking the question because 1021 doesn't sound like a "special" number.(As in not a power of 2)


```

$ ls -lh fileop.txt
-rw-rw-r-- 1 IAMTubby IAMTubby 103K Jun 18 00:17 fileop.txt
$ ls -l racdumpop.txt
-rw-rw-r-- 1 IAMTubby IAMTubby 105265 Jun 18 00:17 fileop.txt

```

Thanks.

EDIT : Now I'm totally confused, I did a **wc -c fileop.txt** and that gives me 105265(same as the block output). Since wc -c gives you the number of characters and each character is 8 bytes, does that mean 1 block == 8 bytes :o ?
EDIT : stupid of me, 1 character is 8 bits or 1 byte.

---

### Post by dargaud on 2013-06-18
```
ls -l --block-size=K
``` or more simply ```
ls -lk
```
wc actually reads the files and counts the characters in them (much slower than simply asking the filesystem how big the files are). The number of bytes is usually the same as the number of characters (unless you use sparse files and a few other caveats). A byte is 8 bits. Study this:
```
$ echo 1234567890 >/tmp/one
$ ls -s --block-size=1 /tmp/one; du -b /tmp/one; wc -c /tmp/one
4096 /tmp/one
11      /tmp/one
11 /tmp/one
 
```

---

### Post by trent.josephsen on 2013-06-18
```
% python
>>> 105265/1024
102.7978515625
>>> round(102.7978515625)
103
```
I don't see the problem.

---

### Post by IAMTubby on 2013-06-19
> **trent.josephsen said:**
> ```
% python
>>> 105265/1024
102.7978515625
>>> round(102.7978515625)
103
```
I don't see the problem.
Thanks trent.josephsen, what happened was because of the **.7978515625**, when I divided 105265/103, I was getting 1021 and not 1024.
I wasn't satisfied with the number 1021 because it's not a power of 2. But now it's all clear after you mentioned the rounding. Thanks!
> **dargaud said:**
> [CODE]ls -lk
Thanks dargaud.
So basically ls -l output lists the number of bytes ?
But some sites I referred told me that ls -l gives the output in terms of **blocks**. So does that mean that 1block==1byte unless set explicitly as --block-size=SIZE to say,use SIZE-byte blocks ?

---

### Post by trent.josephsen on 2013-06-19
> **IAMTubby said:**
> But some sites I referred told me that ls -l gives the output in terms of **blocks**.

That is *kind of* incorrect. Misleading, perhaps, is a better word. ls -l displays the apparent size of the file (what you would get from `du -b`), not how much disk space it uses. By default, -l uses a block size of 1 byte, so the number of blocks and the number of bytes is the same. ls -s displays disk usage instead (what you would get from `du`) and uses a different block size (1024 for me, but it can be different). When I talk about blocks in reference to files, this is the kind of file size I'm usually thinking of, so I wouldn't use the word "blocks" to describe the output of ls -l.

If you do a plain `du` or `ls -s` you'll probably notice that all the numbers are whole multiples of 4, even for files less than 4 kilobytes; this is because your filesystem has one inode every 4,096 bytes and every file has to take up at least one whole inode. This is just another thing to be aware of if you're wondering how file sizes actually work. (4096 is a typical number, but by no means universal -- it's possible to have an inode density of e.g. 8192 which would make all the numbers in `ls -s` be multiples of 8.)

---

