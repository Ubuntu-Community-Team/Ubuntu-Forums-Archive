---
title: "HOWTO: Install GNU Emacs with antialiasing"
date: 2006-02-05
forum: Outdated Tutorials &amp; Tips
---

### Post by trevorv on 2006-02-05
Emacs is an amazing piece of software, but it's also hellishly ugly by default.

Here, I'll show you how to get it from CVS with antialiasing and GTK support, like this;

[IMG]http://www.activist-news.co.uk/misc/emacs_aa_screen.png[/IMG]

My apologies in advance; I'm not sure of the dependencies, other than CVS and TLA. Hopefully any error messages should be verbose enough for you to figure it out.

I've read I guide similar to this before, but I've lost the URL. Kudos to whoever wrote that one.

engla recommends using checkinstall as "It makes me feel much better about my system, knowing that it's easy to just throw something you compile-installed out again if you screwed up."

[LIST]
[*]First, we want to get it from CVS. To do so, run;

```
cvs -z3 -d:pserver:anonymous@cvs.savannah.gnu.org:/cvsroot/emacs co emacs
```

[*]Now, cd into emacs, and get the Xft branch of Emacs by running

```
cd emacs
cvs up -Pd -r XFT_JHD_BRANCH
```

[*]Next get the following emacs-snapshot-debian directory 

```
tla register-archive jerome@debian.org--2005 http://people.debian.org/~jerome/arch/jerome@debian.org--2005/

tla get -A jerome@debian.org--2005 emacs-snapshot-debian--main
```

[*]And then rename the directory "debian" and put it in emacs/src. You then have to edit out the build instructions for the -nox variant of Emacs in emacs/src/debian/rules. You can find the edited file [here]("http://www.activist-news.co.uk/misc/rules").

[*]And now you're good to go! From the emacs directory, run the following commands (make bootstrap takes a while, so go grab some lunch).

```
./configure --with-x-toolkit=gtk --with-xft=yes
make bootstrap
make
sudo make install
```

[*]There we are, that wasn't too bad! To set your font, add something like the following to ~/.Xresources (you may need to restart X before it takes effect).

```
Emacs*font: Monospace-7
```
[/LIST]

And finally, you might want to create a menu item for it. Happy hacking!

---

### Post by Wallakoala on 2006-02-05
I get the following error:
```
walla@ubuntu:~/emacs$ tla get -A jerome@debian.org--2005 emacs-snapshot-debian--main
archive not registered: jerome@debian.org--2005
  (see register-archive)
walla@ubuntu:~/emacs$

```

....I'm a noob at this stuff

---

### Post by trevorv on 2006-02-05
[QUOTE=Wallakoala]I get the following error:
```
walla@ubuntu:~/emacs$ tla get -A jerome@debian.org--2005 emacs-snapshot-debian--main
archive not registered: jerome@debian.org--2005
  (see register-archive)
walla@ubuntu:~/emacs$

```

[/QUOTE]

Argh, sorry, I put the wrong line in :-# 

I'll change that now.

---

### Post by Wallakoala on 2006-02-05
[QUOTE=trevorv]Argh, sorry, I put the wrong line in :-# 

I'll change that now.[/QUOTE]

Ok, it works now. I'm still waiting for make bootstrap to finish....:P

---

### Post by ow50 on 2006-02-05
Thanks for this. I've been waiting for the antialiasing before giving emacs a serious try.

[QUOTE=trevorv]My apologies in advance; I'm not sure of the dependencies, other than CVS and TLA.[/QUOTE]
Perhaps
```
sudo apt-get build-dep emacs
sudo apt-get install cvs tla
```
would take care of most issues that might come up.

---

### Post by Wallakoala on 2006-02-05
Wow...this is sick. Emacs looks nice! Thanks for this awesome how to!

---

### Post by ubuntumaneh on 2006-02-05
This how-to seems to be very nice. I didn't try it yet, so forgive my ignorance.
If I installed emacs from the repositories with apt-get, as usual. And then install some fonts in X, maybe using xft, for instance, or some other one, and add it to the .Xresource file, would it work? I do also "emacs -fn <somefont>", and seems to be nice. Im using now the font "terminus". I really don't know how better is your recipe.

---

### Post by trevorv on 2006-02-05
[QUOTE=ubuntumaneh]If I installed emacs from the repositories with apt-get, as usual. And then install some fonts in X, maybe using xft, for instance, or some other one, and add it to the .Xresource file, would it work? I do also "emacs -fn <somefont>", and seems to be nice. Im using now the font "terminus". I really don't know how better is your recipe.[/QUOTE]

I'm not 100% sure how Emacs is packaged in the repositories, but I'm almost certain this won't work. Emacs needs to compiled with xft support.

---

### Post by ubuntumaneh on 2006-02-05
I have looked around in the web, and happen to learn that what you've just said is correct. Emacs has to be compiled with xft support. I did't know that emacs was not able to support these fonts. I was so used to terminus, that I did't realized there was the possibility to use other fonts in my work. I have installed the cleartype here, but never thought of using it in emacs. So you just point us a very nice thing. I will try your how-to right now.
Hope to see this kind of stuff already in dapper.

---

### Post by engla on 2006-02-05
This is great, I though about this earlier today!

Building emacs was a breeze, and it seems to be faster now, too!

I removed all my emacs packages before installing, but I don't know if that's neccessary.

You should recommend 'checkinstall' to everyone. It makes me feel much better about my system, knowing that it's easy to just throw something you compile-istalled out again if you screwed up.

---

### Post by forbmj on 2006-02-05
[QUOTE=trevorv]Argh, sorry, I put the wrong line in :-# 

I'll change that now.[/QUOTE]

$tla get -A [email]jerome@debian.org[/email]--2005 emacs-snapshot-debian--main 

No such version (0)
  name: [email]jerome@debian.org[/email]--2005
  location: [http://people.debian.org/~jerome/arch/jerome@debian.org--2005/](http://people.debian.org/~jerome/arch/jerome@debian.org--2005/)
  package-version: emacs-snapshot-debian--main--0


any problem?

---

### Post by Wallakoala on 2006-02-05
[QUOTE=engla]This is great, I though about this earlier today!

Building emacs was a breeze, and it seems to be faster now, too!

I removed all my emacs packages before installing, but I don't know if that's neccessary.

You should recommend 'checkinstall' to everyone. It makes me feel much better about my system, knowing that it's easy to just throw something you compile-istalled out again if you screwed up.[/QUOTE]
I tried using checkinstall on this and it failed....I have no idea why.

---

### Post by trevorv on 2006-02-05
[QUOTE=engla]You should recommend 'checkinstall' to everyone.[/QUOTE]

I added the recommendation, cheers :)

---

### Post by trevorv on 2006-02-05
[QUOTE=forbmj]any problem?[/QUOTE]

Sorry, I'm not sure why you're getting that error. Are you sure you ran the first tla command?

If you still get the error, maybe someone else can help.

---

### Post by Tryke on 2006-02-05
So, I followed the tutorial to the letter, but I only get console emacs. How do I run it with the fancy GTK stuff? I can't find an "xemacs" binary anywhere.

---

### Post by engla on 2006-02-05
[QUOTE=Wallakoala]I tried using checkinstall on this and it failed....I have no idea why.[/QUOTE]
It will offer to display an error log. You should look at it, if it fails.

If you already have some kind of emacs package installed, it will say 'emacs [the package you built] conflicts with package emacsen-common [or any other emacs package you might have]'

So checkinstall is great to keep your system clean, but you have to clean out old stuff first, and it's far from perfect.

---

### Post by kaamos on 2006-02-06
[QUOTE=trevorv][*]There we are, that wasn't too bad! To set your font, add something like the following to ~/.Xresources (you may need to restart X before it takes effect).[/QUOTE]
No need to restart X. This should take care of it
```
xrdb -merge ~/.Xresources
```

---

### Post by VCSkier on 2006-02-06
i'm an ultra noob at linux.  i removed windows and installed ubuntu about a week ago, w/ no prior experience.  i've followed this guide sucessfully (as far as i can tell) till the last step, where i need to locate "~/.Xresources".  where is this supposed to be?  is it a file or a folder?  sorry if i've messed something up, or missed something simple.  thanks though for the guide.

---

### Post by LordBug on 2006-02-07
> add something like the following to ~/.Xresources
> where i need to locate "~/.Xresources"?

No offense, VCSkier, but I would highly recommend reading up on how Linux directory and file schemes work.

~ = your home directory. ('cd ~' will take you to it)
.Xresources = the file that needs edited.  the period (.) in front means it will normally be hidden from ls, though ls -a will make it show up.

---

### Post by VCSkier on 2006-02-07
[embarrassed]i was wondering why that period was there...  lol.  thanks.  [/embarrassed]

---

### Post by Lux Perpetua on 2006-02-13
Neat! Everything went without a hitch...except the newly installed Emacs shows a graphical bug that causes its window not to be redrawn properly, making it unusable (although wherever text appears, it is clearly antialiased). At this point, I should embarrassingly admit that I'm still running Hoary, so I probably have no right to complain. However, has anyone else experienced this, or does anyone know more specifically what the cause might be?

---

### Post by Manny C on 2006-02-14
[QUOTE=Lux Perpetua]Neat! Everything went without a hitch...except the newly installed Emacs shows a graphical bug that causes its window not to be redrawn properly, making it unusable (although wherever text appears, it is clearly antialiased). At this point, I should embarrassingly admit that I'm still running Hoary, so I probably have no right to complain. However, has anyone else experienced this, or does anyone know more specifically what the cause might be?[/QUOTE]

Be embarrased...and I don't your problem on Breezy...dammit, dapper is nearly out.

---

### Post by Mr_Smiley on 2006-02-15
Hi,

Just followed through the instructions and it seemed to install ok. However when I try and run emacs I get this message:
```

emacs: Cannot open termcap database file
``` 
Thanks for any help.

EDIT: Well I managed to fix the problem by installing 'libncurses5-dev' and then recompiling emacs however I now have another problem. When starting emacs it loads the console version. Any ideas why?

Thanks.

---

### Post by Zed on 2006-02-17
Thanks for the HOWTO; Emacs looks great without having to run it in console mode in an xfce4-terminal.

Is there any way to convince apt (& friends) that this is an acceptable alternative to the emacs21 packages such that one could install auctex, or other things that have emacs21 packages as dependencies? (Yes, I know there may be incompatibilities and weirdness and  that it would be all my fault.)

---

### Post by Lux Perpetua on 2006-02-21
[QUOTE=Mr_Smiley]Hi,

Just followed through the instructions and it seemed to install ok. However when I try and run emacs I get this message:
```

emacs: Cannot open termcap database file
``` 
Thanks for any help.

EDIT: Well I managed to fix the problem by installing 'libncurses5-dev' and then recompiling emacs however I now have another problem. When starting emacs it loads the console version. Any ideas why?

Thanks.[/QUOTE]
I had the same problem initially, and I managed to fix it (on both Breezy and Dapper). I think it just didn't configure correctly. (libncurses-dev should be irrelevant to this thread, since we want Emacs to use GTK and XFT, let alone curses :)) 

1. First, install libgtk2.0-dev from Synaptic or apt-get.

2. If you try to follow the procedure now, it might work...but it didn't for me. Actually, make bootstrap failed, with gcc reporting syntax errors in a header file (apparently due to some un-kosher macro expansion). If this happens to you, you might try the following inelegant, hack-ish solution (**read: no guarantees implied whatsoever**): fire up a text editor (like gedit, if you don't have another Emacs) and open the file emacs/configure. Find the following section: 
```

if test "$have_x" != yes; then
  echo "$as_me:$LINENO: result: $have_x" >&5
echo "${ECHO_T}$have_x" >&6
  no_x=yes
else
  # If each of the values was on the command line, it overrides each guess.
  test "x$x_includes" = xNONE && x_includes=$ac_x_includes
  test "x$x_libraries" = xNONE && x_libraries=$ac_x_libraries
  # Update the cache value to reflect the command line values.
  ac_cv_have_x="have_x=yes \
		ac_x_includes=$x_includes ac_x_libraries=$x_libraries"
  echo "$as_me:$LINENO: result: libraries $x_libraries, headers $x_includes" >&5
echo "${ECHO_T}libraries $x_libraries, headers $x_includes" >&6
fi

```Exchange the lines "no_x=yes" and "else", so that the section looks like this: 
```

if test "$have_x" != yes; then
  echo "$as_me:$LINENO: result: $have_x" >&5
echo "${ECHO_T}$have_x" >&6
[b]else
  no_x=yes[/b]
  # If each of the values was on the command line, it overrides each guess.
  test "x$x_includes" = xNONE && x_includes=$ac_x_includes
  test "x$x_libraries" = xNONE && x_libraries=$ac_x_libraries
  # Update the cache value to reflect the command line values.
  ac_cv_have_x="have_x=yes \
		ac_x_includes=$x_includes ac_x_libraries=$x_libraries"
  echo "$as_me:$LINENO: result: libraries $x_libraries, headers $x_includes" >&5
echo "${ECHO_T}libraries $x_libraries, headers $x_includes" >&6
fi

```Now repeat  the compilation process, starting from the ./configure step. I don't know if it is actually a bug in the script or it is just a fluke that switching the two lines made it compile and run on my machine :) 

3. I haven't confirmed this, but I think there is a chance that

./configure --with-x-toolkit=gtk --with-xft=yes

won't configure properly, but this:

./configure --with-gtk --with-xft

did work for me. Something else to try.

(And the display problem I reported earlier doesn't appear when compiling on Breezy and Dapper.)

Thanks you, trevorv, for this howto. Finally, antialiased Emacs!

---

### Post by yigal.weinstein on 2006-02-27
Another (probably newbie) issue is installing additions to emacs after installation through this method.  Synaptic i.e. apt-get doesn't register it as being installed because it wasn't installed via a .deb package so how to add additions?  I have no clue.

---

### Post by thermans on 2006-02-28
[QUOTE=Lux Perpetua]Neat! Everything went without a hitch...except the newly installed Emacs shows a graphical bug that causes its window not to be redrawn properly, making it unusable (although wherever text appears, it is clearly antialiased). At this point, I should embarrassingly admit that I'm still running Hoary, so I probably have no right to complain. However, has anyone else experienced this, or does anyone know more specifically what the cause might be?[/QUOTE]

I don't think it has anything to do with Hoary.  I'm on Dapper and have redraw problems:

[IMG]http://www.hermans.net/images/emacs-xft.png[/IMG]

Not sure what the cause is.

---

### Post by thermans on 2006-02-28
[QUOTE=yigal.weinstein]Another (probably newbie) issue is installing additions to emacs after installation through this method.  Synaptic i.e. apt-get doesn't register it as being installed because it wasn't installed via a .deb package so how to add additions?  I have no clue.[/QUOTE]

You can do the following to build .debs for the build. Then you can install them in a way Synaptic will understand:

Add the following to "emacs/debian/rules":
```
emacs_gtk_confflags += --with-xft=yes
```
to the "Emacs-gtk confflags" section (round about line 754 of the file).

Now instead of doing "make; make install" and all that jazz do:
```
fakeroot dpkg-buildpackage -nc -b
```
When it's done you will have .deb files that you can install with "dpkg -i".

I got this from [here]("http://times.usefulinc.com/2005/12/02-emacs-xft") (although note the additional argument to the buildpackage command)

---

### Post by thermans on 2006-02-28
Another way to do it, possibly easier:

Build emacs like *trevorv* says in the original post.  But do the "configure" like this: ```
./configure --with-gtk --with-xft --prefix=/usr
```

Also do NOT do the "sudo make install" part.

Now install the *emacs-snapshot* packages like this:
```
sudo apt-get install emacs-snapshot-common
sudo apt-get install emacs-snapshot-el
sudo apt-get install emacs-snapshot-gtk
```
Then copy the new binary over the one you just installed:
```
install -b emacs/src/gtk-emacs /usr/bin/emacs
```
You'll have to remember to replace it each time you upgrade the snapshot, but this should work just fine.

---

### Post by yigal.weinstein on 2006-02-28
Everything is here:

[http://www.emacswiki.org/cgi-bin/wiki/EmacsCvsAndDebian](http://www.emacswiki.org/cgi-bin/wiki/EmacsCvsAndDebian)

---

### Post by VCSkier on 2006-03-01
hmmm...  not working for me yet.  this is what i get after editing the rules file, and then trying to do the ./configure command.```
reed@ubuntu:~/emacs$ ./configure --with-x-toolkit=gtk --with-xft=yes
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
reed@ubuntu:~/emacs$

```so i opened up "config.log" and this is what it reads.```
This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by configure, which was
generated by GNU Autoconf 2.59.  Invocation command line was

  $ ./configure --with-gtk --with-xft --prefix=/usr

## --------- ##
## Platform. ##
## --------- ##

hostname = ubuntu
uname -m = i686
uname -r = 2.6.12-10-686
uname -s = Linux
uname -v = #1 Mon Feb 13 12:18:37 UTC 2006

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = i686
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
hostinfo               = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/local/bin
PATH: /usr/local/sbin
PATH: /sbin
PATH: /usr/sbin
PATH: /bin
PATH: /usr/bin
PATH: /usr/bin/X11
PATH: /usr/games


## ----------- ##
## Core tests. ##
## ----------- ##

configure:1643: checking build system type
configure:1661: result: i686-pc-linux-gnulibc1
configure:1669: checking host system type
configure:1683: result: i686-pc-linux-gnulibc1
configure:2767: checking for gcc
configure:2783: found /usr/bin/gcc
configure:2793: result: gcc
configure:3037: checking for C compiler version
configure:3040: gcc --version </dev/null >&5
gcc (GCC) 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:3043: $? = 0
configure:3045: gcc -v </dev/null >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,java,f95,objc,ada,treelang --prefix=/usr --with-gxx-include-dir=/usr/include/c++/4.0.2 --enable-shared --with-system-zlib --libexecdir=/usr/lib --enable-nls --without-included-gettext --enable-threads=posix --program-suffix=-4.0 --enable-__cxa_atexit --enable-libstdcxx-allocator=mt --enable-clocale=gnu --enable-libstdcxx-debug --enable-java-gc=boehm --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.4.2-gcj-4.0-1.4.2.0/jre --enable-mpfr --disable-werror --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
configure:3048: $? = 0
configure:3050: gcc -V </dev/null >&5
gcc: '-V' option must have argument
configure:3053: $? = 1
configure:3076: checking for C compiler default output file name
configure:3079: gcc    conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:3082: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define MAIL_USE_POP 1
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:3121: error: C compiler cannot create executables
See `config.log' for more details.

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_build=i686-pc-linux-gnulibc1
ac_cv_build_alias=i686-pc-linux-gnulibc1
ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=
ac_cv_env_CFLAGS_value=
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_host=i686-pc-linux-gnulibc1
ac_cv_host_alias=i686-pc-linux-gnulibc1
ac_cv_prog_ac_ct_CC=gcc

## ----------------- ##
## Output variables. ##
## ----------------- ##

ALLOCA=''
CC='gcc'
CFLAGS=''
CPP=''
CPPFLAGS=''
C_SWITCH_X_SITE=''
DEFS=''
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP=''
EXEEXT=''
GETLOADAVG_LIBS=''
GETOPTOBJS=''
GETOPT_H=''
GTK_CFLAGS=''
GTK_LIBS=''
GZIP_PROG=''
INSTALL_DATA=''
INSTALL_INFO=''
INSTALL_PROGRAM=''
INSTALL_SCRIPT=''
KMEM_GROUP=''
LDFLAGS=''
LD_SWITCH_X_SITE=''
LD_SWITCH_X_SITE_AUX=''
LIBOBJS=''
LIBS=''
LIBSOUND=''
LN_S=''
LTLIBOBJS=''
MAINT='#'
NEED_SETGID=''
OBJEXT=''
PACKAGE_BUGREPORT=''
PACKAGE_NAME=''
PACKAGE_STRING=''
PACKAGE_TARNAME=''
PACKAGE_VERSION=''
PATH_SEPARATOR=':'
PKG_CONFIG=''
RANLIB=''
SET_MAKE=''
SHELL='/bin/sh'
XFT_CFLAGS=''
XFT_LIBS=''
X_TOOLKIT_TYPE=''
ac_ct_CC='gcc'
ac_ct_RANLIB=''
archlibdir='${libexecdir}/emacs/${version}/${configuration}'
bindir='${exec_prefix}/bin'
bitmapdir=''
build='i686-pc-linux-gnulibc1'
build_alias=''
build_cpu='i686'
build_os='linux-gnulibc1'
build_vendor='pc'
c_switch_machine=''
c_switch_system=''
canonical='i686-pc-linux-gnulibc1'
carbon_appdir=''
configuration='i686-pc-linux-gnulibc1'
datadir='${prefix}/share'
docdir='${datadir}/emacs/${version}/etc'
etcdir='${datadir}/emacs/${version}/etc'
exec_prefix='NONE'
gamedir='${localstatedir}/games/emacs'
gameuser='games'
host='i686-pc-linux-gnulibc1'
host_alias=''
host_cpu='i686'
host_os='linux-gnulibc1'
host_vendor='pc'
includedir='${prefix}/include'
infodir='${prefix}/info'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
liblockfile=''
lispdir='${datadir}/emacs/${version}/lisp'
lisppath='${locallisppath}:${lispdir}'
locallisppath='${datadir}/emacs/${version}/site-lisp:${datadir}/emacs/site-lisp:${datadir}/emacs/${version}/leim'
localstatedir='${prefix}/var'
machfile='m/intel386.h'
mandir='${prefix}/man'
oldincludedir='/usr/include'
opsysfile='s/gnu-linux.h'
prefix='/usr'
program_transform_name='s,x,x,'
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
srcdir='/home/reed/emacs'
sysconfdir='${prefix}/etc'
target_alias=''
version=''
x_default_search_path=''

## ----------- ##
## confdefs.h. ##
## ----------- ##

#define MAIL_USE_POP 1
#define PACKAGE_BUGREPORT ""
#define PACKAGE_NAME ""
#define PACKAGE_STRING ""
#define PACKAGE_TARNAME ""
#define PACKAGE_VERSION ""

configure: exit 77

```none of the really makes any sense to me, so let me know what you think.  thanks.

---

### Post by Lux Perpetua on 2006-03-05
[QUOTE=thermans]I don't think it has anything to do with Hoary.  I'm on Dapper and have redraw problems:

Not sure what the cause is.[/QUOTE]When I tried it on Hoary, it was much worse than that. I couldn't see what I was typing. I occasionally see the same bug you're seeing (on Breezy). I don't know what the cause is, either, but you can (mostly) fix it when it happens by giving Emacs the command **M-x redraw**.

---

### Post by fladd on 2006-03-10
Hi there,

any news on the redraw bug og the mode-line?
I figured out that it only occurs on some buffers. Exclusively on buffers that do have a formatting that has lines of different heights (customization, LaTeX-mode, etc.).
Is there a patch available? It is really anoying not to see the mode-line :-)

fladd

---

### Post by Jessehk on 2006-03-29
This worked exactly as described -- many thanks!

My one question: how I can get Ruby support? When I try to install it through Synaptic, it wants to install the emacs package. 

*emacs "newbie"*

---

### Post by Ebaad on 2006-03-30
I'm totally new to installing the emacs, I used it at my work long time ago and like it a lot for writting code in c and c++. I tried to download, ./configure and make, which worked and I also got through the error message about the termcap database, but now I'm stuck with the terminal version. When I type in emacs in a terminal it start the non windows version of emacs instead of the nice emacs window I remember from the past.

I dont know how to completly uninstall the emacs and start all over again, or make it work with the gui.

Any help wil really be appreciated.
](*,) 
Thanks,
Ebaad.

---

### Post by dpm on 2006-03-31
I followed the instructions as per post #1, but after successfully finishing the make and installation processes, running emacs gave me the same error as other people in this thread:

```
emacs: Cannot open termcap database file
``` 
I had installed the gtk dev libraries before running ./configure, and as I said, everything compiled and installed fine. I haven't tried installing the ncurses dev library though, as I saw from other posts that that wasn't really helpful either.

Any ideas?

---

### Post by ubuntumaneh on 2006-04-01
Hello,

i have been using emacs-snapshot for a while now. It is being very nice. Since Im in the middle of project I didn't get rid of emacs21. So, both emacs-snapshot and emacs21 are co-existing. Now, it so happen that there is one thing with is bothering me. In emacs22 somethings seem to be missing. For instance, in latex-mode I don't have C-c C-c to run latex, then view, etc. Further, reftex is not being loaded (it is in my .emacs) when I call .tex file, as it used to be in emacs21. in python-mode, I don't have the automatic tab. So many of this little features are missings. Also, I have installed planner-el, but emacs-snapshot don't recognize it. Nevertheless, emacs-snapshot is being very good. Then, I would like to change to it once for all. Now, my question:

how can i enable all this features in emacs-snapshot, like in emacs21?

It seems my old .emacs has no good use in emacs-snapshot.

Thanks

P.S.: Im really ready to leave emacs21 for emacs22. And this weekend seems to be a good period to do so.

---

### Post by Ebaad on 2006-04-04
[QUOTE=desp]
```
emacs: Cannot open termcap database file
``` 
Any ideas?[/QUOTE]


Hi Desp,

I did a lot of things since I installed the emacs to make it work, but when I checked the history I found the following command that installs the ncurses which fixed the above issue. Please give it a shot and see if it works.

sudo apt-get install libncurses5-dev

Thanks,
Ebaad.

---

### Post by kaamos on 2006-04-04
No more crashes!!

Just recompiled with this one line change to xfaces.c and emacs is stable in addition to looking good. :)

[http://www.nabble.com/patch-for-crash-in-XFT_JHD_BRANCH-t163660.html#a454431](http://www.nabble.com/patch-for-crash-in-XFT_JHD_BRANCH-t163660.html#a454431)

---

### Post by longtran79 on 2006-04-06
Hi all, Im a Ubuntu newbie. I just installed it on my laptop. I follow #1 post but  I got this error:
longtran79@ubuntu:~$ cvs -z3 -d:pserver:anonymous@cvs.savannah.gnu.org:/cvsroot/emacs co emacs
bash: cvs: command not found
longtran79@ubuntu:~$
Please give me some advice, thanks a lot!!!!!](*,) ](*,)

---

### Post by [myrddin] on 2006-04-07
[QUOTE=longtran79]
bash: cvs: command not found
[/QUOTE]
use sudo apt-get install cvs
but i think you should wait for an official ubuntu version with xft support and use now emacs-snapshot.

---

### Post by TheEclypse on 2006-04-07
I followed the HOWTO, but when I type "emacs" into the command line I get the console version of emacs, am I doing something wrong?

Thanks.

---

### Post by simon_cheng on 2006-04-08
I have the same problem. Everything is OK, untill I start it, and it is in console style.

---

### Post by TheEclypse on 2006-04-08
I tried configuring with:

./configure --with-gtk --with-xft

But now when I try and make bootsrtap I get the following error:

In file included from xmenu.c:130:
gtkutil.h:163: error: syntax error before &#8216;*&#8217; token
gtkutil.h:165: warning: &#8216;struct scroll_bar&#8217; declared inside parameter list
gtkutil.h:165: warning: its scope is only this definition or declaration, which is probably not what you want
gtkutil.h:179: warning: &#8216;struct scroll_bar&#8217; declared inside parameter list
gtkutil.h:192: error: syntax error before &#8216;*&#8217; token
gtkutil.h:194: error: syntax error before &#8216;Display&#8217;
gtkutil.h:195: error: syntax error before &#8216;*&#8217; token
gtkutil.h:196: error: syntax error before &#8216;*&#8217; token
gtkutil.h:204: error: syntax error before &#8216;Pixmap&#8217;
make[2]: *** [xmenu.o] Error 1

**Edit:** I got it to compile and work, try configuring using: ./configure --with-gtk --with-xft --x-includes=/usr/include/X11 --x-libraries=/usr/lib/X11

---

### Post by monotux on 2006-04-09
Thanks!
This worked without any problems on my dapper laptop - and emacs finally looks nice! :-D

---

### Post by longtran79 on 2006-04-10
I follow the #1 and get this error:

longtran79@ubuntu:~/emacs$ tla register-archive [email]jerome@debian.org[/email]--2005 [http://people.debian.org/~jerome/arch/jerome@debian.org--2005/](http://people.debian.org/~jerome/arch/jerome@debian.org--2005/)
bash: tla: command not found
longtran79@ubuntu:~/emacs$
longtran79@ubuntu:~/emacs$ tla get -A [email]jerome@debian.org[/email]--2005 emacs-snapshot-debian--main
bash: tla: command not found

any help will appreciate!

---

### Post by dpm on 2006-04-10
[quote=longtran79]I follow the #1 and get this error:

longtran79@ubuntu:~/emacs$ tla register-archive [EMAIL="jerome@debian.org"]jerome@debian.org[/EMAIL]--2005 [http://people.debian.org/~jerome/arch/jerome@debian.org--2005/]("http://people.debian.org/%7Ejerome/arch/jerome@debian.org--2005/")
bash: tla: command not found
longtran79@ubuntu:~/emacs$
longtran79@ubuntu:~/emacs$ tla get -A [EMAIL="jerome@debian.org"]jerome@debian.org[/EMAIL]--2005 emacs-snapshot-debian--main
bash: tla: command not found

any help will appreciate![/quote] 
Please read all posts on this thread.

You basically need to install tla, as mentioned in post #5:

```
 sudo apt-get install tla
``` 
Cheers.

---

### Post by sour_Kent on 2006-04-12
Thanks for the great HOWTO.
I was just wondering.... how would I remove this program later on...? 
I'm not really familiar with this way of installing programs.. could somebody give me a hint?

---

### Post by kaolin on 2006-04-13
> **thermans]You can do the following to build .debs for the build. Then you can install them in a way Synaptic will understand:

Add the following to "emacs/debian/rules":
```
emacs_gtk_confflags += --with-xft=yes
```
to the "Emacs-gtk confflags" section (round about line 754 of the file).

Now instead of doing "make said:**
> here[/URL] (although note the additional argument to the buildpackage command)

I followed your instruction but I am getting the following error:
```
 fakeroot dpkg-buildpackage -nc -b
dpkg-buildpackage: source package is emacs-snapshot
dpkg-buildpackage: source version is 20050519215621-1
dpkg-buildpackage: source changed by Jerome Marant <jerome@debian.org>
dpkg-buildpackage: host architecture i386
 debian/rules build
grep: lisp/version.el: No such file or directory
grep: configure.in: No such file or directory
grep: man/Makefile.in: No such file or directory
test -d debian/patched || install -d debian/patched
dpatch  apply-all
applying patch debian-version-mention to ./ ... failed.
make: *** [patch-stamp] Error 1

```
I already successfully built emacs by following the first post, I would just like to install emacs packages via synaptics. Is that the cause of the error?
Thanks,

---

### Post by m87 on 2006-04-14
guys, this branch is stalled since 3 months ago... see changelog.
romain, the current emacs-snapshot debian maintainer told me that the xft code should have been rewritten for 22.1. not sure when this will happen though :)

---

### Post by thermans on 2006-04-21
Kaolin, did you put the emacs source from cvs in a different place maybe?

You should have something like:
> /usr/local/src/emacs
/usr/local/src/emacs/debian

Where "debian" is the package you downloaded from Jerome.

I'm thinking you might have this:
> /usr/local/src/emacs/
/usr/local/src/debian

---

### Post by danirus on 2006-05-11
If you are getting the **console version**, you should check the output of "configure" command. "configure" looks for libraries and headers to detect and setup the compilation against the proper X Toolkit. Probably you must install some additional packages, like: libxt-dev and libgtk2.0-dev

To be sure you have everything you need, check for this lines in the output of configure command:
```

Configured for `i686-pc-linux-gnu'.

  Where should the build process find the source code?    /home/danirus/cvs/savannah/emacs
  What operating system and machine description files should Emacs use?
        `s/gnu-linux.h' and `m/intel386.h'
  What compiler should emacs be built with?               gcc -g -O2 -Wno-pointer-sign
  Should Emacs use the GNU version of malloc?             yes
      (Using Doug Lea's new malloc from the GNU C Library.)
  Should Emacs use a relocating allocator for buffers?    yes
  Should Emacs use mmap(2) for buffer allocation?         no
  What window system should Emacs use?                    **x11**
  What toolkit should Emacs use?                          **GTK**
  Where do we find X Windows header files?                **Standard dirs**
  Where do we find X Windows libraries?                   **/usr/X11R6/lib**
  Does Emacs use -lXaw3d?                                 no
  Does Emacs use -lXpm?                                   no
  Does Emacs use -ljpeg?                                  no
  Does Emacs use -ltiff?                                  no
  Does Emacs use -lungif?                                 no
  Does Emacs use -lpng?                                   yes
  Does Emacs use X toolkit scroll bars?                   yes

```

---

### Post by Zed on 2006-05-25
As of [April](http://www.emacswiki.org/cgi-bin/wiki/XftGnuEmacs) the XFT branch in Emacs' CVS works without patching. This is what I did in Dapper for anti-aliased goodness (I'd guess it works in Breezy too, but I haven't tested it.)

```

sudo apt-get install emacs-snapshot-gtk
cd /opt
sudo cvs -z3 -d:pserver:anonymous@cvs.savannah.gnu.org:/cvsroot/emacs co emacs
cd emacs
sudo cvs up -Pd -r XFT_JHD_BRANCH
sudo ./configure --with-x-toolkit=gtk --with-xft=yes --prefix=/usr
sudo make bootstrap && make
sudo rm /etc/alternatives/emacs
sudo ln -s /opt/emacs/src/emacs /etc/alternatives/emacs 

```

This follows [thermans' suggestion](http://ubuntuforums.org/showpost.php?p=778806&postcount=29) of installing the emacs-snapshot to be sure of getting all the right dependencies and building the right directory structure under /usr/ such that you can install emacs libraries conventionally and your emacs will find them. But instead of overwriting the binary, I just relink /etc/alternatives/emacs, which is what /usr/bin/emacs links to.

---

### Post by Twiggy794 on 2006-05-30
Looks great, but I've got two Emacs related questions as one of these problems seems to have popped up after doing this.

First off, the Delete key behaves like a Backspace.  Any way to change that back?

Second, what's the .emacs syntax to set a default window size?  Mine always starts off all tiny and I like it pretty large.

---

### Post by softrain on 2006-05-30
[QUOTE=Twiggy794]
Second, what's the .emacs syntax to set a default window size?  Mine always starts off all tiny and I like it pretty large.[/QUOTE]

you can put this in your ~/.emacs file

```
(set-frame-height (selected-frame) 50)
(set-frame-width (selected-frame) 120)

```

---

### Post by Zed on 2006-05-31
Here's a [discussion on delete/backspace in Emacs.](http://www.emacswiki.org/cgi-bin/wiki/BackspaceKey)

---

### Post by nullGambit on 2006-06-04
[QUOTE=thermans]Another way to do it, possibly easier:

Build emacs like *trevorv* says in the original post.  But do the "configure" like this: ```
./configure --with-gtk --with-xft --prefix=/usr
```

[/QUOTE]


I'm running Ubuntu 6.0.6 and I'm getting a configure error (I have both libgtk2.0-0 and libglib2.0-0 installed):

checking for gtk+-2.0 >= 2.0.1 glib-2.0 >= 2.0.1... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found Package glib-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `glib-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'glib-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 2.0.1 glib-2.0 >= 2.0.1) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.


How do I fix this problem?

---

### Post by sherlock-holmes on 2006-06-04
[QUOTE=nullGambit]I'm running Ubuntu 6.0.6 and I'm getting a configure error (I have both libgtk2.0-0 and libglib2.0-0 installed):

checking for gtk+-2.0 >= 2.0.1 glib-2.0 >= 2.0.1... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found Package glib-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `glib-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'glib-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 2.0.1 glib-2.0 >= 2.0.1) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

How do I fix this problem?[/QUOTE]

this all go back to having certain libraries..

libgtk2-dev ..
libcairo2-dev
libfontconfig1-dev etc.....

try searching in synaptic, install...and recompile emacs..

...i was stuck at these for quite some time....if u have installed the patched version of "libgtk2ubuntu....patched..." (to make the fonts better as given in a different thread)...then you will get some dependancy error and you will be in a loop with various libs with mutual dependancy issu](*,) es...

i essentially reinstalled 6.06..and i am still trying...

---

### Post by anindya_m on 2006-06-11
Hi,
     Is anyone interested in .deb files for emacs with xft and gtk support. I just made versions for breezy and dapper (i386) and if anyone wants I can make it available.

regards,
Anindya

---

### Post by anindya_m on 2006-06-15
Hello again,
              I have kept .debs for emacs (Xft) and auctex at the following url:
[http://theory/~anindya_m/ubuntu.html]("http://theory/~anindya_m/ubuntu.html")
This is compiled from the latest cvs snapshot. 

To install emacs-xft use: ```
sudo dpkg -i emacs-xft-gtk_1.0-1ubuntu1_i386_dapper.deb
```
This will install emacs-xft in /usr/local and will not disturb Ubuntu's emacs installation.

To install auctex-xft use:```
sudo dpkg --force-overwrite -i auctex-xft_11.83-1_i386_dapper.deb
```
the --force option is needed as the two packages share the same doc directory and will cause auctex-xft to just add the files to the emacs-xft doc directory. It is harmless. 

To activate auctex and latex-preview add the following lines to .emacs:```
(require 'tex-site)
(load "preview-latex.el" nil t t)
```

regards,
Anindya

---

### Post by MaherG on 2006-06-16
[QUOTE=anindya_m]Hello again,
              I have kept .debs for emacs (Xft) and auctex at the following url:
[http://theory/~anindya_m/ubuntu.html]("http://theory/~anindya_m/ubuntu.html")
This is compiled from the latest cvs snapshot. 

To install emacs-xft use: ```
sudo dpkg -i emacs-xft-gtk_1.0-1ubuntu1_i386_dapper.deb
```
This will install emacs-xft in /usr/local and will not disturb Ubuntu's emacs installation.

To install auctex-xft use:```
sudo dpkg --force-overwrite -i auctex-xft_11.83-1_i386_dapper.deb
```
the --force option is needed as the two packages share the same doc directory and will cause auctex-xft to just add the files to the emacs-xft doc directory. It is harmless. 

To activate auctex and latex-preview add the following lines to .emacs:```
(require 'tex-site)
(load "preview-latex.el" nil t t)
```

regards,
Anindya[/QUOTE]
This is the correct link

[http://theory.tifr.res.in/~anindya_m/ubuntu.html](http://theory.tifr.res.in/~anindya_m/ubuntu.html)

---

### Post by kabanta on 2006-06-24
This is great! Thanks for the .deb files

[QUOTE=anindya_m]To install emacs-xft use: ```
sudo dpkg -i emacs-xft-gtk_1.0-1ubuntu1_i386_dapper.deb
```[/QUOTE]
Note: if you execute the command above and get errors such as "*dependency problems prevent configuration of emacs-xft-gtk*", try executing the following  command and the missing dependencies (and emacs) will be installed:

```
sudo apt-get -f install
```
(And the same again, if similar errors when trying to install the auctex .deb file)

---

### Post by bakert on 2006-07-10
<please delete this post can't work out how!>

---

### Post by Steinar on 2006-07-16
> **Mr_Smiley said:**
> Hi,

Just followed through the instructions and it seemed to install ok. However when I try and run emacs I get this message:
```

emacs: Cannot open termcap database file
``` 
Thanks for any help.

EDIT: Well I managed to fix the problem by installing 'libncurses5-dev' and then recompiling emacs however I now have another problem. When starting emacs it loads the console version. Any ideas why?

Thanks.


The X.org development libraries are not installed by default, and this is what gets you into trouble.  If you look at the results of the ./configure, you'll see a couple of "NONE" indicating that configure (rightly) doesn't find the libraries it needs to.

I think libxt-dev and libxaw7-dev should do the trick. :)

---

### Post by cnhzcy14 on 2006-07-20
Hi guys, try this emacs deb with xft:
[http://people.freedesktop.org/~keithp/emacs-xft/](http://people.freedesktop.org/~keithp/emacs-xft/)
It can really replace the emacs-snapshot-gtk in the reporsitory, that means it can work with other .el packages in the reporsitory.

---

### Post by yenliangl on 2006-07-29
> **sherlock-holmes said:**
> this all go back to having certain libraries..

libgtk2-dev ..
libcairo2-dev
libfontconfig1-dev etc.....

try searching in synaptic, install...and recompile emacs..

...i was stuck at these for quite some time....if u have installed the patched version of "libgtk2ubuntu....patched..." (to make the fonts better as given in a different thread)...then you will get some dependancy error and you will be in a loop with various libs with mutual dependancy issu](*,) es...

i essentially reinstalled 6.06..and i am still trying...

You can try to install libgtk+-dev and downgrade libcairo to proper version.

---

### Post by timseal on 2006-07-31
> **cnhzcy14 said:**
> Hi guys, try this emacs deb with xft:
[http://people.freedesktop.org/~keithp/emacs-xft/](http://people.freedesktop.org/~keithp/emacs-xft/)
It can really replace the emacs-snapshot-gtk in the reporsitory, that means it can work with other .el packages in the reporsitory.

On first glance, I thought I'd seen that before - but then I saw it was from keithp, an _extremely_ reputable source.  I wonder if he has been working on the code?

---

### Post by mpx on 2006-08-02
> **timseal said:**
> On first glance, I thought I'd seen that before - but then I saw it was from keithp, an _extremely_ reputable source.  I wonder if he has been working on the code?
This is awesome. Anti-aliased emacs looks so good. Thanks for providing the instructions and the deb files. I used the deb files and the installation was a breeze.

---

### Post by mpx on 2006-08-02
ok.. I guess I spoke too soon. Aparently the emacs snapshot version is not very stable. I had it running overnight and today morning it had crashed. 

I should perhaps build from source of a stable version. So the question is: does the anti-alias support exist *only* in the latest snapshot version? Or can I use a older stable version to build?  Thanks.

---

### Post by Note360 on 2006-08-06
I am getting this error.

emacs: Cannot open termcap database file

Right now I use (g)vi(m) but emacs is just to ugly for me.

---

### Post by Note360 on 2006-08-07
I fixed that one but now everything is on the left and I am right handed. Help!!!!!!

---

### Post by deepspring on 2006-08-07
Thanks for the guide!

---

### Post by speedy_arnakke on 2006-08-13
Great howto, but a get

emacs: Cannot open termcap database file

when I tried to run emacs frome the terminal.

Any tips?

---

### Post by speedy_arnakke on 2006-08-13
Sorry folks. I'm a newbie forum user and did not notice the small numbers at the bottom of the page indicating the thread had more pages...

Anyhow, my beautiful emacs is up and running thanks to #45

---

### Post by anasofiapaixao on 2006-08-17
**EDIT 2:** I would advise anyone with a stupid machine and who is as linux-stupid as I am to NOT follow the howto and to use [the wonderful Anindya's deb package]("http://theory.tifr.res.in/~anindya_m/ubuntu.html"). I went through dependency hell with the compilation and ended up erasing tla, cvs and almost anything with "emacs" on folder/filename on my pc out of rage, while the package installation was a breeze - it even took care of TWENTY-THREE dependencies without me having to move a finger!



I followed this howto step by step, everything runned without a hitch, except for a little detail... emacs is *still* in GTK 1.2!! And yes I did restart the computer, to check if that wasn't the problem... any help?

Also, I don't have any such file as ".Xresources" in my home dir, the closest I found was ".Xauthority", has this anything to do with the problem?

EDIT: Never mind me, I couldn't imagine the emacs menu entry wasn't the same link I needed to use. Typed "emacs on the terminal and got "emacs: Cannot open termcap database file", will install. Still trying to workaround it with the help of people's previous posts.

---

### Post by EGR on 2006-08-19
I was wondering, has anyone else been experiencing problems with installing AucTeX from the .deb package? When I run dpkg -i on it, I get the following error message:
```
dpkg: error processing auctex-xft_11.83-1_i386_dapper.deb (--install):
 trying to overwrite `/usr/local/share/info/dir', which is also in package emacs-xft-gtk
dpkg-deb: subprocess paste killed by signal (Broken pipe)

```
---
Sorry, I see the question is already answered above. I really should have read more carefully.

Cheers,
EGR

---

### Post by dbenhur on 2006-08-28
Anindya's .deb package installed great for me on my i386 box. Yeah, emacs that doesn't sear the eyes!  And it finally responds to drag+drop too.

On amd64, however, I get the complaint about it being for the wrong architecture (i386) though.

Should I just try it with --force-architecture ?  Will I need to do bunch of fixups to get it all together?  Anyone been through this already?

---

### Post by Anonii on 2006-09-03
Is there a .deb for a Kubuntu (KDE in general) or do you have any other howtos?
The emacs I installed in Kubuntu so far doesnt support antialiasing and the text doesnt change color when you start a function etc...
Do you know how can this be fixed? 
I used these packages to install emacs:
_emacs21 emacs-extra emacs-goodies-el emacs auctex preview-latex xfonts-jmk_

---

### Post by GoldBuggie on 2006-09-24
NOTE for KDE users:
Since the gtk2-engines-qt is version 0.6 in dapper you will get the background problem(background color is only set to text not to whole display). To remove this install the latest version 0.7: [http://www.freedesktop.org/wiki/Software/gtk-qt](http://www.freedesktop.org/wiki/Software/gtk-qt)

---

### Post by Skardal on 2006-09-26
Thanks! This looked great!
I got some errors when I installed the .deb's but it haven't complained about anything when using the program, so I guess I'll just ignore it 8)

---

### Post by Frédéric Perrin on 2006-10-07
I tried installing Anindya's deb, but why does it depends on things like gnome-screensaver (?), compiz (a 3D desktop ?) or rhythmbox (!) ?
It seems to me that the packaging is not very well done...

---

### Post by Bionic_Beefpile on 2006-10-09
I had this installed previously, using the deb packages.  I migrated to beryl, so removed the compiz packages, and now it's pretty well broken.

The deb packages indeed depend on compiz, which in turn seems to depend on csm, which I can't find anywhere.

The error I get when I try to run ./configure --with-gtk --with-xft
is the follwing:
> checking for gtk+-2.0 >= 2.0.1 glib-2.0 >= 2.0.1... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found Package glib-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `glib-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'glib-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 2.0.1 glib-2.0 >= 2.0.1) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

---

### Post by Bionic_Beefpile on 2006-10-17
After a bit of poking at this and some Googling, I found that many people recommend installing libgtk2.0-dev

Unfortunately this fails with unmet dependencies.
A bit more work, and I tracked it down to libcairo2-dev, which is giving me:
> The following packages have unmet dependencies:
  libcairo2-dev: Depends: libcairo2 (= 1.0.4-0ubuntu1) but 1.2.2-0ubuntu2 is to be installedE: Broken packages

I'm officially stumped now ](*,)

---

### Post by blastura on 2006-10-18
Hi
I followed this:
> **Zed said:**
> As of [April](http://www.emacswiki.org/cgi-bin/wiki/XftGnuEmacs) the XFT branch in Emacs' CVS works without patching. This is what I did in Dapper for anti-aliased goodness (I'd guess it works in Breezy too, but I haven't tested it.)

```

sudo apt-get install emacs-snapshot-gtk
cd /opt
sudo cvs -z3 -d:pserver:anonymous@cvs.savannah.gnu.org:/cvsroot/emacs co emacs
cd emacs
sudo cvs up -Pd -r XFT_JHD_BRANCH
sudo ./configure --with-x-toolkit=gtk --with-xft=yes --prefix=/usr
sudo make bootstrap && make
sudo rm /etc/alternatives/emacs
sudo ln -s /opt/emacs/src/emacs /etc/alternatives/emacs 

```

This follows [thermans' suggestion](http://ubuntuforums.org/showpost.php?p=778806&postcount=29) of installing the emacs-snapshot to be sure of getting all the right dependencies and building the right directory structure under /usr/ such that you can install emacs libraries conventionally and your emacs will find them. But instead of overwriting the binary, I just relink /etc/alternatives/emacs, which is what /usr/bin/emacs links to.
and it works. I have emacs running and it sure do looks good now, but I get random crashes
```
Fatal error (11)Segmentation fault
```
I run Ubuntu Dapper with XGL Beryl(compiz)
/ Thanks for any help, I really can't live without emacs, and I don't like ugly fonts

---

### Post by Bionic_Beefpile on 2006-10-26
Well after updating to Edgy, I was now able to install libgtk2.0-dev, and then followed the steps in the above post.  Works great!

---

### Post by TexLogic on 2006-10-28
Emacs-gtk + antialiasing compiled nicely for me.  Two issues though.  First, the toolbar icons are flat greyscale instead of the nice 3d colored icons.  Second, the Emacs status bar is often overwritten by the last line in my text buffer.

Any idea how to solve either of these problems?

Thanks.

TexLogic

---

### Post by mistermix on 2006-10-31
This worked for me in edgy, but I also had to apply the patch from here:

[http://www.forcix.cx/work_environment/emacscvs.html](http://www.forcix.cx/work_environment/emacscvs.html)

to get the resulting emacs to run like "debian" emacs, i.e., running startup files from /etc/emacs

---

### Post by mak42 on 2006-11-01
> **blastura said:**
> Hi
I followed this:

and it works. I have emacs running and it sure do looks good now, but I get random crashes
```
Fatal error (11)Segmentation fault
```
I run Ubuntu Dapper with XGL Beryl(compiz)
Dito, but I run Ubuntu Edgy without compiz.
Maybe it works with an older cvs snapshot?

---

### Post by WhizCas on 2006-11-01
Im getting this error:

> cas@cas-desktop:~/emacs$ tla register-archive [email]jerome@debian.org[/email]--2005 [http://people.debian.org/~jerome/arch/jerome@debian.org--2005/](http://people.debian.org/~jerome/arch/jerome@debian.org--2005/)
cas@cas-desktop:~/emacs$ tla get -A [email]jerome@debian.org[/email]--2005 emacs-snapshot-debian--main
webdav error: 404 Not Found

---

### Post by sperlyjinx on 2006-11-02
> **WhizCas said:**
> Im getting this error:

I'm getting the same error...is this snapshot no longer available?

---

### Post by elektronaut on 2006-11-23
I also tried it Zed's way:
```
sudo apt-get install emacs-snapshot-gtk
cd /opt
sudo cvs -z3 -d:pserver:anonymous@cvs.savannah.gnu.org:/cvsroot/emacs co emacs
cd emacs
sudo cvs up -Pd -r XFT_JHD_BRANCH
sudo ./configure --with-x-toolkit=gtk --with-xft=yes --prefix=/usr
sudo make bootstrap && make
sudo rm /etc/alternatives/emacs
sudo ln -s /opt/emacs/src/emacs /etc/alternatives/emacs
```
Now I got two emacs on my system. One is /usr/bin/emacs-snapshot-gtk. This is from the Ubuntu repository, it's version is 22.0.50.1. Then I have /opt/emacs/src/emacs from cvs, version 22.0.50.2. Doesn't seem to make a big difference version number wise. The latter has a much uglier gui than the 'official' one. What's going on here? Do I somehow have to configure it's looks?

---

### Post by Ryan H on 2006-12-02
I'm also getting the error:
webdav error: 404 Not Found

Anyone know why?

-Ryan H

---

### Post by svref on 2006-12-12
I just skipped that step.  It seemed to work OK for me.  Then again, I'm running debian stable, so what the hork am I doing here?
____________________-

My biggest complaint with the new emacs is that the block cursor is SOLID BLACK.  I can't see the char that's underneath it!  Customizing the "cursor" face has no effect on the actual cursor.

---

### Post by durus on 2007-01-13
Thx for this How to, it looks very good now, but i have some questions:
How do i change font ?
How do i know witch fonts i have ?
Witch fonts do you recommend ?
How do i fix auto indent in python, it do not work after installing with antialiasing  ?

---

### Post by etola on 2007-01-18
> **anasofiapaixao said:**
> 
Also, I don't have any such file as ".Xresources" in my home dir, the closest I found was ".Xauthority", has this anything to do with the problem?


 no its not the same file. you can create it yourself in your home dir ~/.

---

### Post by etola on 2007-01-18
> **Ryan H said:**
> I'm also getting the error:
webdav error: 404 Not Found

Anyone know why?

-Ryan H

same for me too

---

### Post by shak on 2007-02-05
i found something useful in the net (esp. google cache ;) )

.Xresources

```


Emacs*FontBackend: xft
Emacs*font: Monospace-11
Xft.dpi: 96
Xft.hinting: None


```

no need to restart the X-Server just do:

```

xrdb -merge ~/.Xresources

```

kind regards

---

### Post by rosslaird on 2007-03-29
This howto only got me part way there, so I tried the debian (ubuntu) package from Alexandre Vassalotti:

[http://peadrop.com/blog/2007/01/06/pretty-emacs](http://peadrop.com/blog/2007/01/06/pretty-emacs)

Worked perfectly.

Ross

---

### Post by willnapier on 2007-08-27
Hi, I would just like to say that the link in the above post worked perfectly for me on feisty. I hope that it's description as alpha doesn't mean that it is really unstable. Will report back if so.

---

### Post by phill0 on 2008-04-04
Well it's April 2008 and I'm not sure whether above info applies to modern days. It would be amazing if it does. I didn't compile anything yet but tried to use emacs as it's distributed for Ubuntu 7.10. I don't get antialiased fonts of course, so I tried and I can start emacs with different fonts (the names of which I get from xlsfonts) for example:
```

emacs --font "lucidasanstypewriter-10"

```
This changes the font but I can't make it look antialiased which is quite amazing since fonts everywhere in the system are nice... :(

I have also tried putting:
```

Emacs*FontBackend: xft
Xft.dpi: 96
Xft.hinting: None

```
And then doing "xrdb -merge ~/.Xresources", but that didn't change anything.

Can someone who knows current state of Emacs in Ubuntu say what should be done in modern days, should I still download a cvs version and compile it?

---

### Post by Arathon on 2008-04-17
Not to oversimplify, but I do know of one solution that worked wonderfully for me.  Given that the "Pretty Emacs" (Google it) solution doesn't seem to be working for Hardy Heron, I found something else online that someone said worked.

However, you have to be running Hardy.  =P  If you do decide to make the upgrade, then all you have to do is install

```

sudo apt-get install emacs-snapshot-gtk
```

then, within your home directory, create an .Xresources file to tell emacs what font to use...as you can see, I chose Monospace-10.  You could choose anything you want.

```

echo "Emacs.font: Monospace-10" > .Xresources
```

On a fresh install of the RC for Hardy Heron, this worked perfectly.  Nothing else that I tried did.

Oh, and to give credit where it's due: [http://psung.blogspot.com/2008/03/emacs-in-ubuntu-hardy-now-has-anti.html](http://psung.blogspot.com/2008/03/emacs-in-ubuntu-hardy-now-has-anti.html)

---

### Post by z0mbie on 2008-04-17
I'm starting to learn Emacs, thanks for this tutorial. I will defintely give it a shot.

---

### Post by control_guy on 2008-05-02
> **Ebaad said:**
> Hi Desp,

sudo apt-get install libncurses5-dev

Thanks,
Ebaad.

Thank you Ebaad. That worked for me.

---

### Post by mohbana on 2008-11-02
Thanks! Very quick and painless. But, this package requires one to start emacs from the command line, they aren't menu icons what so ever.

---

