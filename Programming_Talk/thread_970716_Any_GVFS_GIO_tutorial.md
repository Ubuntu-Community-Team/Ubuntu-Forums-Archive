---
title: "Any GVFS GIO tutorial?"
date: 2008-11-04
forum: Programming Talk
---

### Post by cl333r on 2008-11-04
Hi,
I don't know whether GVFS / GIO is ready for "production", GVFS in Intrepid - how do I use it? Is there any (C/C++) tutorial? Google didn't yield anything useful. I only found the raw API.
I find tutorials much easier for learning.

---

### Post by nvteighen on 2008-11-04
What's actually GVFS meant to be? I know what it is, but what advantages does it offer?

---

### Post by cl333r on 2008-11-04
> **nvteighen said:**
> What's actually GVFS meant to be? I know what it is, but what advantages does it offer?
Well, I'm gonna/willing to use it cause it looks more Java-like (since I'm coming from Java).
But here's the "official" explanation:

> 
GIO is striving to provide a modern, easy-to-use VFS API that sits at the right level in the library stack. The goal is to overcome the shortcomings of GnomeVFS and provide an API that is so good that developers prefer it over raw POSIX calls. Among other things that means using GObject. It also means not cloning the POSIX API, but providing higher-level, document-centric interfaces.
....
 Beyond these, GIO provides facilities for file monitoring, asynchronous I/O and filename completion. In addition to the interfaces, GIO provides implementations for the local case. Implementations for various network file systems are provided by the GVFS package as loadable modules.

Other design choices which consciously break with the GnomeVFS design are to move backends out-of-process, which minimizes the dependency bloat and makes the whole system more robust. The backends are not included in GIO, but in the separate GVFS package. The GVFS package also contains the GVFS daemon, which spawn further mount daemons for each individual connection. 


---

