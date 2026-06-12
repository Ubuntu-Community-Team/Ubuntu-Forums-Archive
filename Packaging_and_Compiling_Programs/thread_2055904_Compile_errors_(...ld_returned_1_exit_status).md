---
title: "Compile errors (...ld returned 1 exit status)"
date: 2012-09-10
forum: Packaging and Compiling Programs
---

### Post by chrisinpants on 2012-09-10
It seems I've messed up my compiler library and thus cannot compile anything. I end up with:

/usr/local/bin/ld: this linker was not configured to use sysroots
collect2: ld returned 1 exit status

when trying. This may have happened when I configured an AVR tool chain but I'm not sure, something I need to take a little more time over next time, me being new to linux, and newer yet to compiling for source. Upon logging in, my default PATH is:

/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

I don't know where lightdm came from and I thought this was the problem and have tried to grep for entries with nothing coming back. I've removed it per session but this does not change anything when I try to compile, anything (e.g. hello.c). Errors from various source packages include recurring errors like:

configure:3498: gcc -V >&5
gcc: error: unrecognized option '-V'
gcc: fatal error: no input files
compilation terminated.
configure:3509: $? = 4
configure:3498: gcc -qversion >&5
gcc: error: unrecognized option '-qversion'
gcc: fatal error: no input files

I've been scouring for a solution but don't really have the knowledge to work it out...I hope someone can help.


I have gcc, g++, and other libraries required to compile but it seems that there's a missing link...


#gcc -v:

[http://paste.ubuntu.com/1201818/](http://paste.ubuntu.com/1201818/)

---

### Post by oldos2er on 2012-09-10
Moved to Packaging and Compiling Programs.

---

### Post by chrisinpants on 2012-09-10
Sorry for the mistake, and thanks for moving

---

### Post by chrisinpants on 2012-09-12
I changed my post quite a bit after doing a bit of digging. Bump!

---

### Post by dodo3773 on 2012-09-12
How did you wind up with ld being located in /usr/local/bin? Is that something you put together or was that the default? The first thing that caught my eye when reading your post is this --> "This may have happened when I configured an AVR tool chain". Can you tell us or link us to how you did this? It may help for other people viewing this post.

---

### Post by chrisinpants on 2012-09-13
The guide is below for reference but tbh, but I don't think that guide will indicate anything to do with my problem. That's just the last process of events I remember being able to compile successfuly. I remember mingw being a pain to configure, which if I remember rightly, was an offshoot of this process.


[http://www.ladyada.net/learn/avr/setup-unix.html](http://www.ladyada.net/learn/avr/setup-unix.html)

I've made tarballs of root every few days since installation if they're any use here.

---

### Post by dodo3773 on 2012-09-13
Do you have more than one ld installed? Is ld also at "/usr/bin/ld" or similar? If you export your $PATH to not include "/usr/local/bin" temporarily does your program compile? Just a shot in the dark but this is some stuff I would take a look at

---

### Post by chrisinpants on 2012-09-14
Thanks for the tips. I have:

/usr/bin/avr-ld
/usr/bin/ld

/usr/bin/ld.bfd
/usr/bin/ld.gold
/usr/bin/ldd

/usr/local/bin/ld
/usr/local/bin/ld.bfd

Things remain the same when excluding /usr/local/bin

my ldconfig:

#!/bin/sh

if  test $# = 0							\
    && test x"$LDCONFIG_NOTRIGGER" = x				\
 && test x"$DPKG_MAINTSCRIPT_PACKAGE" != x			\
 && dpkg-trigger --check-supported 2>/dev/null			\
 && dpkg --compare-versions "$DPKG_RUNNING_VERSION" ge '1.14.5ubuntu10~~'
then
	if dpkg-trigger --no-await ldconfig; then
		if test x"$LDCONFIG_TRIGGER_DEBUG" != x; then
			echo "ldconfig: wrapper deferring update (trigger activated)"
		fi
		exit 0
	fi	
fi

exec /sbin/ldconfig.real "$@"

---

### Post by dodo3773 on 2012-09-14
Other than rebuilding everything I do not know. Wish I could help more but this is over my head for now

---

### Post by chrisinpants on 2012-09-14
Ah no worries man, thanks for trying anyway. I'm just glad I learned how to automate tar, back to the clock :) 

And I think the next trick would be keeping the toolchains seperated somehow. I remember talk of such things, somewhere out there. Perhaps logging all my terminal input would be an idea too, for future fumble.

---

