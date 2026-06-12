---
title: "adding library"
date: 2007-08-18
forum: Programming Talk
---

### Post by Rij on 2007-08-18
Greetings to the community.
I am new to this and I hope I have posted this question in the right forum.
I am installing ModelNet on my machine. modelNet expects a graph library called boost that I have downloaded and saved. Trouble is, the "configure" file (which I presume is generating the Makefile) is not able to locate the boost library. I tried saving it in two place: in my local folder and in /usr/local/lib. I added the path names to /etc/ld.so.conf and ran ldconfig. Yet I have the same problem. Can someone please help?

Boost is primarily a collection of header files. Here is the configure file.

Would it rather make sense to change the configure file? If so, can you help me with where to make the change?

---

### Post by Mirrorball on 2007-08-18
You can install boost from Synaptic, then I'm pretty sure configure is going to find it.

---

