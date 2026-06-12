---
title: "install ubuntu 11.10 full after windows"
date: 2012-03-24
forum: New to Ubuntu
---

### Post by florin1123 on 2012-03-24
hi!
 
i want to know if it possible to install ubuntu(11.10) without burning a cd or make a bootable usb stick.i know wubi.exe , but i want to install without a dual boot.I have a single partition (C) where is installed windows 7.
 
Thanks !:popcorn:

---

### Post by cortman on 2012-03-24
Hi, welcome to the forums!

So you're saying you want to replace Win7 with Ubuntu? Easily done, but you'll need to make a live CD or USB. It's a very easy process, even in Windows.

---

### Post by NikTh on 2012-03-24
Hello, 
your question is interesting. I never thought about it. No CD , no usb . How do you install without any of these ? 
Lets see what others will answer . 
Of course you talk about a regular install. don't you ? You don't want VirtualBox i guess.

---

### Post by florin1123 on 2012-03-24
i hate windows because has low security, and a big price.I was installed last year  ubuntu 10.04 with a usb stick (i have netbook), but now i don't have a usb stick.i can install windows 7 full(like a single OS), with daemon tools.Ubuntu work like this?

---

### Post by cortman on 2012-03-24
> **florin1123 said:**
> i hate windows because has low security, and a big price.I was installed last year  ubuntu 10.04 with a usb stick (i have netbook), but now i don't have a usb stick.i can install windows 7 full(like a single OS), with daemon tools.Ubuntu work like this?

[Here's]("http://linux-software-news-tutorials.blogspot.com/2010/06/4-ways-to-install-ubuntu-without-cd-or.html") some stuff on network installation, but you'd better have a pretty reliable internet connection, and an unlimited or fairly large plan.
There's also the [wiki]("https://help.ubuntu.com/community/Installation"), of course.

---

### Post by NikTh on 2012-03-24
> **NikTh said:**
> 
Lets see what others will answer . 

> **cortman said:**
> [Here's]("http://linux-software-news-tutorials.blogspot.com/2010/06/4-ways-to-install-ubuntu-without-cd-or.html") some stuff on network installation,

Yes.. !!! Network installation. Great ! :razz:
Thank you  cortman , i am going for reading now cause maybe i will need something like that in the future.

---

### Post by florin1123 on 2012-03-25
> **cortman said:**
> [Here's]("http://linux-software-news-tutorials.blogspot.com/2010/06/4-ways-to-install-ubuntu-without-cd-or.html") some stuff on network installation, but you'd better have a pretty reliable internet connection, and an unlimited or fairly large plan.
There's also the [wiki]("https://help.ubuntu.com/community/Installation"), of course.
   For me not work.I was downloaded mini.iso,and unzip it.I can't find setup.exe.

---

### Post by Mark Phelps on 2012-03-25
Either you're installing using a network or you're trying to install locally, without using one.  We need to know WHICH approach you're trying in order to help you.

If you're using the local option, and using unetbootin (as in the example provided), you can NOT install to the same partition containing the unetbootin program!  What you would be trying to do is run a Linux installer from inside Windows that then wipes out Windows and installs itself in it's place -- which can't be done.  The unetbootin example presumes you're going to install Linux to a NEW partition separate from the one containing MS Windows.

---

