---
title: "[SOLVED] vim syntax highlighting 7.10"
date: 2007-11-28
forum: Programming Talk
---

### Post by 65 mustang on 2007-11-28
In all the treads i have found i see you are supposed to uncomment
```
syntax on
``` in
/etc/vim/vimrc

This makes vim print out an error at start up:
```
vim server.c 
Error detected while processing /usr/share/vim/vimrc:
line   20:
E319: Sorry, the command is not available in this version: syntax on
Press ENTER or type command to continue

```

help?

---

### Post by LaRoza on 2007-11-28
```

sudo aptitude install vim-full

```

Ubuntu has vim-tiny.

---

### Post by 65 mustang on 2007-11-28
That worked!  Thank you!

Steps to fix this are:
[LIST=1]
[*]**Install Vim full**
```
sudo aptitude install vim-full
```
[*]**Turn Syntax highlighting on**
```
sudo vi /etc/vim/vimrc
``` 
change (uncomment)
```
"syntax on
```
to
```
syntax on
```
[/LIST]

---

### Post by Compyx on 2007-11-29
You shouldn't alter the system-wide vimrc, but instead create a file ".vimrc" in your home directory and put the commands you need there.

---

### Post by dwhitney67 on 2007-11-29
> **Compyx said:**
> You shouldn't alter the system-wide vimrc, but instead create a file ".vimrc" in your home directory and put the commands you need there.
Agreed... however like countless other developers have found, it doesn't make one iota of a difference unless you have the "full" vim installed.

P.S. <snip>

---

### Post by sujoy on 2007-11-29
> **dwhitney67 said:**
> Agreed... however like countless other developers have found, it doesn't make one iota of a difference unless you have the "full" vim installed.

could you please explain, what difference does it make with "full" vim installed? 

cause I just edited the same ...:confused:

---

### Post by LaRoza on 2007-11-29
> **sujoy said:**
> could you please explain, what difference does it make with "full" vim installed? 

cause I just edited the same ...:confused:

> 
Vi IMproved - enhanced vi editor - compact version 
Vim is an almost compatible version of the UNIX editor Vi.

Many new features have been added: multi level undo, syntax
highlighting, command line history, on-line help, filename
completion, block operations, folding, Unicode support, etc.

This package contains a minimal version of vim compiled with no
GUI and a small subset of features in order to keep small the
package size. This package does not depend on the vim-runtime
package, but installing it you will get its additional benefits
(online documentation, plugins, ...).


> 
Vi IMproved - enhanced vi editor - full fledged version
Vim is an almost compatible version of the UNIX editor Vi.

Many new features have been added: multi level undo, syntax
highlighting, command line history, on-line help, filename
completion, block operations, folding, Unicode support, etc.

This package contains a version of vim compiled with support for
the GNOME2 GUI and scripting support for Perl, Python, Ruby, and
TCL.


Go to Synaptic Package Manager, and you will see many optional features for Vim, Vim tiny is just the barest and lightest, but is only useful for basic text editing.

Vim is on every *nix, and is standard. Where ever you go, Vim is there.

---

### Post by LaRoza on 2007-11-29
>Agreed... however like countless other developers have found, it doesn't make one iota of a difference unless you have the "full" vim installed.

As much as I dislike the Vim default installation, Ubuntu wasn't designed for programmers specifically but for a wide range of users. Most distributions I have used have the "build-essential" type package and have Vim in all its glory. It is a bit of a hastle installing these (along with Java, Ruby, NASM, and others), it is not a real knock against Ubuntu. They only have a CD to work with.

[http://www.ubuntu.com/](http://www.ubuntu.com/)

---

### Post by dwhitney67 on 2007-11-29
LaRoza

I agree with you... they only have a CD to work with.  Why?????????

Most other worthy distros provide the means for prospective users to download a DVD ISO, or multiple CD ISOs.  Why is Ubuntu different?

Are they (Canonical) trying to placate those who have 5-year old computers, which don't have a DVD-ROM drive?  There is sooooo much free/open-source software that it can't possibly fit on a single CD.

Recently I was asked for my recommendation for a distro for the office to use for development purposes.  I thought of Ubuntu because it is simple for non-savant user to operate with, however when I considered the hassle of upgrading the basic system with the tools necessary to perform "serious" software development, I leaned towards Fedora.

I've been using Linux since 1997, and I have never found a more pitiful distro ("out of the box") than Ubuntu for doing s/w development.  For web-browsing, multi-media purposes, email, perhaps it is fine.  But for legitimate purposes of assisting me in making a buck or two (as a s/w engineer) to put food on the table, forget it.

---

