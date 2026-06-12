---
title: "howto: find and compile ranlib"
date: 2006-03-20
forum: Programming Talk
---

### Post by glug101 on 2006-03-20
Greetings!
    I am a linux user at heart who, for the time being, is using a mac.  I have several open source programs that I would like to compile to run on it that have worked in the past, but now I get problems.  I believe that Apple must have changed something when they released the latest developement packages because ranlib up and barfs on me when I try to compile something.  

    Through reading elsewhere, I have found the problem.  Apples ranlib is NOT gnu compatible.  I would like to compile the gnu version and install it, but I can't find it, so I assume that it's packaged with some other source code.  

    Does anybody know where I can download source code for ranlib?

---

### Post by hod139 on 2006-03-20
Looks like it is part of the binutils package.
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=ranlib&searchmode=searchfiles&case=insensitive&version=breezy&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=ranlib&searchmode=searchfiles&case=insensitive&version=breezy&arch=i386)

---

### Post by glug101 on 2006-03-20
[QUOTE=hod139]Looks like it is part of the binutils package.
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=ranlib&searchmode=searchfiles&case=insensitive&version=breezy&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=ranlib&searchmode=searchfiles&case=insensitive&version=breezy&arch=i386)[/QUOTE]
Crap!  I thought that was the case.  When I try to compile Binutils, I get a message telling me that ranlib was asked to use an unrecognized option....

Just a second, let me get the output:
```
ar cru libintl.a intl-compat.o bindtextdom.o dcgettext.o dgettext.o gettext.o finddomain.o loadmsgcat.o localealias.o textdomain.o l10nflist.o explodename.o
ranlib: unrecognized option `-q'
Try `ranlib --help' for more information.
ar: internal ranlib command failed
make[1]: *** [libintl.a] Error 1
make: *** [all-intl] Error 2
```

maybe './configure --disable-ranlib'?  Though I imagine that will just keep ranlib from being built instead of not looking for ranlib.

What kind of sick joke is it to require ranlib to compile ranlib?

---

### Post by hod139 on 2006-03-21
Can't you install the binutils package from the repositories, and after it has installed build your own custom version of ranlib?

---

### Post by glug101 on 2006-03-21
[QUOTE=hod139]Can't you install the binutils package from the repositories, and after it has installed build your own custom version of ranlib?[/QUOTE]
That would be great, except for the fact that I'm running on mac OS right now;)  I was hoping against hope that there was a different different package that I could download and compile.  The end result that I'm looking for is a working jpilot, or similar, that will allow me to sync my handspring organizer.

Sorry if my last post sounded like complaining.  Sometimes compiling programs drives me nutz because of all the dependencies.  However, the cool part of compiling programs is the fact that many packages are used again and again, and only require a single download:)

Thanks for the help though.  I might play with fink a bit more, or I might just wait till next month when I can finally build my prototype Ubuntu box that I plan on putting up for sale (with a happy Dapper install and good PRINTED docs;) )

---

