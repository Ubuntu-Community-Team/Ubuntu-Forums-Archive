---
title: "How can I get gmake?"
date: 2007-03-21
forum: Programming Talk
---

### Post by alphilli on 2007-03-21
I happen to need gmake to build the xercesc library. It does not seem to be available on my Ubuntu system.

I assumed I could execute a command something like: "apt-get install gmake"

All that gives me is the message: "E: Couldn't find package gmake".

What command do I need to execute to get "gmake"?

Thanks.

---

### Post by ansi on 2007-03-21
```
sudo ln -s /usr/bin/make /usr/bin/gmake
```

---

### Post by hod139 on 2007-03-21
gmake is make on Ubuntu (any GNU/Linux system actually).  What ansi did was make soft link setting gmake to point to make.

---

### Post by mac.ryan on 2007-03-21
...in other words, "gmake" is just an alias for "make", like "gcc" and "cc". I suppose this is due to small differences in naming conventions between unix and linux (g-nu)...

---

### Post by ssam on 2007-03-21
IIRC 
there are lots of implementations of make.
gmake is what gnu make is called on most unix systems, to differentiate it from other makes
gnu make has always been the default on linux, and so it is usually just called make.

---

### Post by alphilli on 2007-03-21
Thanks.

That helps.  Now at least I know that "gmake" isn't going to help me.  It's obviously going to have the same problems that "make" has. The Makefile that supposedly works fine on several versions of unix just doesn't work on linux.

---

### Post by WW on 2007-03-21
Is "xercesc" the same thing as the "Xerces C++  validating XML parser"?  If so, it *is* available in the Ubuntu repositories: [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libxerces27&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libxerces27&searchon=names&subword=1&version=all&release=all)

---

### Post by alphilli on 2007-03-22
Yes.  It is the Xerces C++ validating XML parser but I have to be able to build the shared libraries from source.

---

### Post by skarootz on 2008-05-15
I had a problem like that, now I realize that gmake is the same that the simply make commands, I'll try with this, thank you.:)

---

### Post by zerothis on 2008-12-19
(comment withdrawn)

---

### Post by LinuxGuy1234 on 2008-12-19
To fix everyone's "gmake" problem, do this:
```
sudo cp /usr/bin/make /usr/bin/gmake
```
You can do this with "ln -s" as well, but alas I can't test now.

---

