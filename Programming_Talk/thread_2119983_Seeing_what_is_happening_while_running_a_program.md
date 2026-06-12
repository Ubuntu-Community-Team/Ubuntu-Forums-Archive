---
title: "Seeing what is happening while running a program"
date: 2013-02-25
forum: Programming Talk
---

### Post by cristo-father on 2013-02-25
Is there any way to, while executing a pascal or C program, see all the variables that are changing, when they change, how many times loops occur etc
I would really like something that is advanced that fits this description, since it would be helpful when creating programs in C or/and Pascal(Pascal i am learning atm, so i need it more :P C only in the end of the year).
Thx for your time.

---

### Post by r-senior on 2013-02-25
Which Pascal compiler are you using? GNU, Free Pascal or other?

For C, it sounds like you need a mixture of gdb - the GNU debugger and gprof - the GNU profiler, perhaps with the addition of some conditional debug macros and use of assert.

[GNU Debugger]("https://www.google.co.uk/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&ved=0CDQQFjAA&url=http%3A%2F%2Fwww.gnu.org%2Fsoftware%2Fgdb%2F&ei=SYQrUYeUFO2b1AXuy4CICw&usg=AFQjCNEZ3AIki-tPVKN33He0ws3Qs3vCaA&sig2=PXtO16sn0oPK8HTKlCHOjA&bvm=bv.42768644,d.d2k")
[GNU Profiler]("http://sourceware.org/binutils/docs-2.23.1/gprof/index.html")

Both have GUI wrappers or alternatives.

When you start working a bit more on C, come back and ask for help on assert, NDEBUG and use of macros with #ifdef. ;)

---

### Post by Bachstelze on 2013-02-25
I would argue that no, it would not be helpful at all. gdb and gprof are only useful to experienced programmers. To someone who is learning C they would do more harm than good.

---

### Post by Warren Hill on 2013-02-25
For C and C++ programming I use eclipse.  This uses gdb hid behind a user friendly GUI to help you debug.  

**gdb** is a powerful debugger but it can be difficult to use if not integrated with a nice GUI inside an IDE (Integrated Development Environment).  There are lots to choose from.

If you want eclipse you can install it with
```

sudo apt-get install eclipse-cdt
```but there are others.  Take a look at the "developer tools" section of the software centre.

I have not used Pascal since Uni 20 something years ago so I can't advise on the tools for that any more but there should be others here who can.

---

### Post by cristo-father on 2013-02-25
> **r-senior said:**
> Which Pascal compiler are you using? GNU, Free Pascal or other?

For C, it sounds like you need a mixture of gdb - the GNU debugger and gprof - the GNU profiler, perhaps with the addition of some conditional debug macros and use of assert.

[GNU Debugger]("https://www.google.co.uk/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&ved=0CDQQFjAA&url=http%3A%2F%2Fwww.gnu.org%2Fsoftware%2Fgdb%2F&ei=SYQrUYeUFO2b1AXuy4CICw&usg=AFQjCNEZ3AIki-tPVKN33He0ws3Qs3vCaA&sig2=PXtO16sn0oPK8HTKlCHOjA&bvm=bv.42768644,d.d2k")
[GNU Profiler]("http://sourceware.org/binutils/docs-2.23.1/gprof/index.html")

Both have GUI wrappers or alternatives.

When you start working a bit more on C, come back and ask for help on assert, NDEBUG and use of macros with #ifdef. ;)

I am using fpc(free pascal compiler), if anyone can help me out, would be much appreciated.

---

### Post by r-senior on 2013-02-25
In theory you just debug it like C with gcc. When you compile, you add the -g option, just like you do in gcc:

```
fpc -g Hello.pas
```

I say in theory because I tried a quick program and, although I could get it to stop at a breakpoint, I couldn't print the values of variables.

I'd suggest looking at Lazarus, which is the standard IDE for Free Pascal. I've not used it because I only dabble with Pascal every now and then for old times' sake but it seems to have debugger support:

[http://wiki.lazarus.freepascal.org/Main_Page](http://wiki.lazarus.freepascal.org/Main_Page)
[http://wiki.lazarus.freepascal.org/GDB_Debugger_Tips](http://wiki.lazarus.freepascal.org/GDB_Debugger_Tips)

Lazarus is in the Ubuntu repositories -- search for lazarus.

---

