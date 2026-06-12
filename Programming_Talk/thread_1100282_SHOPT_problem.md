---
title: "SHOPT problem"
date: 2009-03-19
forum: Programming Talk
---

### Post by umshiva on 2009-03-19
Hi Experts,

I am using a RHEL-5 sys. I use ksh for my shell programming

When i use echo " hai \c " in k shell .. the escape sequence is printed as it is

But i found from Google that echo -e would serve the purpose ...

Morover in Bash there is a command shopt which can be used , so all escape sequences are expanded by default

I dont want to use echo -e as there are are 1000+ scripts to change

is thr any other way that we can enable this facility in K shell ?

Please suggest ..

Thanks in advance
Shiva

---

### Post by ghostdog74 on 2009-03-19
without going into what shells to use, you want to explain again what you want to do? how do you want to change the files? show examples.

---

### Post by umshiva on 2009-03-19
> **ghostdog74 said:**
> without going into what shells to use, you want to explain again what you want to do? how do you want to change the files? show examples.

Hi... 
In unix.... echo "hi\c" outputs like "hi" and suppresses the newline char so that cursor remains in the same line.

If the same is given in Redhat Enterprise Linux version 5... the same echo outputs like hi\c  ...  that is the escape sequence is not expanded but treated as some char...

I'm using K Shell in both unix and linux.

This issue could be solved by giving -e as argument to echo like echo -e "hi\c" ... I have many scripts with these sequences and it's not possible to change every script.. 

"SHOPT -s xpg_echo" could be used to change the echo behaviour to expand the escape sequences by default ... but this is available only in bash shell in Linux... and not available in K shell... 

Is there any similar option available for this in linux k shell..

Hope this explanation gives you a bigger picture :)

If you knew it and if possible , please help .

Thanks in advance.

---

### Post by ghostdog74 on 2009-03-19
use printf instead of echo. printf is more portable.

---

### Post by geirha on 2009-03-19
From what I can tell based on the man-page of ksh [http://manpages.ubuntu.com/manpages/gutsy/man1/ksh93.1.html](http://manpages.ubuntu.com/manpages/gutsy/man1/ksh93.1.html), ksh's echo is very rudimentary and does not handle options or escape sequences at all. Instead, it calls the system's echo command if an option or escape sequence is given, and linux's echo command needs the -e option to interpret escapes. I'm guessing /bin/echo on the other unix system interprets escapes by default.

One option could be to add an alias in ksh's rc/profile file on
```
alias echo='echo -e'
```
Another option could be to make a shell script at /usr/local/bin/echo:
```
#!/bin/sh
exec /bin/echo -e "$@"

```
/usr/local/bin is before /bin in $PATH in ubuntu by default, probably in rhel too.

bash and dash has builtin versions of echo that accept options, and so bash and dash scripts should not be affected by that echo script. Don't know what rhel uses as /bin/sh though, in ubuntu it is dash.

---

### Post by slavik on 2009-03-19
1. Echo is built in to shells ... Definately so in bash and ksh. /bin/echo will actually run the echo binary. Echo will just use the shell's built in.

2. Echo -n will not output the new line.

---

