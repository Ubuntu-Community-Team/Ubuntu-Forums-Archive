---
title: "Modifying existing software (gthumb)"
date: 2008-10-31
forum: Packaging and Compiling Programs
---

### Post by gimmejimmy on 2008-10-31
Hello, I've recently downloaded and installed gthumb.  I made a few changes to one of the .c files.  How do I compile another copy of the program so I don't affect the existing install?  Thanks.

---

### Post by ddrichardson on 2008-11-01
I don't know about this specific source but there is usually a base install folder in the Makefile that you could change to /opt if you wanted to do a make install.

However you chould be able to still compile it to your woriking folder and run it.

---

### Post by gimmejimmy on 2008-11-01
I uninstalled using Synaptic, then did ./configure, make and make install without errors.  checkinstall was giving me errors.  But when I type in gthumb it says command not found.  Help!

PS - Say I want to start from scratch and delete every file and directory with "gthumb" in the name, how do I do it?

Edit:

I deleted every file and directory with gthumb in the filename then re-downloaded the source code using apt-get source,  Then I made some modifications to one of the source files.  Then ./configure then make.  So far so good.  When I try sudo checkinstall -D I get:
> chmod 644 /usr/local/lib/libgthumb.a
chmod: changing permissions of `/usr/local/lib/libgthumb.a': No such file or directory
make[3]: *** [install-libgthumbLTLIBRARIES] Error 1
make[3]: Leaving directory `/home/moral/gthumb-2.10.8/libgthumb'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/moral/gthumb-2.10.8/libgthumb'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/moral/gthumb-2.10.8/libgthumb'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.


---

### Post by ddrichardson on 2008-11-01
I think you're getting a little confused - what is it you want to do and why are you mixing apt and compiling?

---

### Post by gimmejimmy on 2008-11-02
I was looking at different photo viewing software so I installed gthumb using apt-get or Synaptic, can't remember which.  It was the best fit but needed some tweaking for my needs so I downloaded the source to modify it.  I did this using "apt-get source".  I then removed the existing install and tried to compile, with "sudo checkinstall" failing with the error quoted above.

---

### Post by ad_267 on 2008-11-02
Usually when you run the configure script you can set a different prefix so that the program will install in a different location to the default installation.

eg: "./configure --prefix="$HOME/opt"

Which will install under the opt directory in your home directory.

---

### Post by mc4man on 2008-11-02
Why don't you just use a make command of this to create 'proper' .deb's (have fakeroot installed

```
fakeroot debian/rules binary
```

Then just install the resulting .deb(s) as normal (uninstall existing first.

The repo version will be seen as an upgrade even though it's the same as the above built so watch out for upgrades or lock the newly installed one in synaptic.

If you try above it's best to start fresh (or maybe run a make clean, starting over is best.


edit: it never hurts to run a ./configure --help for info and look at the rules file in the debian dir. to see if there are any useful edits.  (sometimes in a 'confflags' file

---

### Post by gimmejimmy on 2008-11-07
It's working now.  I had to manually copy two files into the proper folders and do ldconfig after checkinstall.  Thanks all.

---

