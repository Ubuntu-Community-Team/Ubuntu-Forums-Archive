---
title: "Manage compiled programs"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by xusword on 2008-08-22
Hi All

There are times that I download sources and build them into share libraries or applications. I am wondering how I can keep track and manage my installations so I will be able to remove them when I need to.

thanks

Absolute Absolute beginner

---

### Post by doorknob60 on 2008-08-22
If you use sudo checkinstall instead of sudo make install, you can manage them with apt-get, dpkg, synaptic and alll those good programs :)

---

### Post by mcduck on 2008-08-22
You really should, like suggested, use checkinstall.

What it does is that when compiling, instead of running "sudo make install" you run "sudo checkinstall". Checkinstall then creates a .deb package from the compiled code and installs that for you. This means that the installed programs is registered in Ubuntu's package management, and you can manage & uninstall it just like any other package.

(By the way, .deb packages created with checkinstall shouldn't be distributed. They might not work correctly on other machines because they don't contain correct information about dependencies. This is not a problem on your own machine, you already have all the dependencies installed if you were abe to compile the program, but other people might not have them.)

---

### Post by kpkeerthi on 2008-08-22
[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

### Post by xusword on 2008-08-22
thanks for all your help

HMM... How do I mark this topic "[SOLVED]" and how do I post a "thank"(Thanked 0 Times in 0 Posts)?

---

### Post by cardinals_fan on 2008-08-22
> **xusword said:**
> thanks for all your help

HMM... How do I mark this topic "[SOLVED]" and how do I post a "thank"(Thanked 0 Times in 0 Posts)?
See my reply to another of your posts [here]("http://ubuntuforums.org/showpost.php?p=5645711&postcount=6").

---

