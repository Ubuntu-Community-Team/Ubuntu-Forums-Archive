---
title: "Where is dos2unix in Ubuntu 10.04?"
date: 2010-07-27
forum: Programming Talk
---

### Post by darrenleeweber on 2010-07-27
I've got a build system that requires 'dos2unix' and it's not available on Ubuntu 10.04 (to my knowledge).  I tried the following, without success.

```

$ uname -a
Linux XXX 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux
$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"
$ apt-cache search dos2unix
$ apt-file search dos2unix
$ apt-cache show tofrodos
$ sudo apt-get install tofrodos
$ apt-file list tofrodos
tofrodos: /usr/bin/fromdos
tofrodos: /usr/bin/todos
tofrodos: /usr/share/doc/tofrodos/NEWS.Debian.gz
tofrodos: /usr/share/doc/tofrodos/changelog.Debian.gz
tofrodos: /usr/share/doc/tofrodos/copyright
tofrodos: /usr/share/doc/tofrodos/readme.txt.gz
tofrodos: /usr/share/doc/tofrodos/tofrodos.html
tofrodos: /usr/share/man/man1/fromdos.1.gz
tofrodos: /usr/share/man/man1/todos.1.gz

```

Anybody know where to find 'dos2unix' and 'unix2dos'?  These utilities have been around by those names for a long time.  Why change the names (or remove symlinks with those names)?  Is this a good candidate for a feature request on tofrodos (tofromdos)?  Without this feature in the package, I used the following hack:

```

$ sudo ln -s /usr/bin/fromdos /usr/bin/dos2unix
$ sudo ln -s /usr/bin/todos /usr/bin/unix2dos

```

TIA,
Darren

---

### Post by dwhitney67 on 2010-07-27
Just install the 'tofrodos' package.
```

sudo apt-get install tofrodos

```

P.S.  dos2unix and unix2dos are sym-linked to the multi-binary (?) called 'fromdos'.

---

### Post by ghostdog74 on 2010-07-27
you can just make your own dos2unix()

```

dos2unix(){
  tr -d '\r' < "$1" > t
  mv -f t "$1"
}
dos2unix file

unix2dos(){
  sed -i 's/$/\r/' "$1"
}

unix2dos file

```

---

### Post by tiga2001 on 2010-12-15
> **dwhitney67 said:**
> 
P.S.  dos2unix and unix2dos are sym-linked to the multi-binary (?) called 'fromdos'.
Does anyone know why they changed the names of dos2unix to unix2dos? Is it just for philosophical reasons? (Like, since everyone except dos is using '\n' line endings, we shouldn't have "unix" in the command name). This was creating a lot of unnecessary problems. I tried searching the internet, but no one could give me an answer on why they changed the names, not even in the read-me files in the debian package.

---

### Post by dwhitney67 on 2010-12-15
[UNIX]("http://www.geek.com/articles/news/jury-says-novell-owns-unix-copyright-20100331/") is a copyrighted term.  When dos2unix and unix2dos exist under UNIX systems, there's not a conflict of interest; put it under Linux, and perhaps there is.

Also, Linux is not UNIX.  I suppose in lieu of fromdos, the binaries could have been called dos2linux and linux2dos.  :-)

---

### Post by tiga2001 on 2010-12-15
> **dwhitney67 said:**
> [UNIX]("http://www.geek.com/articles/news/jury-says-novell-owns-unix-copyright-20100331/") is a copyrighted term.  When dos2unix and unix2dos exist under UNIX systems, there's not a conflict of interest; put it under Linux, and perhaps there is.

Also, Linux is not UNIX.  I suppose in lieu of fromdos, the binaries could have been called dos2linux and linux2dos.  :-)
Wow, thanks for replying so quickly. I guess it does make sense for Canonical to avoid any lawsuits considering how much money has been spent battling for UNIX trademarks.

---

