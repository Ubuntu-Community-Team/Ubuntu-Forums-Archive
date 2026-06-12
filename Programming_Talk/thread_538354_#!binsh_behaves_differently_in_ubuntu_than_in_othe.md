---
title: "#!/bin/sh behaves differently in ubuntu than in other linuxes???"
date: 2007-08-29
forum: Programming Talk
---

### Post by jf/ on 2007-08-29
hi, as per subject. I'm pretty used to /bin/sh behaving the way it's always behaved for me when it comes to shell scripts, so I was pretty surprised when I transported a script over from another distro to ubuntu.

Look at the error it gave me...

```
[: 5: ==: unexpected operator
```

and this is the line that triggered it - if I change the double '==' to a single '=', it works out ok instead...

[html]
if [ "$?" == "0" ]; then
[/html]

(sorry about wrapping it in "html", but the "code" handler does not handle the \[, \] brackets properly...)

I'm just wondering, though - is this the proper way sh is supposed to behave ("like true sh"), or is this because /bin/sh is linked to (????) /bin/dash, or...?

---

### Post by jf/ on 2007-08-29
(pls ignore this post - double post due to problem with forum software. How do I delete this post???)

---

### Post by finer recliner on 2007-08-29
do this:
```

$file /bin/sh

```

sh is a symbolic link (like a shortcut in windows) this command will tell you where /bin/sh is pointing to. mine points to bash, however i think the default for ubuntu is now dash. there are LOTS of different shells, so in your shabang line i would point to a specific shell (i.e bash, dash, tcsh, csh...etc)  instead of a OS's default (because different distros of linux use different default shells).

EDIT: oops i half-misread your question. /bin/sh is what shell scripts can use in the shabang line if they want to use an linux distro's default shell script (because you can install more that one). be carefull if you change where it points, because this can break some of the shell scripts that rely on it.

---

### Post by yabbadabbadont on 2007-08-29
```
sudo dpkg-reconfigure dash
``` Answer 'No' when asked if you want it to be the default shell.  This solves a great many problems with script compatibility.

---

### Post by jf/ on 2007-08-29
> **yabbadabbadont said:**
> ```
sudo dpkg-reconfigure dash
``` Answer 'No' when asked if you want it to be the default shell.  This solves a great many problems with script compatibility.

hm... thanks!!! POSIX - I didn't know bash wasn't POSIX-compliant (or rather, '=='!!?)... I've always thought that (and 'man bash' confirms it???) that bash, when called as 'sh' will be posix-compliant??? from man bash -

```
If bash is invoked with the name sh, it tries to mimic the startup behavior of historical versions
of sh as closely as possible, while conforming to the POSIX standard as well.
```

and then further along in the same paragraph:

```
When invoked as sh, bash enters posix mode after the startup files are read.
```

---

### Post by jf/ on 2007-09-02
> **jf/ said:**
> hm... thanks!!! POSIX - I didn't know bash wasn't POSIX-compliant (or rather, '=='!!?)... I've always thought that (and 'man bash' confirms it???) that bash, when called as 'sh' will be posix-compliant??? from man bash -

```
If bash is invoked with the name sh, it tries to mimic the startup behavior of historical versions
of sh as closely as possible, while conforming to the POSIX standard as well.
```

and then further along in the same paragraph:

```
When invoked as sh, bash enters posix mode after the startup files are read.
```

anybody any comments?

---

### Post by nanotube on 2007-09-03
it's not that bash isn't posix compliant - it's that dash isn't. 
by default (since edgy), /bin/sh points to /bin/dash, not to /bin/bash (for whatever reasons they thought up...)

so, you can either reconfigure /bin/sh to point to bash, or start your shell scripts explicitly with 
```
#!/bin/bash
```

---

### Post by jpkotta on 2007-09-03
> **nanotube said:**
> it's not that bash isn't posix compliant - it's that dash isn't. 
by default (since edgy), /bin/sh points to /bin/dash, not to /bin/bash (for whatever reasons they thought up...)


Bash is very large and slow for a shell.  If you're running many short scripts in succession (e.g. boot or running a configure script), you are better off using a small, minimal shell.  Bash is still much better for interactive use or more sophisticated programs like abcde (abcde is a CD ripper implemented in Bash).  Thus they switched to Dash as /bin/sh because it's smaller and faster, and all system scripts and portable scripts are *supposed* to be in Bourne shell language.

Anyway, I think the problem is that when bash is invoked as /bin/sh, it doesn't go into Bourne shell mode.  Bash runs Bourne shell scripts just fine, because Bash language is a superset of Bourne language.  Obviously it doesn't work the other way around.  Dash only understands Bourne shell language.  So Bash should act like Bourne shell if invoked as /bin/sh, but instead it acts like Bash, and is too permissive.

Edit: To clarify, your script was wrong, but you got away with it because Bash didn't tell you.  The fact that it is POSIX compliant means that it will do what the specification says it must, and possibly more if the spec doesn't forbid it.

---

### Post by Ramses de Norre on 2007-09-03
> **jf/ said:**
> [html]
if [ "$?" == "0" ]; then
[/html]

Are you sure you don't want this: ```
if [ $? == 0 ]; then
```
Your line turns the numbers into strings because of the quotes and will compare them on length. I think you want to check if the two variables have the same integer value and if so you don't want those quotes.

---

### Post by cwaldbieser on 2007-09-03
> **Ramses de Norre said:**
> Are you sure you don't want this: ```
if [ $? == 0 ]; then
```
Your line turns the numbers into strings because of the quotes and will compare them on length. I think you want to check if the two variables have the same integer value and if so you don't want those quotes.

Are you sure?
```

$ [ "1" == "0" ]
$ echo $?
1

```
When I execute the above interactively, test returns 1.  If test was comparing string lengths, shouldn't it return 0?

The bash manual says the following about the == operator
> 
When  the  == and != operators are used, the string to the right
              of the operator is considered a pattern and matched according to
              the  rules described below under Pattern Matching.  If the shell
              option nocasematch is enabled, the match  is  performed  without
              regard  to  the case of alphabetic characters.  The return value
              is 0 if the string matches (==) or does not match (!=) the  pat-
              tern, and 1 otherwise.  Any part of the pattern may be quoted to
              force it to be matched as a string.


---

### Post by Jessehk on 2007-09-03
```

if [ $? -eq 0 ]; then
...
fi

```

---

### Post by Ramses de Norre on 2007-09-03
> **cwaldbieser said:**
> Are you sure?
```

$ [ "1" == "0" ]
$ echo $?
1

```
When I execute the above interactively, test returns 1.  If test was comparing string lengths, shouldn't it return 0?

The bash manual says the following about the == operator

I think I did conclude that string-length thing to fast, it looks like I was wrong :)

---

### Post by ssam on 2007-09-03
as i understand bash and dash are both POSIX compliant. the problem is that many scripts use bash features beyond the POSIX stuff.

a script starting with
```

#!/bin/sh

```

should be writen to run on any shell, but to many people only test with bash.

see [https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)

---

