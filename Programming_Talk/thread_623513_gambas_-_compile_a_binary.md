---
title: "gambas - compile a binary"
date: 2007-11-25
forum: Programming Talk
---

### Post by weblordpepe on 2007-11-25
Hello guys.

I'm using Gambas 1.9.49 (which calls itself Gambas 2??) anyway I'm trying to compile a binary so my program can run on any linux machine with GTK etc installed.

So far I can only compile binaries which require Gambas to be installed. This is no good since most end-users won't. Can anyone please let me know how I can compile a gambas executable / gambas project into a native linux binary?

---

### Post by drarem on 2007-12-02
Unfortunately, I think their website said it was an interpreter which means it requires Gambas..  it is somewhat sad as the application is nice.  There is hope though, maybe someone will add native compilation later.

For now, you can do this:

Project-->Make installation package-->

and select from the many distros, ubuntu, deb, fedora, open suse, etc.

and it should include the gambas interpreter in the installation package.

If I'm wrong,please someone slap me with a wet fish..

---

### Post by gambasfr on 2007-12-03
I slap you with a wet fish...

The interpreter is just linked in the package... so when your user install your program it will call the gambas runtime of his distribution.

You can compare gambas at python, perl, java, .net... all need an interpreter or a framework. And many, many all language now...
As the advantage of an interpreted language is to have the ability to be executed on each plateform where its interpreter exist.

Now, infortunally gambas is young and have only a linux interpreter.. VB have the same handicap in the windows world.

>>So far I can only compile binaries which require Gambas to be installed. This is no good since most end-users won't. Can anyone please let me know how I can compile a gambas executable / gambas project into a native linux binary?<<

 ???? and they never install python too. you have just to install gambas and libs...

as far as i know gambas interprter size is less than 300 ko, and libs...
40 MO for all the libs, 2 Mo for the gtk one... it's really not enouth comparate to a java or .net framework.

If you use the gambas packager, your end user system will only download the Gambas interpreter and the needed libs... generally max 10MO. But not the gambas tools such as IDE or Gambas Database manager...
So it will not change anything visually on the system.

Fabien Bodard

--
[http://www.gambasforge.net](http://www.gambasforge.net)

---

### Post by weblordpepe on 2007-12-05
:( so basically I should rig it so the interpreter installs with whatever software I distribute?

ie set gambas interpreter as a dependancies?

---

