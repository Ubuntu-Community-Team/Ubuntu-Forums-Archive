---
title: "C++: how to compile example using boost"
date: 2009-06-16
forum: Programming Talk
---

### Post by froggyswamp on 2009-06-16
Folks, what are the command line arguments to g++ to compile this?
Asking cause pkg-config doesn't know about boost, but I do have it installed, I have Jaunty.

```

#include <iostream>
#include <boost/thread/thread.hpp>
#include <boost/thread/mutex.hpp>
#include <boost/bind.hpp>

boost::mutex io_mutex;

void count(int id) {
    for (int i = 0; i < 10; ++i) {
        boost::mutex::scoped_lock lock(io_mutex);
        std::cout << id << ": " << i << std::endl;
    }
}

int main(int argc, char* argv[]) {
    boost::thread thrd1(boost::bind(&count, 1));
    boost::thread thrd2(boost::bind(&count, 2));
    thrd1.join();
    thrd2.join();
    return 0;
}


```

---

### Post by SledgeHammer_999 on 2009-06-16
In order to see which packages pkg-config has info about do a:
```
 pkg-config --list-all
```
If you have installed boost's -dev files then it should be in the list(haven't tried it)

---

### Post by dwhitney67 on 2009-06-16
For the shared-object library:
```

g++ YourApp.cpp -lboost_thread

```

If you want the static version of the library:
```

g++ YourApp.cpp -static -lboost_thread

```

---

### Post by dwhitney67 on 2009-06-16
Btw, don't you want your threads to run concurrently?  I thought that one had to add their individual threads to a Boost thread_group, then perform the join (i.e. join_all())?

P.S.  Try this:
```

#include <iostream>
#include <boost/thread/thread.hpp>
#include <boost/thread/mutex.hpp>
#include <boost/bind.hpp>

boost::mutex io_mutex;

void count(int id) {
    for (int i = 0; i < 1000; ++i) {
        usleep(1000);   // give up time-slice
        boost::mutex::scoped_lock lock(io_mutex);
        std::cout << id << ": " << i << std::endl;
    }
}

int main(int argc, char* argv[]) {
    boost::thread_group tgroup;
    tgroup.add_thread(new boost::thread(boost::bind(&count, 1)));
    tgroup.add_thread(new boost::thread(boost::bind(&count, 2)));
    tgroup.join_all();
}

```

---

### Post by froggyswamp on 2009-06-16
Thanks a lot!!
-lboost_thread worked like a charm!

btw, at least on Jaunty pkg-config --list-all doesn't list boost among other packages, don't know if it's supposed to.

---

### Post by stair314 on 2009-06-16
> **dwhitney67 said:**
> Btw, don't you want your threads to run concurrently?  I thought that one had to add their individual threads to a Boost thread_group, then perform the join (i.e. join_all())?

[/code]

I believe thread_group is only for convenience (not needing to call join repeatedly). It isn't necessary to get threads to run in parallel.

---

### Post by Fatman_UK on 2009-11-09
> **froggyswamp said:**
> pkg-config --list-all doesn't list boost among other packages, don't know if it's supposed to.

Apologies for waking an old thread, but I thought this was of general interest.

It seems the Boost package maintainers don't generate the .pc files used by pkg-config. There have been discussions about it on the Boost mailing list since 2005, but they don't seem to have reached a conclusion. At least, I haven't found anything. :( They do say bjam can create .pc files, but that's only really useful if you build Boost yourself.

I'll raise a bug on Launchpad if there isn't one already.

---

### Post by A_Fiachra on 2009-11-09
If you figure out how to use bjam ... please post it here!!!!!



That has to be the worst documented program I've ever tried to use.

---

### Post by Fatman_UK on 2009-11-11
> **A_Fiachra said:**
> If you figure out how to use bjam ... please post it here!!!!!

That has to be the worst documented program I've ever tried to use.

Agreed. You'd think they would have made Boost more GCC friendly.

I think my solution will be to hand-code some .pc files, though I haven't looked into the feasibility of that. If I do, I'll definitely share.

---

### Post by jmlynn on 2009-12-23
Hi,

I am new to ubunto.  Can someone help me by showing me a few pointers on how to build the Boost C++ library?

I have downloaded the latest library, yet it is composed of source only, no prebuild .so.

Following the build instruction, I built the library.  However, instead of one single so file, I got quite a few .so files, one for date_time, one for system, etc.

Is there a way that I can build one single .so file, like libboost-1.41.0.so?

Thanks!

jml

---

### Post by MadCow108 on 2009-12-23
boost consists of many libraries (and headers) each serving a certain purpose.
why do you want one huge shared library?
it would just waste memory because you will probably not need every single part of boost in your project.

and under ubuntu you don't have build yourself, you can also install it over the packet manager. This is mostly easier (although you usually don't get the newest version).

---

