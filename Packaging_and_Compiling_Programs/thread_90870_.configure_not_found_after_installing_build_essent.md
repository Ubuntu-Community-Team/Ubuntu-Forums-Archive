---
title: "./configure not found after installing build essentials!"
date: 2005-11-16
forum: Packaging and Compiling Programs
---

### Post by jason_65c02 on 2005-11-16
Noob here - LOVE breezy!!!  

Can't compile one of my simple progs from source though... ](*,) 

I've installed "build-essentials", which looks like it installed make. (from adept)
but ./configure gives "no such file or dir"

I know it's something simple... :D 

Thanks a million for relief from MICROSOFT HELL! =D>

---

### Post by reedlaw on 2005-11-16
What directory are you in when you run ./configure?
I assume you have done a tar -xvzf program.tgz and then cd program/ before you did ./configure?

---

### Post by jason_65c02 on 2005-11-16
I'm in the source dir for the program i'm trying to compile. (under my home/jason/ dir...)

---

### Post by lcg on 2005-11-16
[QUOTE=jason_65c02]I'm in the source dir for the program i'm trying to compile. (under my home/jason/ dir...)[/QUOTE]
Maybe I'm asking the obvious here, but is there a configure script in that directory? And do you have execute permissions for that script?

A configure script comes with the software you are trying to build, not with the build-essentials.

HTH,
Lars

---

### Post by jason_65c02 on 2005-11-16
Thanks for asking "the obvious" - it's welcome.  Although the answer is yes AFAIK - this is source I compiled successfully about 6 years ago on mandrake - God only knows how - and promptly abandoned due to business reasons.  Now I'm reviving it.  

I have the MAKEFILE and .C and .H files, and do (I think) have "execute" permissions for the .C script (do you really "execute" .C script???)  the makefile/.c/.h are in a subdir of my home dir - so whatever permissions are set by defult install of Breezy...

UPDATE:
MY BAD: I DON'T HAVE A ./CONFIGURE (I forgot CONFIGURE was provided by some source progs - _but not the one I'm trying to compile_.  The "INSTALL" doc that came with the source says:

$CD <src dir> 
$MAKE
$SU MAKE INSTALL  (i prob should do  $SUDO MAKE INSTALL -- is this ok?)

and that's it.

******HOWEVER:*******
**I still have a MAKE problem:**  
I get lots of "GTK-CONFIG NOT FOUND" errors.  

I've already added GTK-CONFIG to the path with
$PKG_CONFIG_PATH=/usr/lib/pkgconfig
$export PKG_CONFIG_PATH

(whats the diff between 'pkgconfig' and 'pkg-config'? I found both with 'locate')

Thanks!!!! I'm getting there..... ;-)

---

### Post by JohnnyMast on 2005-12-06
> A configure script comes with the software you are trying to build, not with the build-essentials.

Well not always, sometimes it happends that a configure scripts does not exst. I can take mailutils (By GNU) for example.

After extracting it from there cvs respo* there is only Makefile.cvs, if this ever happens to you take the following steps 

$ make -f Makefile.cvs

An other scenario is if there is no Makefile.cvs but configure.ac (or configure.in) run there 2 commands.

 $ autoconf
 $ automake

If you dont have these commands on your system apt-get install the following packages 

automake1.8
autoconf1.4

These are commonly the most used development tools.

cheers,

Johnny Mast

---

### Post by lcg on 2005-12-16
[QUOTE=lcg]Maybe I'm asking the obvious here, but is there a configure script in that directory? And do you have execute permissions for that script?

A configure script comes with the software you are trying to build, not with the build-essentials.[/QUOTE]
[QUOTE=JohnnyMast]Well not always, sometimes it happends that a configure scripts does not exst. I can take mailutils (By GNU) for example.[/QUOTE]
You really should read the whole thread or at least my posting. ;)

I am well aware of the fact that some programs come without a configure script.
The original poster asked how to compile a program which complained when he tried to './configure'. I then told him to check if there even was a configure script for that software. Because configure scripts come with the software (if the software has one), not with the build-essentials package.

Lars

---

### Post by voltage on 2007-02-11
> **JohnnyMast said:**
> Well not always, sometimes it happends that a configure scripts does not exst. I can take mailutils (By GNU) for example.

After extracting it from there cvs respo* there is only Makefile.cvs, if this ever happens to you take the following steps 

$ make -f Makefile.cvs

An other scenario is if there is no Makefile.cvs but configure.ac (or configure.in) run there 2 commands.

 $ autoconf
 $ automake

If you dont have these commands on your system apt-get install the following packages 

automake1.8
autoconf1.4

These are commonly the most used development tools.

cheers,

Johnny Mast

Hi,

I also facing the missing of configure script too... then after I read though the instruction above, I try to locate the Makefile.cvs and configure.ac (or configure.in) also not in list. Due to this, do you have any ideal to tell me ? If yes ... Please include those step to show me .. sorry to give you troble .. because i were really very fresh from Ubuntu .. 

Thanks ..

---

### Post by hod139 on 2007-02-14
Is there a README file or an INSTALL file?

---

