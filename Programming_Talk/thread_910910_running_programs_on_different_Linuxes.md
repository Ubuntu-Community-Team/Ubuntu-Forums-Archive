---
title: "running programs on different Linuxes"
date: 2008-09-05
forum: Programming Talk
---

### Post by techmarks on 2008-09-05
If I write a programme on Xubuntu will it then run on another Ubuntu?  how about another distro? like let's say a Fedora or Suse etc..
Do they have to be compiled for each distro?

Thanks for any info.

---

### Post by ghostdog74 on 2008-09-05
what language are you using to write your programme

---

### Post by techmarks on 2008-09-05
The GCC compiler for C++

---

### Post by ghostdog74 on 2008-09-05
yes, it should be able to run on different linuxes...

---

### Post by jespdj on 2008-09-05
The different Linux distributions don't differ that much. They all use the same underlying operating system (Linux) and there's only a handful of desktop environments (GNOME, KDE, etc.). Programs written for one desktop environment also run on another desktop environment (the only thing is that they will have a slightly different look and feel).

You do not have to recompile software to run on different Linux distributions.

---

### Post by techmarks on 2008-09-05
So I should be able to give someone a binary and it should run.

Most people don't like to fiddle with compiling from source and it's always error prone.

Thanks, that's what I was hoping to learn.

---

### Post by amo-ej1 on 2008-09-05
Oh it isn't  as simple as that I think, it depends on how complex your application is. Don't expect that the binary you compiled today will work on a 3 year old RHEL.  If you make use of certain other (dynamic) libraries they might have changed the API as well.  When you compile it for x86 expect complaints from 64 bit users, from PPC users, etc etc. Also what if someone wants to run it on a FreeBSD or Solaris box ? 

To solve the library issue, most problem will be solved if you compile it statically (meaning non depending on .so's).

It's nice to provide a binary, it will work for a large percentage of users, but _do_ provide sourcecode for all those other people out there ;-)

---

### Post by pmasiar on 2008-09-05
It might or might not run on different distro: it depends on what you use from "environment": version of libraries and stuff.

---

### Post by rnodal on 2008-09-06
Here is a link about it. I hope it helps.
[Linking libstdc++ statically]("http://www.trilithium.com/johan/2005/06/static-libstdc/")


-r

---

### Post by techmarks on 2008-09-06
> **rnodal said:**
> Here is a link about it. I hope it helps.
[Linking libstdc++ statically]("http://www.trilithium.com/johan/2005/06/static-libstdc/")


-r

Thanks yes, that is an informative link.
What a mess!

I feared as much, I'd prefer doing things in C++, but really seems to create limitations, and C seems has less of these type of problems.

C++ just has better libraries,  and of course being able to use classes helps the organisation of the program and keeps it shorter.

C programs tend to get really long for some reason (maybe just mine!)

But back to the subject, it's really too bad.

I think this just holds Linux back, I mean now I understand why many programs don't make it into Linux.

I almost had a headache just reading about the issue.

:frown:

---

### Post by rnodal on 2008-09-06
It is not so much the language (even though it has something to do, one thing leads to another) but the [ABI]("http://en.wikipedia.org/wiki/Application_binary_interface")
Check this little discussion to see what I mean.
[http://kerneltrap.org/node/576]("http://kerneltrap.org/node/576") 

-r

---

### Post by mssever on 2008-09-07
I should also point out that things aren't nearly so difficult if you use a dynamic language such as Ruby or Python.

---

### Post by LaRoza on 2008-09-07
> **mssever said:**
> I should also point out that things aren't nearly so difficult if you use a dynamic language such as Ruby or Python.

Or release source for any language (assuming there exists a runtime or compiler for the various targets)

---

### Post by mssever on 2008-09-07
> **LaRoza said:**
> Or release source for any language (assuming there exists a runtime or compiler for the various targets)
Except that potentially involves compiling, which the OP wants to avoid.

---

### Post by amo-ej1 on 2008-09-07
And this really doesn't hold Linux back, try running DOS games under XP or Vista, or try running DirectX 3 games under an XP system with DirectX 9 installed ... I'm just saying that releasing binary only is a bad idea, if you release source people that really want to do exotic things are able to do so. Offcourse releasing a standard rpm or standard .deb or a binary for the default distributions is a good idea, but _do_ release source code too.

---

