---
title: "sdljava problem"
date: 2011-05-20
forum: Programming Talk
---

### Post by Largaroth on 2011-05-20
Hi all,
I've been having a little trouble with getting sdljava to work for me (in Natty).

Basically, my mate and I have a little project going, and he decided to go for java with SDL. He has started coding and it works fine for him, but when he sent it all to me, I realised he is running Windows...

Therefore, I need to set the SDL bindings up for it to run on my machine, but I'm having a lot of trouble with that...

Has anybody else had trouble ? I tried just copying he folder over to my project and use it like that, but I haven't managed to get that working.

And so I tried compiling it no a native layer. The only problem is that the INSTALL file says to use a specific makefile that needs to be copied from a certain location.
And guess what ? There is no makefile there as far as I can tell.

Help ? =)

Larg

---

### Post by Petrolea on 2011-05-20
Java & SDL are both easy to port from OS to OS but by just copying files it is most likely it won't work. It's two completely different OSs!

If you want to compile it you will first have to install all required libraries (can't tell which, try compiling the code and it will list the headers it can't find).

It is not necessary to compile it with Makefile, your friend should send you the source code (it should also be in subdirectory src) and you can compile it easily in a command line or IDE like Eclipse (Makefile can be useful in some cases but if there isn't much code & files a normal way to compile it is ok).

---

### Post by Largaroth on 2011-05-20
Hi, I'm sorry, I wasn't quite clear enough.

I have the source code that my friend has written, and I have downloaded sdljava for Ubuntu.

The Makefile I was talking about is the one they reference in the INSTALL file that came with the sdljava archive.

Also, When I try to compile with javac (I don't with Eclipse) it only returns errors due to the SDL and the first one is this :

```
Jeu.java:3: package sdljava does not exist
```

---

### Post by Petrolea on 2011-05-21
> **Largaroth said:**
> Hi, I'm sorry, I wasn't quite clear enough.

I have the source code that my friend has written, and I have downloaded sdljava for Ubuntu.

The Makefile I was talking about is the one they reference in the INSTALL file that came with the sdljava archive.

Also, When I try to compile with javac (I don't with Eclipse) it only returns errors due to the SDL and the first one is this :

```
Jeu.java:3: package sdljava does not exist
```

Maybe you have to configure & then make install.

---

### Post by Largaroth on 2011-05-21
There is no configure file in the whole directory...

To be honest, itt all seems quite sketchy to me.. Here is part of the INSTALL file :

```
COMPILE FROM SOURCES (SOURCE RELEASE/CVS)
==================
On any platform compilation consists of two steps.
   1) compile the native interface layer
   2) compile the java source files

UNIX:
	Compile Native Layer
	--------------------------------------------------

	To compile the native interface layer copy the Makefile from
	etc/build/linux

		$ cp etc/build/linux/Makefile src/sdljava/native

	Type make and see if the build works.  If not you most likely
	will need to add an additional include path based on the error
	message received.
```

This is where I get the error (I know I haven't gotten very far have I ? ^^"). There is no such directory (etc/build) on my machine... Am I missing something here ?

---

### Post by Petrolea on 2011-05-22
> **Largaroth said:**
> There is no configure file in the whole directory...

To be honest, itt all seems quite sketchy to me.. Here is part of the INSTALL file :

```
COMPILE FROM SOURCES (SOURCE RELEASE/CVS)
==================
On any platform compilation consists of two steps.
   1) compile the native interface layer
   2) compile the java source files

UNIX:
	Compile Native Layer
	--------------------------------------------------

	To compile the native interface layer copy the Makefile from
	etc/build/linux

		$ cp etc/build/linux/Makefile src/sdljava/native

	Type make and see if the build works.  If not you most likely
	will need to add an additional include path based on the error
	message received.
```

This is where I get the error (I know I haven't gotten very far have I ? ^^"). There is no such directory (etc/build) on my machine... Am I missing something here ?

Can't really help you atm, I would try but am not at home. Maybe google can help or some other package.

---

### Post by SevenMachines on 2011-05-22
Hi there. looks like sdljava is 6 years old since any changes so i would recommend not to use it if possible. if you want to though..
```
$ cvs -d:pserver:anonymous@sdljava.cvs.sourceforge.net:/cvsroot/sdljava login
$ cvs -z3 -d:pserver:anonymous@sdljava.cvs.sourceforge.net:/cvsroot/sdljava co -P sdljava
```will get you the source and so the linux makefile ( or an ant build file too )
wont build here though. best to look into other more up-to-date and active projects i think

[EDIT] the source directories look odd too, seems a little messy to me (no offence to the developers :) ) another reason to look around for something else
maybe Lightweight Java Game Library (LWJGL)? [http://lwjgl.org/](http://lwjgl.org/)

---

### Post by Largaroth on 2011-05-22
Okay, thanks guys. I'm looking into lwjgl, but I'm having a little trouble with javac when compiling :/ I must be doing something wrong in the command line, like forgetting libraries or whatever.

Anyway, I think I'll look into an Ant tutorial instead.

[EDIT]I'm all set up, using Eclipse to build, it's easier =)

---

### Post by Petrolea on 2011-05-23
> **Largaroth said:**
> Okay, thanks guys. I'm looking into lwjgl, but I'm having a little trouble with javac when compiling :/ I must be doing something wrong in the command line, like forgetting libraries or whatever.

Anyway, I think I'll look into an Ant tutorial instead.

[EDIT]I'm all set up, using Eclipse to build, it's easier =)

Glad you solved the problem. And using Eclipse to program should make your life much easier :). You can mark this problem as [SOLVED] now.

---

### Post by Largaroth on 2011-05-23
Yes, Eclipse is very good, however, I am more used to emacs, which is also a very powerful tool

---

