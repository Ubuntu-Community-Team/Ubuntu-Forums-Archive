---
title: "installing Nvidia"
date: 2012-07-09
forum: New to Ubuntu
---

### Post by barrykgerdes on 2012-07-09
This is another thread closed too soon

I will put the question another way.

If I click on the Nvidia file I am asked do i want to run it or display its contents.

If I say run in a terminal the file is opened and checked but then says it needs to be installed as "root"

How do I run it in a terminal as sudo so I don't need to login as root

The file is "NVIDIA-Linux-x86-96.43.20-pkg1.run"

Barry

---

### Post by Elfy on 2012-07-09
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

As I posted earlier :)

---

### Post by barrykgerdes on 2012-07-09
I read through that article and tried to do what was suggested but had no success.

I hoped someone who had installed the necessary files would have given a simple instruction. I guess I will figure it out eventually.

The main problem I came up against is that a program that ran perfectly on my computer under 10.04 using an intel graphics card will not run on 12.04 except in native(no opeGl or card specific drivers) mode. I changed the graphics card to an old Gforce2 to see if it was the card problem but the new card has the same problem. On another computer with 11.10 and an ATI card the program also ran faultlessly.

Barry


Barry

---

### Post by coffeecat on 2012-07-09
> **barrykgerdes said:**
> 
The file is "NVIDIA-Linux-x86-96.43.20-pkg1.run"

If you're running 12.04, that version of the nvidia driver is in the repos as the package nvidia-96. Have you tried installing that either with apt-get or with Software Centre?

---

### Post by barrykgerdes on 2012-07-09
I haven't tried to install that file separately but I am quite sure that it did get installed when I ran 12.04 in recovery mode because before I ran recovery I only had the basic screen driver in non Opengl 1024 x 768 mode

The problem is something else with 12.04 that I am yet to find out. This is not the first problem I had with 12.04 on this computer. I spent weeks trying to install 12.04 into Windows but never got past the first stage. I later found out that the problem was the wifi card not being recognised but there was no indication that this was the problem.

I am not a regular user of Linux. I have it on three computers solely to build and test Stellarium and QB64 in on a Linux platform

Barry

---

