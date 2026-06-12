---
title: "Can some one help with my SquidGuard upgrade, please?"
date: 2006-06-20
forum: Programming Talk
---

### Post by krunkite on 2006-06-20
:confused: 
Hi! Wonder if someone can throw some light on what I've missed....
I started off this morning attempting to upgrade my version of squidguard, from version 1.2.0 to 1.2.10. I also decided to upgrade my version of sleepycat's berkeley DB from v3.2 to 4.4.2.
I thought I should have the latest....yeah, I'm probably a dumb whatjamacallit!

That's all so simple, so far.
Anyway, I followed the instructions I have on this useful squidguard help site
[http://www.maynidea.com/squidguard/step-by-step.html]("http://www.maynidea.com/squidguard/step-by-step.html")
Squidguard.org being out of date!

Everything was okay. I navigated to my source directory and entered this code:

[COLOR="DarkRed"][FONT="Fixedsys"]./configure --prefix=/usr/local/squidguard --datadir=/usr/share --sysconfdir=/etc --localstatedir=/var --infodir=/usr/lib/dpkg/info --mandir=/usr/share/man --with-sg-config=/etc/squid/squid.conf --with-sg-logdir=/var/log/squid --with-sg-dbhome=/var/lib/squidguard --with-db=/usr/local/BerkeleyDB.4.4  --with-db-lib=/var/lib/squidguard/ --with-sg-dbhome=/var/lib/squidguard/db/weapons[/FONT][/COLOR]


This was the outcome:

[COLOR="DarkRed"][FONT="Fixedsys"]checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking whether make sets $(MAKE)... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for bison... no
checking for byacc... no
checking for flex... no
checking for lex... no
checking for yywrap in -lfl... no
checking for yywrap in -ll... no
checking for lynx... false
checking for perl... /usr/bin/perl
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for unistd.h... (cached) yes
checking db.h usability... yes
checking db.h presence... yes
checking for db.h... yes
checking regex.h usability... yes
checking regex.h presence... yes
checking for regex.h... yes
checking for ldap_init in -lldap... no

LDAP library not found
[/FONT][/COLOR]


If ldap is the problem, and it is installed (unconfigured though it is), how do I change things with a workaround?

I appear to be unable to proceed beyond this point with any of these:

1) make - I get : [COLOR="DarkRed"][FONT="Fixedsys"]make: *** No targets specified and no makefile found.  Stop.[/FONT][/COLOR]

2) make install

3) make clean - I get: [COLOR="DarkRed"][FONT="Fixedsys"]make: *** No rule to make target `clean'.  Stop.[/FONT][/COLOR]

4) make test - I get: [COLOR="DarkRed"][FONT="Fixedsys"]make: Nothing to be done for `test'.[/FONT][/COLOR]

I looked in the source folder and can't find a makefile](*,) 

Any ideas? :confused:

---

### Post by nanotube on 2006-06-20
why not try to install ldap? not sure, but maybe packages "libldap2" and "libldap2-dev" will do the trick? then try your ./configure again.

---

### Post by krunkite on 2006-06-22
> why not try to install ldap? not sure, but maybe packages "libldap2" and "libldap2-dev" will do the trick? then try your ./configure again.

Thanx 4 the tip!

The original error is no longer thrown up.

I installed the ldap and libldap2 as suggested. They were definitely missing. However, after cleaning up the original compilation I tried it again.
A new problem came up.

Couldn't locate db.h! The file existed but squidguard couldn't locate it some how...... I do have a fix for this issue, for next time.

By default the db-tools are located in /usr/local/BerkeleyDB.4.x/bin/. 

I found this neat little trick from someone, somewhere [COLOR="Red"]**(I apologise to the donor who's name or website from whence I borrowed valued text I can't recall)**[/COLOR]. He suggested making symlinks so that the binaries reside in their default locations. To do this enter, 

> [COLOR="DarkRed"]Code:

# ln -s /usr/local/BerkeleyDB.4.x/bin/db_archive /usr/local/bin/db_archive
# ln -s /usr/local/BerkeleyDB.4.x/bin/db_archive /usr/bin/db_archive[/COLOR]

...and this for every binary in /usr/local/BerkeleyDB.4.x/bin/

[COLOR="Black"][COLOR="darkred"]> It may be necessary to manually adjust the  libraries from a *deb install. Code:[/COLOR]

[COLOR="DarkRed"]# ln -s /usr/local/BerkeleyDB.4.x/bin/include/db.h /usr/include/db.h
# ln -s /usr/local/BerkeleyDB.4.x/include/ /usr/local/include/db4/
# ln -s /usr/local/BerkeleyDB.4.x/lib/ /usr/local/db.h[/COLOR][/COLOR]

The first symlinks is for the db.h file. Replaces the old symlink with the new one.

[COLOR="Red"]The second and third allows the configure script of LDAP to find the right 'include' files and libraries.[/COLOR]

[COLOR="Black"][COLOR="DarkRed"]Update ld.so.conf & ld.so.cache with code:[/COLOR]

[COLOR="DarkRed"]# ldconfig[/COLOR][/COLOR]

I've had to start from scratch on a different PC so I'll keep you posted.:-k

---

