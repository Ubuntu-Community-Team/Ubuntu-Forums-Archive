---
title: "libgnomeui-2.0 missing?"
date: 2006-06-30
forum: Programming Talk
---

### Post by bieber on 2006-06-30
Trying to build a simple project with Glade, I find myself getting this error upon running autogen.sh
```

checking for PACKAGE... configure: error: Package requirements (libgnomeui-2.0) were not met:

```

I looked in Synaptic, but the only package I could find was libgnomeui-0 and lignomeui-32.  How do I get libgnomeui-2?

Edit-If I download the final project source and try to compile it (from a tutorial), I also get these errors

```

No package 'libgnome-2.0' found
No package 'libgnomeui-2.0' found
No package 'libglade-2.0' found

```

In Synaptic, I'm seeing libgnome2-0 and libglade0.  Is something just wrong with my system?

Yet another edit - I just had to install the dev packages.  *Wow*, I feel like an idiot now...

---

### Post by shawnhcorey on 2007-04-14
Thanks for your posting. I got mine working by downloading the dev packages.

---

### Post by atma_64 on 2008-01-17
Hi there

I am having the same problem where lib-gnomeui-2.0 is missing.

i am just a beginner with ubuntu so could someone please tell me as soon as possible maybe step by step how i can solve the problem? or even how to download the dev packages so that i can solve the problem?

thanks
atma

---

### Post by atma_64 on 2008-01-17
ok problem sorted...


had to install libgnomeui-dev 

thanks

---

### Post by stijngysemans on 2008-06-08
got the same issue, executing command: sudo apt-get install libgnomeui-dev results in broken packages:


I'm using Hardy and want to compile f-spot from source to make some changes.
```

 sudo apt-get install libgnomeui-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgnomeui-dev: Depends: libbonoboui2-dev (>= 2.13.1) but it is not going to be installed
                  Depends: libgnomecanvas2-dev (>= 2.6.0) but it is not going to be installed
                  Depends: libgtk2.0-dev (>= 2.9.0) but it is not going to be installed
E: Broken packages


```

---

### Post by victorbstan on 2009-08-20
I'm getting this error after ./configure:

configure: error: cannot run /bin/bash ./config.sub

What's that about?!

---

