---
title: "Stupid Newbie gnu automake questions."
date: 2008-10-24
forum: Programming Talk
---

### Post by Jonas thomas on 2008-10-24
I could use one of you guys/gals who know what your doing help.

I've been working through a tutorial on gnu autotools ([http://www.lrde.epita.fr/~adl/autotools.html]("http://www.lrde.epita.fr/~adl/autotools.html")) and I've been trying to follow the steps verbatim.  (This tutorial works well with Adobe btw) 

I'm made it to page 107 and and I tried the following:
```
jonas@Ubuntu4:~/amhello$ autoreconf --install
configure:1987: error: possibly undefined macro: AC_PACKAGE_TARNAME
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure:1988: error: possibly undefined macro: AC_PACKAGE_VERSION
autoreconf: /usr/bin/autoconf failed with exit status: 1
jonas@Ubuntu4:~/amhello$ ls -R
.:
aclocal.m4  autom4te.cache  configure  configure.ac  Makefile.am  src

./autom4te.cache:
output.0  output.1  requests  traces.0  traces.1

./src:
main.c  Makefile.am

```
Needless to say this is not what the tutorial said would happen..
It appears that the offending lies are the following in "configure"

```
# Define the identity of the package.
 PACKAGE='AC_PACKAGE_TARNAME'
 VERSION='AC_PACKAGE_VERSION'
```

My understanding from the tutorial is that I need to have every defined in 
[LIST]
[*]configure.ac  
[*]Makefile.am 
[*]src/Makefile.am
[/LIST]
and run "autoreconf --install" and everything should magically happen..
I followed the tutorial exactly (I think),  Should I be adding something to configure.ac to prevent this line from being generated in configure ??
Current contents of of the files is as follows:
configure.ac
[EDIT: BUGS are in this section "AC_INIT_AUTOMAKE (" s/b "AC_INIT_AUTOMAKE("
also "&#8722;Wall &#8722;Werror" s/b "-Wall -Werror"(somehow the "-" got screwed up when I copied code from the PDF(SEE NEXT POST FOR SOMETHING THAT RUNS))]
```
AC_INIT ([amhello],[1.0],[nottoday@blahblah.com])
AM_INIT_AUTOMAKE ([&#8722;Wall &#8722;Werror foreign])
AC_PROG_CC
AC_CONFIG_HEADERS ([config.h])
AC_CONFIG_FILES ([
Makefile 
src/Makefile
])
AC_OUTPUT
```

Makefile.am
```
SUBDIRS = src
```

src/configure.ac
```
bin_PROGRAMS = hello
hello_SOURCES = main.c
```

and while we're at it.
main.c
[EDIT Code below is buggie also.. problems with "&#8221;" s/b """, also gave up on trying to get "puts("This is " PACKAGE STRING "." );" to work simplified to puts(PACKAGE_STRING) and called it a day :)]
```
#include<config.h>
#include<stdio.h>
int 
main (void)
{
   puts (&#8221;Hello World ! &#8221;);
   puts ( &#8221;This is &#8221;PACKAGE STRING &#8221;.&#8221; );
   return 0;
}
```

:confused::confused::confused::confused::confused::confused:
Thanks,
JT

---

### Post by Jonas thomas on 2008-10-24
Well, I sort figured out what went wrong with the configure.ac file anyway.
I didn't realize that this file is very white space sensitive.  I also used had a problem with the "-" in the "-Wall".  I copied the script from the PDF to clipboard and it got weird on me.
This seemed to get rid of the error
> AC_INIT([amhello],[1.0],[blah@blahblah.com])
AM_INIT_AUTOMAKE([-Wall -Werror foreign])
AC_PROG_CC
AC_CONFIG_HEADERS([config.h])
AC_CONFIG_FILES([
Makefile 
src/Makefile
])
AC_OUTPUT

Still getting errors.. But I think I'll be able to track them down.

---

