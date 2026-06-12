---
title: "How to retrieve screenshots of a package in ubuntu"
date: 2015-05-30
forum: Programming Talk
---

### Post by wisdom2 on 2015-05-30
i'm developing an application which manipulates packages in ubuntu.  I'm working with python. I need to retrieve screenshots of packages by  using package-name. For example, say that package-name is filezilla. By  knowing package-name, i want to retrieve filezilla's screenshots and  then display these screenshots in my application's gui. 
  When i know the package-name, i can retrieve all details of a package  by using python-apt. But i don't know how to retrieve the package's  screenshots. 
  Thanks in advance.

---

### Post by ian-weisser on 2015-05-30
The same way you retrieved the package's icon in [an earlier thread]("http://ubuntuforums.org/showthread.php?t=2280166"). Same package.

From your description, seems like you are reinventing some of the easier bits of Software Center. Why?
If you are interested in Python, Ubuntu is looking for volunteers to port several Software Center dependencies from Python 2 to Python 3.

---

### Post by wisdom2 on 2015-05-31
> **ian-weisser said:**
> The same way you retrieved the package's icon in [an earlier thread]("http://ubuntuforums.org/showthread.php?t=2280166"). Same package.

From your description, seems like you are reinventing some of the easier bits of Software Center. Why?
If you are interested in Python, Ubuntu is looking for volunteers to port several Software Center dependencies from Python 2 to Python 3.

But i didn't find any directory which includes screenshots in my computer?

Yes, although i run my application and work in ubuntu, i actually develop this software center for another linux distrubition. My boss wants it because she wants to publish an original software center rather than ubuntu's one.

---

### Post by ian-weisser on 2015-05-31
> **wisdom2 said:**
> But i didn't find any directory which includes screenshots in my computer?

EDIT: kostkon's answer below is better than mine was.

---

### Post by kostkon on 2015-05-31
Screenshots are taken from [http://screenshots.debian.net/](http://screenshots.debian.net/) ([http://screenshots.ubuntu.com/](http://screenshots.ubuntu.com/) also redirects to it).

---

