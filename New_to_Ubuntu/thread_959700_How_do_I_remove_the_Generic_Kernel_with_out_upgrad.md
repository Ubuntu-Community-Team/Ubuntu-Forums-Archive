---
title: "How do I remove the Generic Kernel with out upgrading"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by Qwertinsky on 2008-10-26
I have an EeePC-900 and I am using Ubuntu 8.04 with a custom kernel for the eee.

I want to totally remove the Generic Linux kernel to free up some disk space.

Now I go through Synaptic and select all the generic linux kernel, modules, and etc. for complete removal

But synaptic seems to only allow me to remove the old generic kernel AND install the latest generic kernel and says it will consume 1.5GB MORE SPACE

I want to REMOVE the generic stuff and use LESS space.

Why is it that hard to do?

---

### Post by Crandom on 2008-10-26
Anything to do with patching, compiling or removing kernels is incredible difficult, usually involving many, many terminal commands that is far beyond the reach of this "beginner talk" forum. I don't even know if it is possible to remove the generic kernel, as it may still be central to the system.

---

### Post by BDNiner on 2008-10-26
That is a good question, i would try and ask it in the main support category. but you can remove older, unused kernels. Did you complie your own kernel from scratch? when i used the real time kernel i had to have the generic kernel install along side it. for some reason i could not remove one without the other.

---

### Post by BDNiner on 2008-10-26
Check you this link:
[http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/](http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/)

---

### Post by Qwertinsky on 2008-10-26
> **BDNiner said:**
> Check you this link:
[http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/](http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/)

Yes I understand how to do that part. 

But when I select Linux-image-2.6.24-19-generic to be removed 
Synaptic automatically selects to install and upgrade everything to Linux-image-2.6.24-21.42-generic 
and says it will consume 1.4GB more space.

I am trying to free up more space not to use more space.

---

