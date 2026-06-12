---
title: "Debugging Symbol Blues"
date: 2007-10-26
forum: Programming Talk
---

### Post by Carl Hamlin on 2007-10-26
The key players here are NASM, ld, gdb, and ddd.

I build my code using NASM:

```

nasm -f elf code.asm

```

Then I link using ld:

```

ld code.o -o code

```

Please note that I have NOT stripped debugging symbols.

THEN.

I go into ddd to figure out where the segmentation faults are coming from, and I get this:

```

GNU DDD 3.3.11 (i486-pc-linux-gnu), by Dorothea Lutkehaus and Andreas Zeller.
Copyright (C) 1995-1999 Technische Universitat Braunschwieg, Germany.
Copyright (C) 1999-2001 Universitat Passau, Germany.
Copyright (C) 2001 Universitat des Saarlandes, Germany.
Copyright (C) 2001-2004 Free Software Foundation, Inc.
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(gdb) file '/home/chamlin/Assembly Language House/Code/code'
(no debugging symbols found)

```

I've been writing ASM on this machine for quite a while now, and I've never had any trouble getting debugging symbols to work properly until now.

I'm wondering if I've inadvertently modified a configuration parameter in ld which is causing it to strip debugging symbols by default.

I've already done the search engine thing with limited results. Nothing would make me happier than for this to be one of those 'Oh, yeah - you gribbled your Farber gasket when you were messing with the settings in Pickle; just de-gribble the gasket and you should be back to where you were' sorts of things.

Common issue, anyone?

---

### Post by fatalGlory on 2008-05-13
I know this is an old thread, but I'm having this issue too and I'm hoping to get some guidance on it.  Hopefully someone knows what's wrong by now... (p.s. I'm explicitly using the -g flag to nasm as well.  Still no debugging symbols found).

---

### Post by NathanB on 2008-05-13
Simply use the "-g" option to tell NASM to include the debugging symbols.

```
nasm -f elf -g code.asm
ld -o code code.o
```

Nathan.

---

### Post by NathanB on 2008-05-14
fatalGlory -

Be sure that you invoke gdb (and its front-ends:  ddd, xxgdb, etc. ) correctly.  Prepend either "./" or the full path onto the front of the executable you wish to examine.  Example:
```
 gdb ./code 
```

Nathan.

---

### Post by fatalGlory on 2008-05-22
Tried "gdb ./prog" - no dice.  And in ddd I generally open the executable from File->Open anyway.

Google still returns basically nothing.  Wondering (as grandparent post said) if it is something in the way ld works rather than nasm.

---

### Post by fatalGlory on 2008-05-23
Update: compiled source file with nasm on a different machine to get the object file.  Next, transferred the object file to my machine and linked with ld.

Debugging symbols worked fine this way so ld is not to blame (not accidently stripping out debug info).  nasm is apparently not even adding the info.

"nasm -v" on my machine shows:
```
NASM version 0.99.06-20071101 compiled on Nov 15 2007
```

On the machine where it works it shows:
```
NASM version 2.01 compiled on Feb 20 2008
```

So I tried upgrading to version 2.02 with the binary rpm I found at nasm.sf.net and now debugging symbols are working for me again.

My previous version is the latest version in the hardy repo at time of writing, but it seems a long way behind (two major versions) the project's stable release, does this maybe require some attention from the ubuntu devs/package maintainers?  Might file a bug.

---

### Post by Zugzwang on 2008-05-23
For the protocol: If debugging symbols are not found, read the manual. It is [clearly stated]("http://nasm.sourceforge.net/doc/nasmdoc2.html#section-2.1.6") that an output format might not support some format of debugging information. In that case, -g is ignored. Also one has to make sure that the information is in gdb-readable format. See [http://nasm.sourceforge.net/doc/nasmdoc2.html#section-2.1.5]("http://nasm.sourceforge.net/doc/nasmdoc2.html#section-2.1.5") for details.

---

### Post by fatalGlory on 2008-05-24
I did in fact find that information out in the process of trying to fix this.  I found that STABS seemed to be the correct debugging symbol format, however, I couldn't even get this one to output.

I hadn't had problems with nasm before just using "nasm -g -f elf myprog.asm", and after updating my nasm, I can use this command again just like before.

---

