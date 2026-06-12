---
title: "How to use Ratfor or fweb for compiling .rat files"
date: 2009-05-09
forum: Programming Talk
---

### Post by kush007 on 2009-05-09
I have received  a folder containing files with extensions ".rat", ".nic" and ".f". The place from where I got this folder said that, it is written in ratfor (rational fortran). After searching for it in synaptic package manager, i have installed ratfor and fweb. Now, after that I dotn have a clue of how to go about it. I need a step by step solution to this problem since I am very new to ubuntu and fortran programming.

If someone knows, then please help.


OK, so what I have done is added the folder in .tar form in this link, so that it can be downloaded.(very small 70 KB file)
[http://homepages.iitb.ac.in/~kush007/send.tar](http://homepages.iitb.ac.in/~kush007/send.tar)
If you download it, you can see the .rat files in it. I need to compile them and run them to get results and graphs. Please help.

---

### Post by Victor Liu on 2009-05-31
From what I gather at looking at the makefile and the original ratfor documentation, you should just run make (just type "make") first to convert all the .rat files into .f files. Then you can compile together all the fortran files ("g77 *.f -o read", or something like that). The final executable should be called "read". I haven't actually done any of what I just described, so I'm not sure this will work. I hope this at least gives you an idea of what to do.

---

