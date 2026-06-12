---
title: "Linking the correct libstdc++"
date: 2007-04-26
forum: Programming Talk
---

### Post by zenkaon on 2007-04-26
Hello,

I have just moved to ubuntu. Everything about the os works fantastically, goodbye red hat  :) 

However, unless I can get my code to compile and link correctly then I'm in trouble. Now that I've figured out how to have both gcc-3.4 and gcc-4.1, I can carry on using gcc-3.4 for my main programme and gcc-4.1 for new stuff. Thanks to jespdj and wmcbrine for that one :) 

I am having a spot of bother linking everything together,  basically gcc is dynamically linking everything up with libstdc++.so.6 and I need it to be dynamically linking with libstdc++.so.5 so that 3rd party code works correctly.

I get a linking warning like this:
usr/bin/ld: warning: libstdc++.so.5, needed by /usr/lib/libCLHEP-2.0.3.1.so, may conflict with libstdc++.so.6

The libraries do conflict and my programme dies very quickly indeed. Not good.

I see that when linking, the flag -lstdc++ is passed, presumably this points to libstdc++.so.6

Can anybody tell me what I can put in my Makefile to convince gcc that -lstdc++ points to libstdc++.so.5 ??

Cheers
John

---

### Post by harun on 2007-04-26
This documentation gives you a few options you might be able to go with:

[http://www.linux.org/docs/ldp/howto/Program-Library-HOWTO/shared-libraries.html](http://www.linux.org/docs/ldp/howto/Program-Library-HOWTO/shared-libraries.html)

Do parts of the final product need version 6 and parts version 5?

---

### Post by zenkaon on 2007-04-27
Hello,

The documentation was useful, taught me a lot about linked libraries, but I still don't have a working progamme.

I need EVERYTHING to be linked with libstdc++.so.5. I can't have a trace of libstdc++.so.6 in the executable. 'ldd go.exe | grep libstdc++.so.6' must come up blank. This is because (a) My programme uses 3rd party (open source) software which hasn't been implemented with libstdc++.so.6 and (b) I have to be able to run this on a RHEL3 machine which hasn't got libstdc++.so.6

I was using RHEL4 and have only just (Tuesday night) moved to kubuntu. I am liking everything about kubuntu so far, it's a lot nicer to use than RHEL4, but I am taking a big productivity hit not being able to link my code correctly. If I don't have this working by the middle of next week then I'm going to have to go back to red hat :( 

In the linking process I see -lstdc++ which I think refers to libstdc++.so.6, does anybody know how to get this to refer to libstdc++.so.5 ????

---

### Post by hod139 on 2007-04-27
In your makefile, you should be able to set gcc-version to do the linking.  For example,
```

LD=gcc-3.4

```

And then the correct version of cstdlib should be linked (I think).

---

### Post by zenkaon on 2007-04-27
Success!! A big thank you goes out to Brian Dessent from the [email]gcc-help@gcc.gnu.org[/email] mailing list. He says:

You can't just pick and choose which version of the library is used.  It
is highly coupled to the version of gcc; in other words, the version of
gcc that you use will determine which version of libstdc++ your code
gets linked to, and nothing else.  They go hand in hand.

Generally when you are aiming for binary compatibility across multiple
systems/platforms, the only way to achieve this is to set the compile
environment to the oldest combination of libraries and compilers that
you want to support.  There is no way to go backwards, i.e. use a recent
gcc but link to an older library.  If you want to produce binaries that
still link against an older libstdc++ you'll have to install gcc 3.3 on
your system and use that.  The libstdc++.so.5 that ubuntu provides is
for compatibility for existing binaries that were compiled with gcc 3.3,
it is not possible to link against it for new programs compiled with gcc
3.4 or 4.x.

Brian
~~~~~~~~~~~~~~~~

So after removing a lot of programmes that I was linking to, I installed gcc/g++ 3.3 and re-built everything. An few hours later my code finally worked :) :) 

 I can breath a sigh of relief, forget using red hat (on my laptop at least - work is pretty ingrained) and start worrying about that new functionality I was planning. 

On a plus side I learnt about shared libraries in C++ and Linux, and maybe you did as well...

---

### Post by harun on 2007-04-27
Thanks for posting the status of your success. I was very interested in how this works as well.

---

