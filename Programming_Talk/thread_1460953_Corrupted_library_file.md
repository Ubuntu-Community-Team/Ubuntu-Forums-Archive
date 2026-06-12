---
title: "Corrupted library file"
date: 2010-04-23
forum: Programming Talk
---

### Post by newport_j on 2010-04-23
I believe that one of my library files may be corrupted. I am not totally sure and that is why I am writing this question.

The compiler cannot access it during compile and linking and when I put the library file in the same directory as the source code (there is no way the compiler could not find it then) it still claims it cannot find it.

Hence, it must be corrupt. How can I test that?

Newport_j

---

### Post by iponeverything on 2010-04-23
.a or .so

ar can list the contents of a .a.

If the libraries were installed via a .deb you can verify the integrity with debsums.

not sure about peeking inside a .so ..

---

### Post by Some Penguin on 2010-04-23
I question the OP's logic.  The 'current directory' is NOT automatically on the linker's search path.

---

### Post by newport_j on 2010-04-23
If it finds the source code of the main program then it should find anything else in the directory, such as a library file that I think is corrupted.

But let's go with what you say. How do I tell if this file is corrupt? I thought putting in the directory with the program source code is a a good way. If it is not then suggest an alternative. 

This is a problem that I want to solve, and any way that I can do it is fine with me.

Newport_j

---

### Post by MadCow108 on 2010-04-23
no the compiler does not look for libraries in the current directory
you have to add the -L. flag
I too suspect some wrong use. A corrupted file does not cause file not found type errors

as for checking: get a checksum of an ok file and compare.
How you get it depends on where you got the library for...

why can't you just reinstall it?

---

### Post by soltanis on 2010-04-24
man ld

```

       -L searchdir
       --library-path=searchdir
           Add path searchdir to the list of paths that ld will search for archive libraries
           and ld control scripts.  You may use this option any number of times.  The
           directories are searched in the order in which they are specified on the command
           line.  Directories specified on the command line are searched before the default
           directories.  All -L options apply to all -l options, regardless of the order in
           which the options appear.  -L options do not affect how ld searches for a linker
           script unless -T option is specified.

           If searchdir begins with "=", then the "=" will be replaced by the sysroot prefix,
           a path specified when the linker is configured.

           The default set of paths searched (without being specified with -L) depends on
           which emulation mode ld is using, and in some cases also on how it was configured.

           The paths can also be specified in a link script with the "SEARCH_DIR" command.
           Directories specified this way are searched at the point in which the linker
           script appears in the command line.

```

The linker does not search the current directory by default.

---

