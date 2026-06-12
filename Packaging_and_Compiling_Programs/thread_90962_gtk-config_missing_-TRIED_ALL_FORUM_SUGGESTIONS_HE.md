---
title: "gtk-config missing -**TRIED ALL FORUM SUGGESTIONS** HELP!!!!!!"
date: 2005-11-16
forum: Packaging and Compiling Programs
---

### Post by jason_65c02 on 2005-11-16
Starting a new thread - as my original post was really about another problem...
LOVE UBUNTU.  Can't compile.  Usual suggestions followed.  I have dev-essentials installed.  my .c script is simple - there is no CONFIGURE, just a MAKEFILE.  And it did compile on Mandrake years ago.

the MAKE stage gives the usual "GTK-CONFIG NOT FOUND" error, but ALL posts i read specify installing dev-essentials or refer to 'configure' dependencies (don't apply here for me i believe).  

LOCATE GTK-CONFIG shows *nothing*.  
LOCATE GTK  shows lots of dirs - all 2.0 and above.

I Have EVERY lib installed (i think) and still can't find GTK-CONFIG!!!!!

PLEASE HELP!!!!!

Also - in my 3+ days of trying to compile a simple program, i may have made some booboo's.... one for sure:

adding GTK to PKG_CONFIG_PATH env var - but i now know it's wrong.  How do I remove my previous entry and what file do I locate to get the correct path?

Thanks!!

---

### Post by ow50 on 2005-11-16
Ubuntu packages tells me that gtk-config is in package libgtk1.2-dev. Do you have that installed?
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=gtk-config&searchmode=searchword&case=insensitive&version=breezy&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=gtk-config&searchmode=searchword&case=insensitive&version=breezy&arch=i386)

---

### Post by jason_65c02 on 2005-11-17
Thank You!! Every reply leads me somewhere different than replys to other persons threads with "similiar" problems.  So I don't think it's a duplicated effort you have given!

I could not find that simple fact out....

Thank you Thank you!!

---

