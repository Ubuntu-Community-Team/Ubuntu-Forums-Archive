---
title: "gcc linking problem"
date: 2007-12-26
forum: Programming Talk
---

### Post by PaperPilot on 2007-12-26
Hi all:

I am compiling a D language program in two files and getting an ld error.

The files are: hello.d which has the main() routine.
                   Word.d has a class which is instantiated in hello

If I compile both files together like:

**dmd hello Word**

the program compiles and links successfully.  If I compile Word.d first and then hello.d and include the working directory like:

**dmd hello -I~/sandbox**  where sandbox is the working directory I get errors like:  **undefined reference to '_D4Word12__ModuleInfoZ'**

D uses the gcc linker, ld, and I installed gcc-buildessential to get it, so the **-I** flag should work, but dosen't in this instance.  Is there another package I need to install?

Thanks in advance.

---

### Post by LaRoza on 2007-12-26
If it is anything like gcc, to link to the object file, just compile with its name, not the -l flag.

```

dmd main.d headers.o

```

---

### Post by brianborchers on 2007-12-26
Try using -L instead of -I.  -I tells gcc where to look for files referred to in #include preprocessor directives.  -L tells ld where to look for libraries.

---

### Post by PaperPilot on 2007-12-26
> **LaRoza said:**
> If it is anything like gcc, to link to the object file, just compile with its name, not the -l flag.

```

dmd main.d headers.o

```

But I might want to include 25 or 30 classes in one main, and I would prefer not to list all the files in the command line.  Just listing the directory would be so much simpler.

---

### Post by PaperPilot on 2007-12-26
> **brianborchers said:**
> Try using -L instead of -I.  -I tells gcc where to look for files referred to in #include preprocessor directives.  -L tells ld where to look for libraries.

Using **-L** gets me **No such file or directory** messages.  I think libraries have a special format.  I am not _that_ familiar with gcc to write libraries.

---

### Post by geraldm on 2007-12-26
> Using -L gets me No such file or directory messages. 

useage is -L{path_to_directory}
and so when used properly with the directory, it never returns 'No such file or directory'
useage for -l{library_filename} 
requires a library filename beginning with "lib", with the first three letters omitted, e.g. "libm.so" becomes -lm

Gerald

---

