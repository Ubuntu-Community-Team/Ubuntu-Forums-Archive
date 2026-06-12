---
title: "File size"
date: 2011-09-03
forum: Programming Talk
---

### Post by nickos on 2011-09-03
Okay,,so i have seen some apps that are about 10 MB in total size.Does that mean that the developer did write 10 MB of code or does this contain all the libraries used to crate it?If so,what will be the total size of code written by the developer?


Q 2 : just asking,can someone add his/shes software to the ubuntu download center or is that onother special task?

---

### Post by MadCow108 on 2011-09-03
a 10mb application consisting only of code would be very large, it exists, but its more likely that it either contains lots of non-code data or is static linked.

static linked applications contain the code of all libraries they use so they tend to be very large (see e.g. skype and many other windows application).
A dynamic linked application is usually much smaller as it will load the libraries at runtime from the system
e.g. gedit, which is ~600kb in size, but it is in dynamically linked against 56 libraries. If these were all static linked it would also be several mb in size.

you can figure out against what an executable dynamically links by using ldd on it

---

### Post by cgroza on 2011-09-03
I am not sure if you are talking about the executable size or the size of the tarball of the application.

Some applications include the some HTML documentation with them (APIs and all that.).
This can inflate the application by a few MB. I see it often, when I run sloccount on some of them.

---

### Post by nickos on 2011-09-03
take gedit for example.1900 KB total size in disk.almost 2 MB
that number includes the whole libraries used to create gedit itself right?

---

### Post by doobrie on 2011-09-03
Also, apps sometime contain images and other resources.  These can increase the size of the executable.

---

### Post by nvteighen on 2011-09-03
> **nickos said:**
> take gedit for example.1900 KB total size in disk.almost 2 MB
that number includes the whole libraries used to create gedit itself right?

What do you refer to as 'gedit'? The gedit package or the gedit binary located at /usr/bin/gedit/? The deb package, as you've been told, also includes documentation, data and package metadata. The dependencies are not included in a regular deb package, because it's the package manager's task to download them separately.

The /usr/bin/gedit binary is only 624376 B long.

EDIT: Or are you referring to memory usage? A program may take a lot of memory despite being relatively small...

---

### Post by Arndt on 2011-09-03
The program 'size' can show you the respective sizes of the memory areas of the program: "text" is program code. "data" is initialized data.

```
$ size /usr/bin/gedit 
   text	   data	    bss	    dec	    hex	filename
 614637	   8632	    752	 624021	  98595	/usr/bin/gedit

```

---

