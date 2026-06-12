---
title: "Net-DBus-0.33.4 Install library, create deb"
date: 2006-11-16
forum: Packaging and Compiling Programs
---

### Post by finalbeta on 2006-11-16
I need to install the new Net-DBus-0.33.4 because the one in Edgy has some bugs. 

I guess I need to create a packet from the sources. I'm using dh-make-perl. But that gives me the following :

> finalbeta@finalbeta-desktop:~/Desktop/Net-DBus-0.33.4$ dh-make-perl 
cat: /etc/mailname: No such file or directory
Found: Net-DBus 0.33.4 (libnet-dbus-perl arch=any)
Argument "DBus" isn't numeric in subtraction (-) at /home/finalbeta/Desktop/Net-DBus-0.33.4/Makefile.PL line 20.
Argument "Net" isn't numeric in subtraction (-) at /home/finalbeta/Desktop/Net-DBus-0.33.4/Makefile.PL line 20.

Package does not provide a long description -  Please fill it in manually.
Using maintainer: finalbeta <finalbeta@>
Found changelog: CHANGES
Found docs: README
Using rules: /usr/share/dh-make-perl/rules.MakeMaker.xs
Done

This is line 20: 'NAME' => 'Net::DBus',


Not a clue on how to fix this.
It creates a /debian directory, but not a .deb file.

---

### Post by Hezekiah on 2006-11-16
I have never tried to use dh-make-perl, but according to the man page, just running 'dh-make-perl' will only do the setup for you (debian/ dir and whatnot), it won't actually build the package.

To do that you can try:
```
fakeroot dpkg-buildpackage
```
or (according to the documentation)
```
dh-make-perl --build
```

There are several other options listed in the man page for dh-make-perl, but I don't have any experience with the package so I'm not sure what to suggest :-)

Good luck!

---

### Post by finalbeta on 2006-11-16
thanks allot. That was the answer.
i'm kind off ashamed now. :)

---

### Post by Hezekiah on 2006-11-16
Nah, no need to be ashamed :-)  These things are easy to miss.

I'm glad it worked though!  I'll have to look in to dh-make-perl more though - I do a lot of work with Perl and it looks really useful.  So thank you for the pointer.

---

