---
title: "Linking against libs in non-standard libdir"
date: 2012-12-14
forum: Packaging and Compiling Programs
---

### Post by HansMeiser2 on 2012-12-14
Hello,
 
have a problem here.
I create a private package for me wich ist creating some libs with same name as some other libs installed in /usr/lib/.
to avoid conflicts my deb is designed to install my binaries and libs in some subdir:
/usr/bin/mypackage/executable
/usr/lib/mypackage/mylib.so.
compiling and packaging/installing is working.
 
My Problem ist that the binaries always look for mylib.so in /usr/lib/ and not in /usr/lib/mypackage/
i tried a lot of things in my rules files LDFLAGS/LD_LIBRARY_PATH etc. but no one works.
 
how to achive that /usr/bin/mypackage/executable  always looks at first in my /usr/lib/mypackage/ folder and not in /usr/lib/ ?
 
Thanks,
Hans

---

### Post by bmatthewshea on 2012-12-14
Why don't you create a static build with any libs needed/used compiled in a standalone binary? This would seem to be the easiest method to avoid using installed or shared libs. But this begs the question: if the libs needed are already in shared libs why are you trying to avoid dependencies on them? Why not just use them?

Though I have limited experience in linking directly to 'special' libs it seems you should try RPATH/RUNPATH - read:

[http://wiki.debian.org/RpathIssue](http://wiki.debian.org/RpathIssue)
and maybe:
[http://blog.tremily.us/posts/rpath/](http://blog.tremily.us/posts/rpath/)
and
[http://www.akkadia.org/drepper/dsohowto.pdf](http://www.akkadia.org/drepper/dsohowto.pdf) (Page 40)

Also, if you absolutely need to link like you do, why not just install the given libs with a different name (in package/sub folder) if they are getting found first in /usr/lib/?


> **HansMeiser2 said:**
> Hello,
 
have a problem here.
I create a private package for me wich ist creating some libs with same name as some other libs installed in /usr/lib/.
to avoid conflicts my deb is designed to install my binaries and libs in some subdir:
/usr/bin/mypackage/executable
/usr/lib/mypackage/mylib.so.
compiling and packaging/installing is working.
 
My Problem ist that the binaries always look for mylib.so in /usr/lib/ and not in /usr/lib/mypackage/
i tried a lot of things in my rules files LDFLAGS/LD_LIBRARY_PATH etc. but no one works.
 
how to achive that /usr/bin/mypackage/executable  always looks at first in my /usr/lib/mypackage/ folder and not in /usr/lib/ ?
 
Thanks,
Hans

---

### Post by HansMeiser2 on 2012-12-15
Hello,
 
>> why are you trying to avoid dependencies on them? Why not just use them?
 
iam compiling a different Version of ImageMagick. i would use them, but /usr/bin/mypackage/executable -version showed wrong version while wrong libs are used. i had to make sure that really my own libs are used.
 
Thanks, for your links. i tried a lot in my rules file but result was unchanged. i did not really understood how to set this in my deb rules file.
currently i did some kind of trick with patchelf
 
[http://nixos.org/patchelf.html](http://nixos.org/patchelf.html)
 
i changed the rulesfile and added some commands
after compiling and before packaging i run patchelf to fix my binaries:
 
patchelf --set-rpath /usr/lib/mypackage/ debian/mypackage/usr/bin/mypackage/executable
 
this is working, my installed bins show all correct liblinks and are working. i know, this is dirty but dont find another way.
do you think this works or produces other problems?
 
Thanks,
Hans

---

