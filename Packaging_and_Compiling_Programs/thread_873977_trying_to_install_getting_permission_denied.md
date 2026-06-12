---
title: "trying to install getting permission denied"
date: 2008-07-29
forum: Packaging and Compiling Programs
---

### Post by exneo002 on 2008-07-29
I am using ubuntu hardy and I have been trying to compile from source by listing the directory of my gzip or bzip and then using the command instsall I get permission denied what am I doing wrong.

---

### Post by NilsE on 2008-07-29
Have you tried sudo in from of the command to give it root permissions?

---

### Post by flytripper on 2008-07-29
front*

---

### Post by pytheas22 on 2008-07-29
What exactly are you trying to install?  Generally you wouldn't type "install" to install something; you'd compile it first with "make" and then install the compiled binaries into the system with "sudo make install."  It would also be useful if you pasted here the output you're getting from the terminal so that we know exactly what it's saying.

---

