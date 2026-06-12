---
title: "Need help publishing first package."
date: 2011-04-10
forum: Packaging and Compiling Programs
---

### Post by shaneomack91 on 2011-04-10
Hello All,

This is my first time attempting to make a Ubuntu package publicly available, and I need some help in doing so.

First of all, some background:

I have developed a helper library for a new resource file format I have created, named ORC (Open Resource Container). It is designed for speed and simplicity. It creates files that consist of a 32-byte header (itself consisting of a magic number, application-specific magic number, reserved field, attribute count, data section offset/length, and a checksum), an attribute/metadata section supporting numberic, textual and binary attributes, and a data section.

Examples of ways this format could be used include audio, images, configuration files, game saves, and documents.

Although I have developed the format and library for my own project, I realised the potential for others to use it and would like to release it, open-source and fully documented, under the GPL.

The library using nothing more than the standard C library, so it  has no dependencies and can be compiled and used on any platform with a file system and C compiler. I have confirmed that it works on 32 and 64-bit Ubuntu, and 32-bit Windows - And that the code is 64-bit aware, using "long" instead of "int" where possible, and using a 64-bit data length.

Now, the things I need help with:

1. A good package name, that won't interfere with an existing package in any popular repository. I can't simply name it "liborc" and "liborc-dev", because the package for "Optimized Inner Loops Runtime Compiler" already exists with those names.

2. Getting the package into a repository, or creating a PPA. Can someone tell me what the best thing to do with it is, and how to do so?

3. Any suggestions, anybody interested in using my library for their own project?

Regards,
Shane Curless

---

### Post by SevenMachines on 2011-04-12
> **shaneomack91 said:**
> 
1. A good package name, that won't interfere with an existing package in any popular repository. I can't simply name it "liborc" and "liborc-dev", because the package for "Optimized Inner Loops Runtime Compiler" already exists with those names. 1. No idea, libopenrc? up to you really

> 2. Getting the package into a repository, or creating a PPA. Can someone tell me what the best thing to do with it is, and how to do so?2. I'd always recommend firstly making a ppa and then trying to get it  approved into a repository. the ppa means that people can use your stuff  while its waiting for approval and also means you can tidy up the  packaging before submission too. 
[https://help.launchpad.net/Packaging/PPA/Uploading](https://help.launchpad.net/Packaging/PPA/Uploading)

To get a package into ubuntu, use the REVU process
[https://wiki.ubuntu.com/MOTU/Packages/REVU](https://wiki.ubuntu.com/MOTU/Packages/REVU)

For debian, which ubuntu will automatically get your package from if included :smile: see debian mentoring
[http://mentors.debian.net/cgi-bin/welcome](http://mentors.debian.net/cgi-bin/welcome)

> 3. Any suggestions, anybody interested in using my library for their own project?3. 'Build it and they will come' :smile: this is why a ppa first is generally good, people can see it and easily try it out

---

### Post by shaneomack91 on 2011-04-12
> **SevenMachines said:**
> 1. No idea, libopenrc? up to you really

Of course, why didn't I think of that before :) libopenrc it is - No existing package with that name in the Ubuntu repos, and Google thinks it's a typo. Perfect.

And thanks for the tip about Debian mentoring, that sounds like the perfect way to get the package into more than just Ubuntu, after all it is a completely platform-independant library that I will also go to the trouble of compiling and releasing for unenlightened Windows users ;)

---

