---
title: "Cross compiling to 64-bit on 32-bit host"
date: 2007-08-06
forum: Programming Talk
---

### Post by sparkymat on 2007-08-06
Hi,

I have 2 Ubuntu machines at home - one with the 32-bit edition of Feisty and one with the 64-bit edition of Feisty. 

I was wondering if it is possible to cross-compile 64-bit programs for the 64-bit Feisty on the 32-bit Feisty (I know that 32-bit binaries would work on the 64-bit with IA32 libs but wondering if 64-bit binaries can be produced on the 32-bit machine).

Regards,
Sparkymat

---

### Post by sparkymat on 2007-08-06
I managed to find out the answer by snooping around in synaptic. :-) . Installing 'lib64gcc1','libc6-amd64' and 'libc6-dev-amd64' lets me compile programs for 64-bit. I just need to add a  '-m64' option to gcc to generate 64-bit binaries.

Now only need to figure out how to get the commonly used 64-bit libraries installed.

---

### Post by sparkymat on 2007-08-07
Sorry for the hasty post. Installing these screwed up my 32-bit gcc. I need to keep both in parallel. Still trying to figure it out. Will update as soon as i find something.

---

### Post by kevykev on 2007-12-05
I dont know if you still have this problem or if you figured it out, but I managed to solve it by installing the gcc-4.x-multilib and g++-4.x-multilib packages from the repository. Then you can compile for 64 bit using the -m64 -fPIC flags

---

### Post by Schuttwegraeumer on 2008-05-25
and how can I set the target CPU with configure?

---

### Post by Joeb454 on 2008-05-25
Check the date of the post above your's ;)

And I don't know if you can do for ./configure because originally the posters were talking about gcc - the GNU C Compiler

---

