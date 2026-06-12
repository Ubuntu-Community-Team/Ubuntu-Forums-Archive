---
title: "Crosscompiler for Pascal"
date: 2005-05-19
forum: Programming Talk
---

### Post by Kimm on 2005-05-19
does anyone know of a crosscompiler (for Linux to make Windows Binaries) for Pascal? I need it for my Delphi class, I was trying to emulate Delphi 3 in wine but it will not work and Kylix does not have the libraries I need.

I need help fairly fast so if anyone can help I would realy apretiate it!!!!

---

### Post by poster_nutbag on 2005-05-19
Have you looked at [Free Pascal](http://www.freepascal.org/) at all?

---

### Post by Kimm on 2005-05-21
I hadnt, but I didnt know it was a crosscompiler...
I'm having some trubble with it though, I need to use win32 libraries so ofcourse I need to compile to a win32 binary, but it doesnt seem to work, this is the error message I get when running "fpc -Twin32 test.pas" (and "fpc test.pas -Twin32"):

```

Fatal: Can't find unit System
Error: Compilation aborted
Error: /usr/bin/ppc386 returned an error exitcode (normal if you didnt specify a source file to be compiled)

```

Can anyone help? btw, this would be how the source file looks:

```

program test;

begin
 writeln('Hello win32 World...');
end.

```

and it compiles nicely without the "-Twin32" argument

---

