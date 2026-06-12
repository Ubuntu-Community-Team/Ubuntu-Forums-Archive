---
title: "Installing USB DSL drivers"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by LvxDemos on 2008-11-18
Hello all, first time poster here!

I've installed Ubuntu 8.10 and I'm having some problems getting my USB DSL modem to work.

I've downloded ECIADSL drivers (BTW, is it called drivers on Linux?) in the form of a tarball. I've tried following the instructions on the Eciadsl.org site but I'm stuck on unpacking the tarball. In the terminal I have entered the command "tar xvfz nameofthefile.tar.bz2" and I recieve an error "Cannot open: No such file or directory". The file in question is on my desktop and in the terminal I'm at "myname@myname-desktop" so I assume that I've put the file in the correct place.

Any help would be much obliged, thanks!

---

### Post by cwsnyder on 2008-11-18
If you type ```
ls
``` does it list nameofthefile.tar.bz2 as a file in the folder?

Normally the correct prompt for being in the desktop folder is ```
myname@myname-desktop:~/Desktop$
```

You may just have to ```
myname@myname-desktop:~/Desktop$ cd Desktop
``` to fix the problem.

---

### Post by chrisod on 2008-11-18
You need to either be in the same directory as the compressed file, or provide the path to the file. Probably easier to just cd your way to the proper directory. Then the tar command should work just fine.

---

### Post by nhasian on 2008-11-19
personally i dont like attaching network devices via USB.  doesnt your DSL modem have an ethernet port?  they are a lot more reliable.  if your pc doesnt have an ethernet adapter, they can be had as cheap as $10.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833180026](http://www.newegg.com/Product/Product.aspx?Item=N82E16833180026)

---

