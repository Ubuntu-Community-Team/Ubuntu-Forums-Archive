---
title: "Ubuntu Shell Commands &amp; Scripting"
date: 2013-08-09
forum: New to Ubuntu
---

### Post by varun2 on 2013-08-09
An absolute newbie question.
Is the shell commands/scripting syntax the same between other distros of Linux especially like RH and Ubuntu ?
Or Ubuntu's shell commands/scripting varies greatly ?

---

### Post by DuckHook on 2013-08-09
There are variations. Not greatly but enough to give a newbie fits (been there, done that). The reality is that Linux is a hacker's OS. It's great strength is that it isn't beholden to a single imperial force. The drawback is that different distros are free to do things differently.

Many scripts for Ubuntu won't work on Fedora. You are asking specifically about commands and syntax. Syntax is more universal, but commands are problematic. Example: Fedora doesn't use *apt* at all.

---

### Post by capscrew on 2013-08-10
> **DuckHook said:**
> There are variations. Not greatly but enough to give a newbie fits (been there, done that). The reality is that Linux is a hacker's OS. It's great strength is that it isn't beholden to a single imperial force. The drawback is that different distros are free to do things differently.

Many scripts for Ubuntu won't work on Fedora. You are asking specifically about commands and syntax. Syntax is more universal, but commands are problematic. Example: Fedora doesn't use *apt* at all.

Huh?????

The shell is distro agnostic.  There are  many shells available for use on any Linux style distro.  Some of them are: Bourne Shell (sh), Bourne-Again Shell (bash), Debian Almquist Shell (dash),C Shell (csh), TENEX C Shell (tcsh), and Z Shell (zsh).  There are internal commands and externally written scripts for each shell.  Some of these shells are incompatible, so scripts written in one may not work in others.  

> varun2]
Is the shell commands/scripting syntax the same between other distros of Linux especially like RH and Ubuntu ?
Or Ubuntu's shell commands/scripting varies greatly ? 

The Ubuntu default shell is  *dash*.  This is basically comparable with *bash * which is somewhat compatible with the original UNIX shell *sh *(Bourne).  All of this is to say, the shell is not Ubuntu specific.  As I said, the Ubuntu system uses *dash*.  The default user shell however is *bash*.  You can check which shell you are using with this command```
echo $SHELL
```

You can read a bit about the default shells with the built in manual like this```
man <shell>
```...where <shell> is either *dash*, *bash* or *sh*.  The man page for sh is really dash, but you can find plenty of information about the original Bourne Shell on the Internet.  You would have to install the other shells to read their man pages.  Of course, you can search the Internet for more information on all of the shells mentioned above.

---

### Post by prodigy_ on 2013-08-10
> **capscrew said:**
> The shell is distro agnostic.
Shells are distro agnostic but configuration files aren't. Pretty much any complex script written for a specific distro needs to be rewritten to a certain degree if you move to a different distro.

Bash syntax is the same everywhere (though, depending on bash version, certain constructs may or may not work) but available packages vary. Moreover, even what looks like the same command may not be exactly the same. For example, **nc** can be GNU netcat, netcat-bsd or ncat.

So **which** and **man** commands are always your friends when you deal with an unfamiliar distro.

---

