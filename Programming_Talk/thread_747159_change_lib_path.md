---
title: "change lib path"
date: 2008-04-06
forum: Programming Talk
---

### Post by leg on 2008-04-06
Is there a way to change the path a binary uses when it is ran? So for instance I am compiling a program that usually finds it libs in /lib or /usr/lib. I want to override that for a particular run of that program to /usr/local/src/<some compiled version of lib> but for it to work normally if no path is specified.

Not sure if I have made myself clear enough so say if not.

---

### Post by stroyan on 2008-04-06
You can set a path for searching for library files by setting the LD_LIBRARY_PATH environment variable.
It is documented in 'man ld.so'.
Be careful about processes started as children of your target binary.
They can inherit the same LD_LIBRARY_PATH with unexpected results.

---

### Post by leg on 2008-04-06
> **stroyan said:**
> You can set a path for searching for library files by setting the LD_LIBRARY_PATH environment variable.
It is documented in 'man ld.so'.
Be careful about processes started as children of your target binary.
They can inherit the same LD_LIBRARY_PATH with unexpected results.Does that affect every process once it has been set or can it be set indivually. What happens with path names at the linking stage ie are they embedded into the binary or not?

---

### Post by smartbei on 2008-04-06
It sounds like what you want is dynamic library loading. Here are some links to more info on the subject:
[list]
[*][http://www.securityfocus.com/infocus/1872](http://www.securityfocus.com/infocus/1872)
[*][http://www.linux.com/base/ldp/howto/Program-Library-HOWTO/dl-libraries.html](http://www.linux.com/base/ldp/howto/Program-Library-HOWTO/dl-libraries.html)
[*][http://www.ibiblio.org/oswg/oswg-nightly/oswg/en_GB.ISO_8859-1/books/linux-c-programming/GCC-HOWTO/x796.html](http://www.ibiblio.org/oswg/oswg-nightly/oswg/en_GB.ISO_8859-1/books/linux-c-programming/GCC-HOWTO/x796.html) - Actual example code.
[/list]

---

### Post by stroyan on 2008-04-07
> **leg said:**
> Does that affect every process once it has been set or can it be set indivually. What happens with path names at the linking stage ie are they embedded into the binary or not?
An environment variable like LD_LIBRARY_PATH will be inherited by child processes.  But environment variables in linux are not system-wide settings.
Setting one will not affect parent processes or already started child processes.
You can start a command from bash shell like
  LD_LIBRARY_PATH=/usr/lib/debug ldd /bin/date
to have an environment variable set for just that process and its descendants.
That won't affect other commands that you run from the shell.
Setting an environment variable like
  export LD_LIBRARY_PATH=/usr/lib/debug
will set it for the shell and all commands that the shell executes after that.

Library search paths can be set at the linking stage by using ld's -rpath option.
That can be done as a gcc -Wl,-rpath option.
You can see the setting of an rpath search path with 'readelf -d a.out'.

---

### Post by leg on 2008-04-07
> **smartbei said:**
> ...Thanks for those links I will read through them and see what I can learn.
> **stroyan said:**
> ...I think you are right and the rpath thing may be what I am after. I suppose reading up on gcc and elf will help with that.

---

