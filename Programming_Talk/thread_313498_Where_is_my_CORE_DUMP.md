---
title: "Where is my CORE DUMP?"
date: 2006-12-06
forum: Programming Talk
---

### Post by charlie. on 2006-12-06
Right. We all know that the C abort() function is supposed to exit and give us a core dump.

Assuming that this is considered the truth, why does it not work?

I've got a C++ app that calls abort() and will exit with a "core dumped" message, but I can't find the dump file. I was told to look for it in the current folder and the executables folder.

I know this is an odd question. Please help.

---

### Post by Arndt on 2006-12-06
> **charlie. said:**
> Right. We all know that the C abort() function is supposed to exit and give us a core dump.

Assuming that this is considered the truth, why does it not work?

I've got a C++ app that calls abort() and will exit with a "core dumped" message, but I can't find the dump file. I was told to look for it in the current folder and the executables folder.

I know this is an odd question. Please help.

It is a bit odd. Did the program perhaps change its current directory while running? The core file is put there. It sounds like you do know what a core dump file is, but in case you don't, its name is "core", not "dump".
It may be possible to configure Linux to make the name be something else, like core.myprogram.3418, but I don't know.

---

### Post by yota on 2006-12-06
By default core dumps are suppressed (for most users are just a waste of space); you can enable them with:
```

ulimit -c *size*

```
See man bash for infos on 'ulimit' usage.
AFAIK the system-wide settings stood in /etc/login.defs, but now it says that is obsoleted by pam. I suppose the correct file now is /etc/security/limits.conf

Hope this helps!

---

### Post by Arndt on 2006-12-06
> **yota said:**
> By default core dumps are suppressed (for most users are just a waste of space); you can enable them with:
```

ulimit -c *size*

```
See man bash for infos on 'ulimit' usage.
AFAIK the system-wide settings stood in /etc/login.defs, but now it says that is obsoleted by pam. I suppose the correct file now is /etc/security/limits.conf

Hope this helps!

If core files are suppressed, the message at the abort will only say "Aborted", not "Aborted (core dumped)", so I don't think this was the original problem.

(I just discovered that if you want to suppress core files and later turn them on again, don't use "ulimit -c 0", use "ulimit -S -c 0".)

---

### Post by yota on 2006-12-06
> **Arndt said:**
> If core files are suppressed, the message at the abort will only say "Aborted", not "Aborted (core dumped)", so I don't think this was the original problem.

Oh, sorry I had never noticed that...
anyway a
```

ulimit -a

```
will tell us for sure if ulimit is involved or not.

---

### Post by charlie. on 2006-12-07
```
ulimit -a
```

says...

```
core file size          (blocks, -c) 0
```

I presume that 0 means that files are suppressed.

```
ulimit -c unlimited
```

changes the output from "0" to "unlimited". Running the aborting code does create a "core" dump file, in the current directory, not the directory that the executable lives in - unless both directories are the same.

The value set by ulimit does not seem to persist across terminal sessions. Even multiple instances of the Gnome terminal do not appear to share this setting.

---

### Post by Arndt on 2006-12-07
> **charlie. said:**
> ```
ulimit -a
```

says...

```
core file size          (blocks, -c) 0
```

I presume that 0 means that files are suppressed.

```
ulimit -c unlimited
```

changes the output from "0" to "unlimited". Running the aborting code does create a "core" dump file, in the current directory, not the directory that the executable lives in - unless both directories are the same.

The value set by ulimit does not seem to persist across terminal sessions. Even multiple instances of the Gnome terminal do not appear to share this setting.

No, it's process local. But if you set it in one shell and start gnome-terminal from that shell, the new shell will inherit it.

---

### Post by sax1johno on 2009-07-29
Adding the following line to your .bashrc file (found in ~/.bashrc) will allow unlimited sized core files for every bash terminal:

```
# Change the core file size to unlimited
ulimit -c unlimited
```

:-) good luck.

---

### Post by monraaf on 2009-07-29
Why on earth are you resurrecting a thread that's more than 2 1/2 years old? :confused:

---

### Post by velmont on 2011-09-26
2,5 more years later:

Because it's still useful today ;-)

---

### Post by ben@kietzman.org on 2012-10-24
Exaclty.  I know I found it useful.

---

### Post by patrickst on 2013-04-17
And just need it recently.

---

