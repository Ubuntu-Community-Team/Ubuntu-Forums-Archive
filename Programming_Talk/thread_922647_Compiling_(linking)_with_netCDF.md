---
title: "Compiling (linking) with netCDF"
date: 2008-09-17
forum: Programming Talk
---

### Post by lazer on 2008-09-17
So I've written a code in ANSI C that compiles and runs just fine with no errors or warnings using the command:

```
gcc mycode.c -lm -o mycode
```

Now I wanted to implement the netCDF data format for outputs.  So I made sure I had the proper packages with adept.  Then I added the appropriate code to the program and relevant header.  Now I got errors.  However they were all from the linker.  I tried compiling first then linking.  The result was that I could generate a ".o" file without error.  Then when I tried to link I got the following errors (which are the same errors I get if I just compile and link at the same time):

```
/tmp/cciaZ26N.o: In function `output':
mhdust.c:(.text+0x40173): undefined reference to `nc_create'
mhdust.c:(.text+0x401a9): undefined reference to `nc_def_dim'
mhdust.c:(.text+0x401df): undefined reference to `nc_def_dim'
mhdust.c:(.text+0x40215): undefined reference to `nc_def_dim'
mhdust.c:(.text+0x40278): undefined reference to `nc_def_var'
mhdust.c:(.text+0x402c0): undefined reference to `nc_def_var'
mhdust.c:(.text+0x40308): undefined reference to `nc_def_var'
mhdust.c:(.text+0x40350): undefined reference to `nc_def_var'
mhdust.c:(.text+0x40398): undefined reference to `nc_def_var'
/tmp/cciaZ26N.o:mhdust.c:(.text+0x403e0): more undefined references to `nc_def_var' follow
/tmp/cciaZ26N.o: In function `output':
mhdust.c:(.text+0x40f28): undefined reference to `nc_put_att_text'
mhdust.c:(.text+0x40f66): undefined reference to `nc_put_att_text'
mhdust.c:(.text+0x40fa4): undefined reference to `nc_put_att_text'
mhdust.c:(.text+0x40fe2): undefined reference to `nc_put_att_text'
mhdust.c:(.text+0x41020): undefined reference to `nc_put_att_text'
/tmp/cciaZ26N.o:mhdust.c:(.text+0x4105e): more undefined references to `nc_put_att_text' follow
/tmp/cciaZ26N.o: In function `output':
mhdust.c:(.text+0x41a0b): undefined reference to `nc_enddef'
mhdust.c:(.text+0x41a4b): undefined reference to `nc_put_vara'
mhdust.c:(.text+0x41a90): undefined reference to `nc_put_vara'
mhdust.c:(.text+0x41ad5): undefined reference to `nc_put_vara'
mhdust.c:(.text+0x41b1a): undefined reference to `nc_put_vara'
mhdust.c:(.text+0x41b5f): undefined reference to `nc_put_vara'
/tmp/cciaZ26N.o:mhdust.c:(.text+0x41ba4): more undefined references to `nc_put_vara' follow
/tmp/cciaZ26N.o: In function `output':
mhdust.c:(.text+0x423ed): undefined reference to `nc_put_var'
mhdust.c:(.text+0x42426): undefined reference to `nc_put_var'
mhdust.c:(.text+0x4245f): undefined reference to `nc_put_var'
mhdust.c:(.text+0x42498): undefined reference to `nc_put_var'
mhdust.c:(.text+0x424d1): undefined reference to `nc_put_var'
/tmp/cciaZ26N.o:mhdust.c:(.text+0x4250a): more undefined references to `nc_put_var' follow
/tmp/cciaZ26N.o: In function `output':
mhdust.c:(.text+0x4254d): undefined reference to `nc_put_vara'
mhdust.c:(.text+0x42595): undefined reference to `nc_put_vara'
mhdust.c:(.text+0x425dd): undefined reference to `nc_put_vara'
mhdust.c:(.text+0x425fc): undefined reference to `nc_close'
/tmp/cciaZ26N.o: In function `handle_error':
mhdust.c:(.text+0x43e2a): undefined reference to `nc_strerror'
collect2: ld returned 1 exit status
```

What am I doing wrong here?

---

### Post by dribeas on 2008-09-17
> **lazer said:**
> What am I doing wrong here?

You are not linking with the library that provides those symbols. Read the docs on what to link against, or try to locate which lib has those symbols.

---

### Post by lazer on 2008-09-17
You beat me to it...total newb mistake.  I needed to add the -lnetcdf to the compilation command.  Dumb!

```
gcc myprogram.c -lm -lnetcdf -o myprogram
```

This works just fine.

---

