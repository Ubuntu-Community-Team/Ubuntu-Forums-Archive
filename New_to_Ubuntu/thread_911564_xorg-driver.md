---
title: "xorg-driver"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by Mr.Magoo on 2008-09-05
Hello,
   I am trying to get my ATI driver up and running.  I have tried several methods, to include ENVY.  None have fully worked.  Currently i am trying to remove what i suspect to be a half deleted xorg-driver file.  when i use 
sudo apt-get remove i get this

dpkg-divert: rename involves overwriting `/usr/lib32/libGL.so.1' with
  different file `/usr/lib32/fglrx/libGL.so.1.xlibmesa', not allowed
dpkg: error processing xorg-driver-fglrx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 xorg-driver-fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)

if anyone can help, that would be great.  thanks

---

### Post by Slug71 on 2008-09-05
Why dont you try it in Synaptic Package Manager?

---

