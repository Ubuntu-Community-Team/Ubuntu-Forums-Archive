---
title: "designing downloader apllication in python"
date: 2009-09-29
forum: Programming Talk
---

### Post by ali rana on 2009-09-29
hello!

i am a new programmer to python and developing a downloader application which can run on windows and linux (if it can). i have a working experience in C and C++. can any one help me out that how a downloader actually works? what is the statistics of a downloader? how it will be coded? can any one post the source code of any downloader? through which i can get idea that how will it be designed? i want to create a very simple application not much complexity. like main and basic options of any downloader.

---

### Post by Bachstelze on 2009-09-29
You can get the source for wget (which is the de facto standard download program for Linux) from the GNU FTP.

[ftp://ftp.gnu.org/gnu/wget/wget-1.12.tar.gz](ftp://ftp.gnu.org/gnu/wget/wget-1.12.tar.gz)

A bit simpler is fetch, which is the program used on BSD systems. Tell me if you would like the source for that.

---

### Post by unutbu on 2009-09-29
To write a downloader written in python you'd probably want to familiarize yourself with the urllib2 module:
[http://docs.python.org/library/urllib2.html#module-urllib2](http://docs.python.org/library/urllib2.html#module-urllib2)

There are examples near the end of the page.

---

### Post by ali rana on 2009-09-29
thnx [[COLOR=#D40000]**Bachstelzes**[/COLOR]]("http://ubuntuforums.org/member.php?u=51114") for your help. ya if have its code plz let me borrow it.

---

### Post by ali rana on 2009-10-09
can any one else help me out a bit more about my problem?

---

### Post by Bachstelze on 2009-10-09
Here you go

---

### Post by ali rana on 2009-10-13
thnx Bachstelzes.

---

### Post by ali rana on 2009-10-13
thanks unutbu for your help

---

