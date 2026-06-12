---
title: "std io still confusing.."
date: 2005-06-20
forum: Programming Talk
---

### Post by kimes on 2005-06-20
hi.. I'm newbie linux programmer. so I'm still confused in std IO. 
I made simple demo programming which just gets every input from stdin and print out to stdout.. I think I dont need to post it. You can imagine it right? (gets/puts in loop)

Anyway let the program name be 'stdiodemo'

when I executed like this
echo 123 | ./stdiodemo
It printed out 123 that's what I wanted..
'echo 123's stdout is redirected to my demo program.

But my question.. How can I redirect stderr to stdin without redirecting stdout to stdin?

Is all my questions clear?
Thanks in advance..

---

### Post by intangible on 2005-06-20
So you want the program to only get STDERR huh?

Try this:
**ls -e 2>&1 1>/dev/null|less**
As you can see, only the error message for the invalid argument gets piped to less.

If you try this:
**ls -l 2>&1 1>/dev/null|less**
You see nothing because -l is a valid argument so there is no STDERR and you are redirecting STDOUT to /dev/null

**2>&1** redirects STDERR to STDOUT
**1>/dev/null** redirects STDOUT to /dev/null

**1>&2** would redirect STDOUT to STDERR

Hope this helps.

---

### Post by kimes on 2005-06-20
[QUOTE=intangible]So you want the program to only get STDERR huh?

Try this:
**ls -e 2>&1 1>/dev/null|less**
As you can see, only the error message for the invalid argument gets piped to less.

If you try this:
**ls -l 2>&1 1>/dev/null|less**
You see nothing because -l is a valid argument so there is no STDERR and you are redirecting STDOUT to /dev/null

**2>&1** redirects STDERR to STDOUT
**1>/dev/null** redirects STDOUT to /dev/null

**1>&2** would redirect STDOUT to STDERR

Hope this helps.[/QUOTE]
 Thanks this helps a lot..
But.. I'm still not sure the syntax like above '2>&1'..
Can I get the full references..?

---

### Post by desdinova on 2005-06-20
[http://www.linuxcommand.org/lts0060.php](http://www.linuxcommand.org/lts0060.php)

---

### Post by LordHunter317 on 2005-06-20
Read the bash manpage for the full details on the redirects it supports.

For details on maniuplating them programatically, get a good UNIX programming book and look at the dup2 system call.

Also, **using gets()/puts() is *extremely* bad practice and you shouldn't do it**.

---

