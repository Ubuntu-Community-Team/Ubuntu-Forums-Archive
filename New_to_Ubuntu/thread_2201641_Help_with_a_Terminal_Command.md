---
title: "Help with a Terminal Command"
date: 2014-01-25
forum: New to Ubuntu
---

### Post by dave2001 on 2014-01-25
I'm was troubleshooting another issue when this came up.

I found a website with a suggested solution for my problem, but it contains a terminal command I'm not familiar with, and it apparently has no man-page. I'm wondering if this means it's not actually a terminal command, but some kind of executable?  Some googling didn't really get me a concrete answer, but I gathered it's something like the "ls" (list) command. Anyway, not a big problem, I just like to understand what a terminal command does before I use it, both for safety and because I enjoy learning about linux.

The command is ```
~$ ll 
```

just two lower case L's 

It's being used in the following context
```
~$ ll /dev/disk/by-partuuid
```

---

### Post by Lars Noodén on 2014-01-25
It's an alias.

```

alias ll
alias

```

*alias* is a built-in capability in bash.  If you dig deep in the manual page for bash, you can find a description of it and other built-in capabilities.  It's useful for making shortcuts for long, but frequently used, commands.  It's down in the section on 'shell builtin commands'

```

man bash

```

---

### Post by Impavidus on 2014-01-25
Usually ll is short for ls -l. An alias indeed.

---

### Post by dave2001 on 2014-01-26
Thanks for the responses, I appreciate it!

Seems like enough commands are already "abbreviated" to an obfuscating degree... and now your telling me some of them also have aliases? *facepalm* :D

---

### Post by Dave_L on 2014-01-26
Another piece of trivia is that "ll" is not always defined. If you "ssh" to a remote server, sometimes you have to tediously type the full "ls -l". :)

---

### Post by DuckHook on 2014-01-26
> **dave2001 said:**
> ... and now your telling me some of them also have aliases?...well... they exist strictly for the user's benefit. You don't have to use them.

Short history:

*nix programmers are a lazy lot (lazy like a fox), so whenever possible, they invent shortcuts that can cut keystrokes. Aliases are an example of this sort of constructive laziness. Instead of having to type *ls -l* all the time, an alias is defined (only in some distros) so that a simple *ll* substitutes for *ls -l*. Admittedly, this specific alias is a rather lame one, but the following one may make a little more sense. I run a multitude of VMs in VirtualBox and must often check their virtual driver version with the command:```
modinfo vboxguest | grep -iw version
```By defining the alias *vbinf* for this string of commands, I not only save a lot of keystrokes, but also the need to remember the exact command string for something I don't use that frequently. For really long convoluted command strings, it's a godsend.

---

### Post by Habitual on 2014-01-26
```
type -f ll 
```
or
```
alias ll
```

---

### Post by The Cog on 2014-01-26
Just enter the command alias to see all the aliases currently defined.

---

