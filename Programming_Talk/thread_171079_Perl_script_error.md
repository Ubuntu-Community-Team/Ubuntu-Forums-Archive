---
title: "Perl script error"
date: 2006-05-05
forum: Programming Talk
---

### Post by Riona on 2006-05-05
Trying to run my first perl script and having trouble.
Here is my program the usual hello world.
#! /usr/bin/perl
print "Hello, World!\n";

the program works fine if i type in perl hello.pl
i get the output Hello, World!
But If i do chmod +x hello.pl
then type hello.pl I get the error 
bash: hello.pl: command not found


I have no idea how to get this working.  Suggestions please thanks.

---

### Post by yaaarrrgg on 2006-05-05
you probably want to type:

./hello.pl

if you are executing a script, you have to tell it it's in the current directory.

---

### Post by Jessehk on 2006-05-05
```

./hello.pl

```

the **./** tells bash that you are trying to execute something in the current directory. :)

---

### Post by Riona on 2006-05-05
Thanks that worked. I'll have to remember to do that in the future.

---

### Post by unbuntu on 2006-05-06
If you want to know the reason to prepend "./" is that bash doesn't have the current directory (.) in its searching path (aka $PATH), which is weird if you come from a Windows background.

---

### Post by shawnhcorey on 2006-05-07
[QUOTE=unbuntu]If you want to know the reason to prepend "./" is that bash doesn't have the current directory (.) in its searching path (aka $PATH), which is weird if you come from a Windows background.[/QUOTE]

Not weird, this is a security issue. If ./ is in your path, make sure it's the last item:

PATH="$PATH:."

If not, you could be running a local command instead of the one you expect. For example, if I put a script called 'ls' in a project directory, then whenever you're working on that project, you would run my command and not '/bin/ls'. Since my program is now running under your useid, I could do all sorts of nasty things.

So, if you're paranoid, do not add '.' to your PATH.

shc

---

