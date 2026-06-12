---
title: "Installing Libharu"
date: 2012-07-09
forum: New to Ubuntu
---

### Post by rossfh on 2012-07-09
I'm trying to install a program called libharu using these instructions [http://libharu.org/wiki/Documentation/Install](http://libharu.org/wiki/Documentation/Install)

When I run the configure script, I get an error that says: 

checking Zlib install prefix... configure: error: Unable to locate Zlib headers, please use --with-zlib=<DIR>

So I do that and it gives an error saying:

No such file or directory

I'm running Ubuntu 10.04 LTS and I really don't know what I'm doing, help!

---

### Post by glennric on 2012-07-09
You need to install the development headers for zlib.  The package name is zlib1g-dev (At least on Ubuntu 12.04 - It should be similar on 10.04).

---

### Post by glennric on 2012-07-09
Why are you trying to build libharu?  This library is available in the Ubuntu repositories.  The package name is libhpdf-2.2.1
Install it with
```
sudo apt-get install libhpdf-2.2.1
```

By the way, what program do you really want to install that uses this library?  You might check if that is in the repositories as well.

---

### Post by Curtis6767 on 2012-07-09
> **glennric said:**
> Why are you trying to build libharu?  This library is available in the Ubuntu repositories.  The package name is libhpdf-2.2.1
Install it with
```
sudo apt-get install libhpdf-2.2.1
```By the way, what program do you really want to install that uses this library?  You might check if that is in the repositories as well.

I was just checking in the Software Center and when I searched for Libharu I came up with  libhpdf-dev. I then clicked on the Developer Web Site and it took me to the Libharu web site.

Might be a lot easier just to install from the Software Center

Edit: Course I'm using 12.04, which may be why I have it in the Software Center and I have no idea what you might have available in 10.04

---

### Post by glennric on 2012-07-09
Curtis6767:  The packages that you see in the Software Center are the same as the ones installed on the command line.  The libhpdf-dev package is the package containing the development headers.  The library itself is contained in the libhpdf-2.2.1 package.  Of course all of this is on Ubuntu 12.04.  So you make a good point about 10.04.  After a quick Google search it seems that the package may not be available there.  So that would answer my question as to why rossfh is trying to build it.

---

### Post by Curtis6767 on 2012-07-09
> **glennric said:**
> Curtis6767:  The packages that you see in the Software Center are the same as the ones installed on the command line.  The libhpdf-dev package is the package containing the development headers.  The library itself is contained in the libhpdf-2.2.1 package.  Of course all of this is on Ubuntu 12.04.  So you make a good point about 10.04.  After a quick Google search it seems that the package may not be available there.  So that would answer my question as to why rossfh is trying to build it.
  
There is a repository listed on the Libharu.org home page and as long as rossfh trusts the site, then that might be the way to go.

---

### Post by glennric on 2012-07-09
There is not an Ubuntu package repository listed on the libHaru site.  The only repository listed is a git repository.  That is for downloading the source code with all of the latest development work.  He already has the source code (which is directly available for download from that site).  So that won't help.

---

### Post by Curtis6767 on 2012-07-09
> **glennric said:**
> There is not an Ubuntu package repository listed on the libHaru site.  The only repository listed is a git repository.  That is for downloading the source code with all of the latest development work.  He already has the source code (which is directly available for download from that site).  So that won't help.

My bad on that.

---

### Post by rossfh on 2012-07-11
Looks like I just needed to install the development headers for zlib.  Thanks so much!!

---

