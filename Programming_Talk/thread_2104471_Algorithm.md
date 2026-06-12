---
title: "Algorithm"
date: 2013-01-13
forum: Programming Talk
---

### Post by rushikesh988 on 2013-01-13
I have created the website in PHP.Now I want to create the package in deb that will install all its dependancies like apache,php5. and automaticall copy all the files into the var/www folder


I am very much new to linux programming . and know python programming language.

Do somebody have any idea about how to implement it or any kind of material (links ) for referance

---

### Post by PaulM1985 on 2013-01-14
Did you check the stickies?  Specifically, [http://ubuntuforums.org/showthread.php?t=1766253](http://ubuntuforums.org/showthread.php?t=1766253)

---

### Post by jorok_tupur on 2013-01-26
Check on the [Ubuntu Packaging Guide]("http://developer.ubuntu.com/packaging/html/").

It teaches how to do packaging for Ubuntu, and how to setup your own PPA.

BTW, the same guide is available in the repository, that means you can install it and browse it offline.

```
sudo apt-get install ubuntu-packaging-guide
```After installing that, you can browse the guide from /usr/share/doc/ubuntu-packaging-guide-html/index.html.

It is also available as PDF and EPUB.

```
sudo apt-get install ubuntu-packaging-guide-pdf ubuntu-packaging-guide-epub
```

---

