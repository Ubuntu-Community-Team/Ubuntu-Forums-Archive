---
title: "How do I find out if getline is part of the c89 standard?"
date: 2011-03-07
forum: Programming Talk
---

### Post by audit on 2011-03-07
Is getline() part of the standard? More importantly how do I find out if something is part of the standard?

In c I tried to write a getline() function and I was not allowed because one seems to be already included in <stdio.h> (although I am not even sure of that). 

I looked for some documentation online and all I found was one reference for this function, but it left me wondering if it is part of the standard, or just something that was placed in gcc 4.4.5.

What I am interested in what is part of the c89 standard. I am using Codeblocks which I have never used before, maybe my problem is I need to set some flag to insure I am using the standard I want. 

All help especially links is appreciated.

Thanks

---

### Post by MadCow108 on 2011-03-07
its not even part of C99.

see the man page:
> CONFORMING TO
Both getline() and getdelim() were originally GNU extensions.  They were standardized in POSIX.1-2008.

besides manpages and google, the best source is of course the offical standard document.
unfortunately you usually have to pay for standards documents but drafts and preprints are often free.
purchase:
[http://infostore.saiglobal.com/store/Details.aspx?DocN=isoc000512954](http://infostore.saiglobal.com/store/Details.aspx?DocN=isoc000512954)

c89 draft (from [http://en.wikipedia.org/wiki/ANSI_C#C89):](http://en.wikipedia.org/wiki/ANSI_C#C89):)
[http://flash-gordon.me.uk/ansi.c.txt](http://flash-gordon.me.uk/ansi.c.txt)

C1x:
[http://www.open-std.org/JTC1/SC22/WG14/www/docs/n1425.pdf](http://www.open-std.org/JTC1/SC22/WG14/www/docs/n1425.pdf)

---

### Post by audit on 2011-03-07
Thanks for the reply, but I am not sure I understand what you mean by see man page

> 
see the man page:
Quote:
CONFORMING TO
Both getline() and getdelim() were originally GNU extensions. They were standardized in POSIX.1-2008. 

do you by any chance know off the top of your head which the gcc flag I use to limit myself to c89?

again thanks for the links.

---

### Post by MadCow108 on 2011-03-07
type in terminal: man getline


to restrict to c89:
```
gcc -std=c89 -pedantic-errors
```
or equivalent (+limits to c++98 if used)
```
gcc -ansi -pedantic-errors
```
for warnings instead of errors use -pedantic
see *Options Controlling C Dialect* in man gcc

but this only affects the language and not library extensions like getline.

---

### Post by nvteighen on 2011-03-07
Usually, the man page has a section where it tells what standards the said function conforms to. You'll usually find it at the bottom.

---

