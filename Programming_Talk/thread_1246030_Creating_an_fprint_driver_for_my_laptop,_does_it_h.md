---
title: "Creating an fprint driver for my laptop, does it have to be in C or C++?"
date: 2009-08-21
forum: Programming Talk
---

### Post by exutable on 2009-08-21
I have an HP HDX16-1370US, except for a few kinks pretty much everything works in Ubuntu except for my fingerprint reader.  After doing some research I found a guy that is developing this program called fprint.

[http://reactivated.net/fprint/wiki/Main_Page]("http://reactivated.net/fprint/wiki/Main_Page")

As it says in the Wiki, he is trying to close the gap of the Linux desktop by creating drivers for consumer fingerprint reading devices.


Now I want to create a fingerprint drivers but it appears that he has programmed everything in C++.  I only have knowledge of Java and Python and not with hardware interactions, busses or anything related

Is it possible to write drivers in those languages? Is it worth it because they run on virtual machines, too slow?

If so, where would I find some good startup guides on how to go about this?  and is Python or Java the better way to go?


Thanks in advance,

Dane

---

### Post by exutable on 2009-09-11
It seems that naturally it should be in C but could potentially be written in python if something like pyusb could interact with it.  It's a bad idea though because python isn't integrated in the kernel and C is much faster and more oftenly used for hardware.

---

### Post by lensman3 on 2009-09-11
You can force C++ to not fold the C names to C++

using:

#ifdef __cplusplus
extern "C" {
#endif

EVERYTHING HERE IS TREATED A C (as far as declarations go).

#ifdef __cplusplus
}
#endif

That way the new drivers you write in C can be called from his C++.

---

