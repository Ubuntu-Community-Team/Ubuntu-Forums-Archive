---
title: "Where to put built development binaries"
date: 2011-08-15
forum: Programming Talk
---

### Post by Xander314 on 2011-08-15
I'm building SFML 2.0 from the source on GitHub. I put the SFML files in /usr/lib/sfml2/. Once the binaries have been build, they are in /usr/lib/sfml2/lib/. My question is: should I move them all to /usr/lib/? If not, what should I do with them? Where must I put the shared libraries so that programs can find them?

Do I put static .a files in /usr/lib as well?

Thanks in advance,
Xander

---

### Post by Bachstelze on 2011-08-15
In general, stuff you have installed manually (i.e. not through the package manager) goes into /usr/local, not /usr. So you should put your libraries (both static and dynamic) into /usr/local/lib. (For static libraries, you can put the mretty much anywhere, but then you would have to specify the path with -L whenever you compile something that uses them.) For executables, /usr/local/bin is in your PATH so it's a good idea to put them there.

---

### Post by Xander314 on 2011-08-15
Okay, thanks. Final thing: seeing as the lib/ directories are for library files, is it stupid of me to put all the downloaded SFML files (source, headers, CMake files etc.) in lib/sfml2? Is there somewhere else I should put the actual SFML directory containing those?

---

### Post by Bachstelze on 2011-08-15
What do you mean by "the SFML files"? If you mean the source files you compiled the library/executables from, yes, there's zero point in having them in a system area (i.e. outside your home directory). Generally you:

1. Download the source somewhere in your home directory;
2. Compile them in your home directory *with your user account*, no root or sudo!
3. Install them (either with make install or by manually copying the files) as root into /usr/local.

Golden rule: never use root/sudo when you do not absolutely need it. In this case, you don't need it in order to compile, so you don't use it.

---

### Post by Xander314 on 2011-08-15
Yes, I did mean the source files, header files etc.

I've previously made tutorials for building SFML on Windows, and I wanted to provide one for Ubuntu too. However, I'm a complete Unix n00b so I had a load of issues to clear up. You've helped with at least three, including one I didn't know existed :)

Thanks so much for you time,
Xander

EDIT: I'm new to this forum as well. How do I mark this as solved? I saw something about a SOLVED prefix, but I only found that on the create thread page.

---

