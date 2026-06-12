---
title: "Running debug firefox (firefox-dbg)"
date: 2006-08-08
forum: Programming Talk
---

### Post by FuturePast on 2006-08-08
Hi,

I'm having some problems writing an XPCOM component for firefox, and I'd like to run the debug version installed from package firefox-dbg.

All the files are installed to /usr/lib/debug/usr/lib/firefox.

Anyone have any tips on what to do next?

---

### Post by amiro on 2007-03-22
Hi, 

Did you figure out how to accomplish that?

If yes, could you explain me how?

[email]alexander.miro@gmail.com[/email]

Thanks 
Alex

---

### Post by FuturePast on 2007-03-22
Hi,

I found out that the package firefox-dbg does not install a debug version of firefox. It installs the symbol table files needed for running firefox in a debugger such as gdb.

What  I actually wanted was a version of firefox built with debugging flags which turns on more verbose logging.
There are a few ways of doing this. I downloaded the ubuntu source package (see instructions [here]("http://www.debian-administration.org/articles/20") for example, then
changed the build configuration and rebuilt the package.
Or you could download the source from the mozilla site and do the same.

I can't remember exactly the steps I took, but it did work, so feel free to ask more questions if required.

---

### Post by FuturePast on 2007-05-10
Ok, I had to do this again so I'm going to note down the steps:
```
[if required] sudo apt-get install fakeroot devscripts
apt-get source firefox
sudo apt-get build-dep firefox
cd firefox-x.x.x/
DEB_BUILD_OPTIONS=debug debuild -us -uc
```

Wait.

Install .deb and run.

Logging and tracing works as so:
```
$ NSPR_LOG_MODULES=<moduleName>:2 firefox

Where:
PR_LOG_NONE = 0,                /* nothing */
PR_LOG_ALWAYS = 1,              /* always printed */
PR_LOG_ERROR = 2,               /* error messages */
PR_LOG_WARNING = 3,             /* warning messages */
PR_LOG_DEBUG = 4,               /* debug messages */

```

---

### Post by coldfire82 on 2008-07-11
> **FuturePast said:**
> Ok, I had to do this again so I'm going to note down the steps:
```
[if required] sudo apt-get install fakeroot devscripts
apt-get source firefox
sudo apt-get build-dep firefox
cd firefox-x.x.x/
DEB_BUILD_OPTIONS=debug debuild -us -uc
```

Wait.

Install .deb and run.

Logging and tracing works as so:
```
$ NSPR_LOG_MODULES=<moduleName>:2 firefox

Where:
PR_LOG_NONE = 0,                /* nothing */
PR_LOG_ALWAYS = 1,              /* always printed */
PR_LOG_ERROR = 2,               /* error messages */
PR_LOG_WARNING = 3,             /* warning messages */
PR_LOG_DEBUG = 4,               /* debug messages */

```

how and what exactly to install for .deb  ?

---

### Post by FuturePast on 2008-07-13
```
sudo dpkg -i firefox-xxxxxxxx.deb
```

---

### Post by Jamie Jackson on 2009-03-16
My FF is crashing on me when logging into a certain site, and I've followed your instructions.

Could you give a literal example of turning on verbose debugging? I don't quite know how to interpret this template:

```
NSPR_LOG_MODULES=<moduleName>:2 firefox

```

---

### Post by FuturePast on 2009-03-16
Logging can be controlled by module and module names are defined in the source code if you know where to look.

I think you probably want to enable all logging so try running the following on the command line```
$ NSPR_LOG_MODULES=all:5 firefox
```


More details here:
[http://www.mozilla.org/projects/nspr/reference/html/prlog.html](http://www.mozilla.org/projects/nspr/reference/html/prlog.html)

---

