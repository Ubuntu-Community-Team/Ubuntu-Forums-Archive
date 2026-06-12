---
title: "tar wildcard question"
date: 2013-11-09
forum: New to Ubuntu
---

### Post by comediancannon on 2013-11-09
I'd like to create a new archive with files

example1.txt
example2.txt
example3.txt

How do I create the archive using a wildcard and leaving example3.txt out?

Thanks

---

### Post by BrunoLotse on 2013-11-09
Hi:) I would do like this```
tar cvf example.tar --exclude *3.txt *
```Try```
 man tar 
```Cheers,Bruno

---

### Post by steeldriver on 2013-11-09
If you really want to use globbing for some reason, you can enable the shell's extended globbing (extglob) feature and use the !(3) ("not 3") pattern

```

$ tar cvf examples.tar example*.txt
example1.txt
example2.txt
example3.txt
$ 
$ shopt -s extglob
$ tar cvf examples.tar example**!(3)**.txt
example1.txt
example2.txt

```

---

### Post by drmrgd on 2013-11-09
> **steeldriver said:**
> If you really want to use globbing for some reason, you can enable the shell's extended globbing (extglob) feature and use the !(3) ("not 3") pattern

```

$ tar cvf examples.tar example*.txt
example1.txt
example2.txt
example3.txt
$ 
$ shopt -s extglob
$ tar cvf examples.tar example**!(3)**.txt
example1.txt
example2.txt

```

Question for you: when do you need to explicitly turn on extglob?  I've been using the '!()' pattern for a while now (in fact, though about posting that very same thing to this thread earlier!), but I've never explicitly turned on extglob.  I didn't even know I had to do that, but I had a quick look at Greg's Wiki, and according to that:

> 
In addition to the traditional globs (supported by all Bourne-family shells) that we've seen so far, Bash (and Korn Shell) offers extended globs, which have the expressive power of regular expressions. Korn shell enables these by default; in Bash, you must run the command:
```

shopt -s extglob

```


Using the same idea, this works for me without the extglob option:

```

$ ls
example1.txt  example2.txt  example3.txt


[ dave@CygnusX1: ~/sandbox/tar ] $ tar cvf test.tar !(*3.txt)
example1.txt
example2.txt


[ dave@CygnusX1: ~/sandbox/tar ] $ tar tvf test.tar 
-rw-rw-r-- dave/dave         0 2013-11-09 13:11 example1.txt
-rw-rw-r-- dave/dave         0 2013-11-09 13:11 example2.txt

```

I had a quick search through .bashrc, .profile, etc., and I can't find any evidence it's been turned on by default in there, but I also don't know where to look to find the default options that are turned on.  Do you know why this works for me without having to turn on extglob, and / or how to find out what options are turned on in the current session?

---

### Post by steeldriver on 2013-11-09
Oops it seems you are correct, it does seem to be enabled by default. You can see the current settings using 'shopt' without arguments

```

$ shopt | grep ext
extdebug        off
extglob         on
extquote        on

```

and since not even /etc/bash.bashrc nor /etc/skel/.bashrc mention it, I guess it's compiled in ? I don't really know

```

$ grep shopt /etc/bash.bashrc
shopt -s checkwinsize
#if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
$ 
$ grep shopt /etc/skel/.bashrc
shopt -s histappend
shopt -s checkwinsize
#shopt -s globstar

```

---

### Post by BrunoLotse on 2013-11-09
Hi:)```
shopt  | grep extglob
```Cheers,Bruno

Oops. It's already there. Racing....

---

### Post by drmrgd on 2013-11-09
> **steeldriver said:**
> Oops it seems you are correct, it does seem to be enabled by default. You can see the current settings using 'shopt' without arguments

```

$ shopt | grep ext
extdebug        off
extglob         on
extquote        on

```

and since not even /etc/bash.bashrc nor /etc/skel/.bashrc mention it, I guess it's compiled in ? I don't really know

```

$ grep shopt /etc/bash.bashrc
shopt -s checkwinsize
#if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
$ 
$ grep shopt /etc/skel/.bashrc
shopt -s histappend
shopt -s checkwinsize
#shopt -s globstar

```

That's very informative!  It's also interesting because everything I look at says that extglob is not enabled by default in Bash.  I can't seem to find what controls these options, but at least now I know that:

[LIST=1]
[*]It's enabled by default
[*]How to look to see what options are currently configured in my shell.
[/LIST]

Once again, I learned something very useful from you!

---

### Post by BrunoLotse on 2013-11-09
Hi:)```
shopt | less
```Cheers,Bruno

---

### Post by sisco311 on 2013-11-09
It seams that in GNU Bash 4.2 extglob is enabled by default in interactive shells. If I remember it correctly this wasn't the case in earlier versions.

In non-interactive shells/scripts it's still disabled by default:
```

[sisco@acme ~]$ shopt extglob 
extglob            on
[sisco@acme ~]$ bash -c 'shopt extglob'
extglob            off

```

---

