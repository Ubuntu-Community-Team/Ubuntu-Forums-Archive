---
title: "gtkmm library problems..."
date: 2011-08-18
forum: Programming Talk
---

### Post by MG&amp;TL on 2011-08-18
Having used a gtkmm library to develop a test program in C++, when I distributed the test program, most people ran it fine (I would expect this, I thought all the GNOME programs were GTK-based, hence we should have the libraries)

However one gets an error:

```
./Test: error while loading shared libraries: libgtkmm-2.4.so.1: cannot open shared object file: No such file or directory
```

a) do you know what's causing this?
b) will gtkmm applications be runnable on a default ubuntu install, or do I need to put a dependency in the .deb?

Thanks (lots!) for any help given.

---

### Post by PaulM1985 on 2011-08-18
The issue is that the library doesn't exist on their computer.

Maybe that person has an older version of gtkmm installed on their computer.  Updating their libraries should solve the problem.  Adding a dependency to the deb file is probably the best way round this  (it saves having to tell people to update their libs).  I would have thought that only people running fairly old versions of Ubuntu would have this issue.

Paul

---

### Post by MG&amp;TL on 2011-08-18
OK, thanks, so:

```
sudo apt-get update && sudo apt-get upgrade
```

should work? (Until I put the depndency in)

Thanks for reply! I thought it was an obscure question.

---

### Post by Zugzwang on 2011-08-18
If you just copy the executable to another computer, I suggest static linkage. Typically, this can be done by just adding "-static" to the gcc/g++ linking command in front of the list of libraries you link against (@everybody: please correct me if I'm wrong here). This will make your executable much larger, but on the target PC, the user will not have to install any library.

---

### Post by MG&amp;TL on 2011-08-18
Great! However, if I'm making a .deb. package, would I be right in thinking that the 'approved' method would be a dependency?

---

### Post by MadCow108 on 2011-08-18
> **Zugzwang said:**
> If you just copy the executable to another computer, I suggest static linkage. Typically, this can be done by just adding "-static" to the gcc/g++ linking command in front of the list of libraries you link against (@everybody: please correct me if I'm wrong here). This will make your executable much larger, but on the target PC, the user will not have to install any library.

-static will make the whole thing static, including static linking of libc, this may be overkill.
If you just want to link one single library statically, put the static version (with .a suffix usually available in -dev packages) into the compilation commandline directly instead of using -lname
```
#static link libstatic, but dynamic link of libm + other stuff
g++ myobj.o /usr/lib/libstatic.a -lm
```

> Great! However, if I'm making a .deb. package, would I be right in thinking that the 'approved' method would be a dependency?

yes, dh_shlibdeps executed by debian/rules in a package will automatically figure out which libraries you need and add them to the substitution variable shlibs:Depends, be sure to add that to the Depends: line of your control file
but when installing a package on a different system, make sure the libraries are also available in api/abi compatible form

---

### Post by MG&amp;TL on 2011-08-18
It's debian-linux specific. Bit out of my depth here. Thanks for all the help though. So if I put the 'shlibs: Depends ' line in Depends: in my control file, It'll work it out for me? That sounds good...:D

---

### Post by Paddy Landau on 2011-08-18
Hi, I'm the "one" who gets the error that TL mentioned in post #1.

I always keep my computer fully up-to-date (apt-get update and apt-get upgrade), so it must be something else.

TL uses 32-bit Lucid, whereas I use 64-bit Lucid; could that cause the problem?

---

### Post by PaulM1985 on 2011-08-18
Hmm, it could be that it is built in 32-bit and as a result is looking for a 32 bit version of libgtkmm.  You will probably have a 64 bit version of libgtkmm installed.

Paul

---

### Post by Paddy Landau on 2011-08-18
> **PaulM1985 said:**
> Hmm, it could be that it is built in 32-bit and as a result is looking for a 32 bit version of libgtkmm.  You will probably have a 64 bit version of libgtkmm installed.
If that's the case, what can TL do about it when compiling his code? Should I take the source code and compile it myself? (I would need instructions, though, as I've never done that before.)

---

### Post by MG&amp;TL on 2011-08-18
I don't have a 64-bit linux machine. I'm happy to give it to someone else who does.

---

### Post by Paddy Landau on 2011-08-18
> **MG&TL said:**
> I don't have a 64-bit linux machine. I'm happy to give it to someone else who does.
(Paddy raises his hand... ):P)

I'm happy to oblige, but I'll need instructions for compiling the code.

Paddy

---

### Post by MG&amp;TL on 2011-08-18
Sure...I was kinda hoping you'd say that...I'll give instructions on the old thread. If you want to PM your email address, I'll email a tarball. Didn't want to put pressure on. Compiling someone else's code is really quite easy.

Since there's no GUI as yet, I suggest that I just email you the source every time we have a new major version, that way we can ensure 64-bit compatibility. :)

Thanks for volunteering!

---

### Post by Paddy Landau on 2011-08-18
> **MG&TL said:**
> Thanks for volunteering!
No problem. It's good to know that I can contribute.

I've PM'd you.

---

### Post by MG&amp;TL on 2011-08-18
Everyone can contribute, even if only ideas. Best bit of Ubuntu/opensource in general, IMO. Email sent. Instructions in old thread. :)

---

