---
title: "can't compile util-linux on ubuntu?"
date: 2007-01-22
forum: Programming Talk
---

### Post by 25an on 2007-01-22
Hi!

I am trying to compile util-linux i start by ./configure and then I get the following message

You have <scsi/scsi.h>
You have <linux/blkpg.h>
You have <linux/kd.h>
You have <locale.h>
You have <langinfo.h>
You have <sys/user.h>
You don't have <uuid/uuid.h>
You have <rpcsvc/nfs_prot.h>
You have <asm/types.h>
You have <linux/raw.h>
You have <stdint.h>
You have <sys/io.h>
You have inet_aton()
You have fsync()
You have getdomainname()
You have nanosleep()
You have personality()
You have updwtmp()
You have fseeko()
You have lchown()
You have rpmatch()
You have <term.h>
You have ncurses. Using <ncurses.h>.
You have termcap
You need -lcrypt
You don't have native language support
You have __progname
You have <pty.h> and openpty()
You have wide character support
You have SYS_pivot_root
You have a tm_gmtoff field in struct tm
Your rpcgen seems to work
You have zlib
You don't have blkid

so I started to look for blkid and uuid  and I found the blkid bin. So i tried to compile it any way
then i got following error

llseek.c:34: error: expected declaration specifiers or ‘...’ before ‘_llseek’
llseek.c:34: error: expected declaration specifiers or ‘...’ before ‘fd’
llseek.c:34: error: expected declaration specifiers or ‘...’ before ‘offset_high’
llseek.c:35: error: expected declaration specifiers or ‘...’ before ‘offset_low’
llseek.c:35: error: expected declaration specifiers or ‘...’ before ‘result’
llseek.c:36: error: expected declaration specifiers or ‘...’ before ‘origin’
llseek.c:50: warning: return type defaults to ‘int’
llseek.c: In function ‘_syscall5’:
llseek.c:52: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
llseek.c:68: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
llseek.c:34: error: parameter name omitted
llseek.c:34: error: parameter name omitted
llseek.c:34: error: parameter name omitted
llseek.c:35: error: parameter name omitted
llseek.c:35: error: parameter name omitted
llseek.c:36: error: parameter name omitted
llseek.c:93: error: expected ‘{’ at end of input
make[1]: *** [llseek.o] Error 1
make[1]: Leaving directory `/home/mans/test/util-linux-2.12r/fdisk'
make: *** [all] Error 1

I managed to find the a person with the same error but he did't get the message 

You don't have <uuid/uuid.h>
You don't have blkid

so I tried to compile it on a station with mandrive and it worked, but I did get the message 

You don't have <uuid/uuid.h>
You don't have blkid

but no errors when compiling.

If I look at the file llseek.c  I can't find the typedef of _llseek, fd or offset_high and I did grep for it 
in the dir of util-linux but nothing.

Dose anyone have any ides.

---

### Post by runningwithscissors on 2007-01-22
So, is there a uuid.h on your system?

I've looked up and it seems to be supplied by e2fsprogs. Consider getting the headers for e2fsprogs first and then check.

---

### Post by 25an on 2007-01-22
thanks for your replay and for taking up your time but i did not look hard enough I missed
the message 

you need -lcrypt

thanks any way.

---

### Post by Khyeron on 2008-04-20
I just stumbled on this as I just fixed my own error with a Debian Lenny box I have been playing with.  I had the same exact errors as you folks.

You DON'T really need -lcrypt (libcrypt -dev files) to check out (as per Jari Ruusu [http://osdir.com/ml/linux.cryptography/2007/msg00285.html](http://osdir.com/ml/linux.cryptography/2007/msg00285.html) ) but you DO need to 


"apt-get install uuid-dev zlib1g-dev"


to get zlib and blkid and zlib to check out.
**  I also installed libblkid-dev but I don't think it was necessary.

Hope that helps.  I know its a wee bit late of a bump.
PS - I would strongly suggest that if you intend to "play" that you have a dedicated "production" system, and a not so dedicated play system (test box).  Be willing to frag your test box at least once daily :)

---

