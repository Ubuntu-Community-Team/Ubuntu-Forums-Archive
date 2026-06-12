---
title: "Anyone familiar with Bison Debug mode?"
date: 2007-08-03
forum: Programming Talk
---

### Post by SNYP40A1 on 2007-08-03
I made a parser using Bison which compiles and used to run fine, but after I added a new grammar feature, it compiles, but does not run like I expect.  I want to use the Bison debug mode, but I am a bit confused by one of the instructions to enable debug mode:

"Once you have compiled the program with trace facilities, the way to
request a trace is to store a nonzero value in the variable `yydebug'.
You can do this by making the C code do it (in `main', perhaps), or you
can alter the value with a C debugger."

[http://www.cs.cmu.edu/cgi-bin/info2www?(bison.info)Tracing](http://www.cs.cmu.edu/cgi-bin/info2www?(bison.info)Tracing)

What does that mean?  I do not have a variable called yydebug in my main() function.  Am I supposed to create one and assign some non-zero value to it?  Has anyone debugged in Bison before?  How do I enable debug mode?

---

### Post by duff on 2007-08-03
before you call yyparse():
```
extern int yydebug;
yydebug = 1;
```

and when you run bison:
```
# bison --debug parser.y
```

---

