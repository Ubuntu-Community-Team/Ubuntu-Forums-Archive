---
title: "How to Create a Source Package"
date: 2008-04-16
forum: Programming Talk
---

### Post by GenuineXP on 2008-04-16
I'm working on a project written in C++ and I'm already using tools like make and Subversion. I'm wondering how I could use more advanced tools though, like those found with source packages I download. With those packages, I'm magically able to issue a simple ./configure --prefix={...}, followed by make, and finally make install. How can I do the same for my project?

I'm unaware of the actual tools that make this possible. If anyone could enlighten me that would be great. Also, any links to tutorials or documentation would be awesome too. I wanted to move my project into MonoDevelop since it handles these things for the developer, but then I decided I'd rather do things manually and learn about them.

Thanks!

---

### Post by t3hi3x on 2008-04-16
./configure is simply a shell script that detects where things are and generates an appropriate makefile. Also make install is just a section in your make file that copies the appropriate files to the root partition somewhere.

---

### Post by mssever on 2008-04-16
Those scripts are frequently from the GNU autotools project.

---

### Post by GenuineXP on 2008-04-16
I understand that configure is script and how make works, but I don't understand what tools are used to generate these special scripts and makefiles. I'll look into autotools to see if that answers me question.

Thanks!

---

### Post by WW on 2008-04-16
[autoconf](http://www.gnu.org/software/autoconf/manual/index.html)

---

