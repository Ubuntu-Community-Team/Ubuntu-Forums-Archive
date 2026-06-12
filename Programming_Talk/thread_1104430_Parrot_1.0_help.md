---
title: "Parrot 1.0 help"
date: 2009-03-23
forum: Programming Talk
---

### Post by coolkid5 on 2009-03-23
I've been trying out parrot, and everything was fine while I was using 0.9.0, but 1.0.0 was just released so I downloaded it, configured, compiled, "make test"ed etc.  Also, in 1.0.0 it's now possible to "make install" (in older versions this would mess things up), so I did that too.  

But now I'm running into a stumbling block because I was previously using [http://www.parrotblog.org/2008/03/targeting-parrot-vm.html](http://www.parrotblog.org/2008/03/targeting-parrot-vm.html) which is a tutorial on making a parrot compiler.  However, I'm confused because now parrot is installed in /usr/local, but all of parrot's language development tools are in the original folder on my desktop where I compiled/tested/"make install"ed Parrot from.  

The tutorial tells me to run "perl tools/dev/mk_language_shell.pl Squaak languages/squaak" in parrot's root directory in order to create the groundwork for the soon-to-be-written compiler.  But I don't know which one is "parrot's root directory" now that Parrot is actually installed in /usr/local.

Basically the organization of Parrot is confusing me.  Where should I be running things and creating my compiler's folder?  Help would be much appreciated.

---

### Post by jordilin on 2009-03-23
> **coolkid5 said:**
> I've been trying out parrot, and everything was fine while I was using 0.9.0, but 1.0.0 was just released so I downloaded it, configured, compiled, "make test"ed etc.  Also, in 1.0.0 it's now possible to "make install" (in older versions this would mess things up), so I did that too.  

But now I'm running into a stumbling block because I was previously using [http://www.parrotblog.org/2008/03/targeting-parrot-vm.html](http://www.parrotblog.org/2008/03/targeting-parrot-vm.html) which is a tutorial on making a parrot compiler.  However, I'm confused because now parrot is installed in /usr/local, but all of parrot's language development tools are in the original folder on my desktop where I compiled/tested/"make install"ed Parrot from.  

The tutorial tells me to run "perl tools/dev/mk_language_shell.pl Squaak languages/squaak" in parrot's root directory in order to create the groundwork for the soon-to-be-written compiler.  But I don't know which one is "parrot's root directory" now that Parrot is actually installed in /usr/local.

Basically the organization of Parrot is confusing me.  Where should I be running things and creating my compiler's folder?  Help would be much appreciated.

did you run configure with --prefix to install in a separate folder? In any case I guess you can do make clean or make uninstall and try again.

---

### Post by coolkid5 on 2009-03-23
I don't really mind what folder it is installed in.  It's just that I don't know where I my compiler's folder (the compiler that I am making) should be...

---

### Post by slavik on 2009-03-23
if the parrot binary is in /usr/bin, then /usr is the parrot root directory :)

---

### Post by coolkid5 on 2009-03-24
> **slavik said:**
> if the parrot binary is in /usr/bin, then /usr is the parrot root directory :)

Yes, I figured that.  However, the parrot binary is in /usr/local, but the development tools for parrot were not placed in /usr/local.  As I said, the tutorial says run "perl tools/dev/mk_language_shell.pl Squaak languages/squaak" in parrot's root directory, but the perl script "mk_language_shell.pl" is only in the original "parrot-1.0.0" folder on my desktop that I compiled and installed from.  "make install" did not put any of these helper perl scripts in /usr/local so running "perl tools/dev/mk_language_shell.pl Squaak languages/squaak" from /usr/local does not work.  

So I'm a bit confused.  I'm wondering if anyone (hopefully someone who has used parrot) can tell me how things are supposed to be done.

---

### Post by coolkid5 on 2009-03-29
I just found out there is a "make install-dev" which installs some of the perl scripts.  I had to actually look in the makefile's source to find this, its not in the readme at all.

---

