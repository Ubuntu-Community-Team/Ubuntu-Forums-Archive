---
title: "Installing nasm-2.09.10"
date: 2012-01-28
forum: Programming Talk
---

### Post by nutan123 on 2012-01-28
Hello everyone, I am new to this forum and new to the Linux environment. I have downloaded nasm-2.09.10.tar.gz from their website, as I wanted it to learn Assembly (using Assembly Language Step by Step) and extracted nasm-2.09.10 folder in my home directory. Now, how can I install nasm ?

---

### Post by nutan123 on 2012-01-28
One more thing, I have installed Ubuntu Natty Narwhal.

---

### Post by lisati on 2012-01-28
Threads merged. It doesn't make much sense to have "one further thing" in a separate thread.

---

### Post by lisati on 2012-01-28
*Thread moved to **Programming Talk**.*

---

### Post by Bachstelze on 2012-01-28
Since you just want to learn assembly, you probably don't need a specific version of nasm, so just install the version from the repositories with [font=monospace]sudo apt-get install nasm[/font] or using your favourite package manager.

---

### Post by nutan123 on 2012-01-29
I used sudo apt-get install nasm but it following was displayed :
 
reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package nasm
 
what should I do ?

---

### Post by Bachstelze on 2012-01-29
Check your repositories, because the package nasm exists, and it is in main too. So you definitely should have it.

---

