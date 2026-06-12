---
title: "C Shared lib compatibility across OS versions"
date: 2007-08-15
forum: Programming Talk
---

### Post by bluedalmatian on 2007-08-15
Could you please explain how the differences in versions of glibc & libstdc++ found on different verisons of linux affect building a binary which will run on older linuxes as well as the latest releases.

i've built a simple binary on Ubuntu 7 but but when I try and run it on an older system I got the following:

error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory


There was a file /usr/lib/libstdc++.so.5
so I made a symlink from /usr/lib/libstdc++.so.6 to that

Im now getting
 /lib/tls/libc.so.6: version `GLIBC_2.4' not found (required by ./random)
./random: /usr/lib/libstdc++.so.6: version `CXXABI_1.3' not found (required by ./random)
./random: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4' not found (required by ./random)


I really have no understand of whats going on here. How can I ensure when I compile something that it will run on older systems?

As I say its only using the standard C & C++ libraries, so I thought it would be pretty universal?

Thanks
Andrew

---

### Post by noof on 2007-08-15
You have to recompile it. It might even compile on windows as well if you're only using standard functions.

---

### Post by bluedalmatian on 2007-08-15
It shouldnt need re-compiling on every machine.

---

### Post by noof on 2007-08-15
It doesn't if you have the same libraries as the one you linked to. That is v6 of the stdlib. The other computer only had 5. If you install v6 on it it'll work.

---

### Post by Ramses de Norre on 2007-08-15
> **bluedalmatian said:**
> It shouldnt need re-compiling on every machine.

If the ABI (application binary interface) of stdlib changed from version 5 to version 6 (and it mostly will), the binary instructions used to interface with stdlib-5 libs wont be the same as those used to interface with stdlib-6 libs. So an app compiled against stdlib-6 wont produce the same binary as one compiled against stdlib-5 and thus your compiled code wont work on both machines.
Your source is version-independent, but a recompile will be necessary.

---

### Post by -Rick- on 2007-08-15
The libc library (on Linux) is fairly solid, however libstdc++ has changed a few times in the last years. For now it's best to support both v5 and v6. To do this compile your binary either on both a v5 and a v6 system or install 2 compiler versions (gcc 3.2 and 3.3 have v5, gcc 3.4 and later have v6).

---

### Post by bluedalmatian on 2007-08-17
Ah right. Thanks Rick & Ramses.  

Is using an older version of gcc the only way to make it use an older verision of the library, there's no way I can force it use an older version with a command line option or something?

---

### Post by -Rick- on 2007-08-17
OK I stuffed a bit and came to a working solution, though better double check it if it really works :)

I did the following:

[LIST=1]
[*]Create an 'include' directory and copy all the C++ headers from the older gcc to it. Since I have 2 versions installed I just copied the directory '/usr/include/c++/3.3.6' to 'include/'.
[*]Create a 'lib' directory, and put a symlink called 'libstdc++.so' which links to '/usr/libstdc++.so.5.X.X' (where X.X are version numbers, in my case it was called 'libstdc++.so.5.0.7')
[*]Compile the program using the -L switch for the 'lib/' directory and the -B switch for the 'include/' directory.
[/LIST]

---

### Post by bluedalmatian on 2007-08-20
What about backwards compatability. If I compile for v5, will it work on a machine with 6 or later?

I also tried forcing it link statically, but then moving to a different machine resulted in a message about the kernel being too old (its 2.4)

Is there a way round that?

Thanks

Andrew

---

### Post by -Rick- on 2007-08-21
> **bluedalmatian said:**
> What about backwards compatability. If I compile for v5, will it work on a machine with 6 or later?

I also tried forcing it link statically, but then moving to a different machine resulted in a message about the kernel being too old (its 2.4)

Is there a way round that?

Thanks

Andrew

If you compile with v5, it will only work with systems which have v5. Though many distros provice 'compat' libraries (different versions), it's best to not rely on that. Linking libstdc++ staticly is not recommended because a few runtime things won't work (I think exceptions accross libraries for example). Besides it can make your binary kinda big.

So really, the best thing is to compile 2 binaries and provide a simple script using 'ldd' or similar which launches the right binary. If you're worried about the size of an additional binary, you could use something like 'rdelta' to make binary patches and apply them when the software is installed (this is what I basicly do for Nixstaller, so if you need any examples ...).

---

### Post by bluedalmatian on 2007-08-25
> (this is what I basicly do for Nixstaller, so if you need any examples 

Thanks Rick, you might regret that ;)

If I was to compile say for v6 and then include the .so file in the same directory as my binary that should work too shouldnt it?

Only problem is I can set the lib path as an envirnment variable by doing echo LD_LIBRAY_PATH= or whatever it is (I cant remeber the exact syntax off hand) but what I'm actually writing is a CGI program thats going to be launched by the web server rather than manually by a user, so how can I set the path in that situation?

Thanks

---

### Post by -Rick- on 2007-08-26
If you want to alter the library search path, it's best to use the rpath linker option. After a bit of googling I found the following forum post which shows a nice trick with it: [http://www.gamedev.net/community/forums/topic.asp?topic_id=456054&whichpage=2&#922155;](http://www.gamedev.net/community/forums/topic.asp?topic_id=456054&whichpage=2&#922155;).

---

