---
title: "do i need to download cygwin?"
date: 2006-12-23
forum: Programming Talk
---

### Post by wannaBeHacker on 2006-12-23
Hey guys i have just recently converted to linux, and before that i was using a combo of eclipse and cygwin to program in opengl/c++

my question is do i need to download cygwin, or does linux (ubuntu) already have a compiler installed to program..

if so are there any additional software i need to download if so can you please list them..

if not... i should not have any problems downloading cygwin and eclipse right?

Thanks

---

### Post by qamelian on 2006-12-23
You definitely don't need to install cygwin and eclipse is already available in the Ubuntu repositories via apt-get, aptitude, synaptic, etc. You may, however, need to install the build-essential package as below:

Open a terminal (Applications > Accessories > Terminal) and type at the prompt ```
sudo aptitude install build-essential
```

When prompted for a password, use your own account password. This will install the basic tools you need to start compiling stuff.

---

### Post by wannaBeHacker on 2006-12-23
thanks so much for your reply, im sorry for being stupid but can you please explain what you meant by > eclipse is already available in the Ubuntu repositories via apt-get, aptitude, synaptic, etc.

im not sure what you mean by repositories, and what are apt-get, aptitude, and synaptics. my programming lingo is not the best.


what about as far as opengl goes dont i need to installed the opengl libs such as opengl, glu, and glut? i used to use opengl32, glu32, glut32 but i know that was designed for windows.

---

### Post by lloyd mcclendon on 2006-12-23
do not use the package in the repositories, it's old and a pain in the ***

[www.yoxos.com/ondemand](www.yoxos.com/ondemand) is the best **** ever

and if you don't have java installed search this forum for automatix, it's the easiest way to get it

---

### Post by qamelian on 2006-12-23
> **lloyd mcclendon said:**
> do not use the package in the repositories, it's old and a pain in the ***

[www.yoxos.com/ondemand]("http://www.yoxos.com/ondemand") is the best **** ever

and if you don't have java installed search this forum for automatix, it's the easiest way to get it
The version in the repositories is neither old nor a pain of any kind. The version in the edgy repositories is the same version as is available through yoxos. Both are 3.2.1.

---

