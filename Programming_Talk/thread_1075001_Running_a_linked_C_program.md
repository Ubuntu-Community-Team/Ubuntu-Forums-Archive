---
title: "Running a linked C program"
date: 2009-02-19
forum: Programming Talk
---

### Post by bgs100 on 2009-02-19
For some reason I can't run a C compiled program that's not statically linked. I have no idea what to do.  The program shows up in ls but if I try to run it it says no such file or directory.  A statically compiled program will run fine, however.  Help? :(

---

### Post by jimi_hendrix on 2009-02-19
please show the compile command you are using

---

### Post by bgs100 on 2009-02-19
gcc -o hello hello.c

---

### Post by jimi_hendrix on 2009-02-19
and the file?

---

### Post by bgs100 on 2009-02-19
Whoops
I deleted it
it just (was meant to) print hello world.  Snova gave me the code.
GCC gave no errors when compiling

---

### Post by jimi_hendrix on 2009-02-19
try it again...see what happens if you do

```

int main()
{
     return 0;
}

```

---

### Post by monkeyking on 2009-02-19
also try 
```
ldd hello
```
or

```
readelf hello
```

---

### Post by bgs100 on 2009-02-19
> **jimi_hendrix said:**
> try it again...see what happens if you do

```

int main()
{
     return 0;
}

```
```
> gcc -o hello hello.c
>./hello
bash: ./hello: No such file or directory

```

---

### Post by bgs100 on 2009-02-19
> **monkeyking said:**
> also try 
```
ldd hello
```
or

```
readelf hello
```
```

>ldd hello
/usr/bin/ldd: line 117: ./hello: No such file or directory
>readelf hello
Usage: readelf <option(s)> elf-file(s)
 Display information about the contents of ELF format files
 Options are:
  -a --all               Equivalent to: -h -l -S -s -r -d -V -A -I
  -h --file-header       Display the ELF file header
  -l --program-headers   Display the program headers
     --segments          An alias for --program-headers
  -S --section-headers   Display the sections' header
     --sections          An alias for --section-headers
  -g --section-groups    Display the section groups
  -t --section-details   Display the section details
  -e --headers           Equivalent to: -h -l -S
  -s --syms              Display the symbol table
      --symbols          An alias for --syms
  -n --notes             Display the core notes (if present)
  -r --relocs            Display the relocations (if present)
  -u --unwind            Display the unwind info (if present)
  -d --dynamic           Display the dynamic section (if present)
  -V --version-info      Display the version sections (if present)
  -A --arch-specific     Display architecture specific information (if any).
  -c --archive-index     Display the symbol/file index in an archive
  -D --use-dynamic       Use the dynamic section info when displaying symbols
  -x --hex-dump=<number|name>
                         Dump the contents of section <number|name> as bytes
  -p --string-dump=<number|name>
                         Dump the contents of section <number|name> as strings
  -w[lLiaprmfFsoR] or
  --debug-dump[=rawline,=decodedline,=info,=abbrev,=pubnames,=aranges,=macro,=frames,=str,=loc,=Ranges]
                         Display the contents of DWARF2 debug sections
  -I --histogram         Display histogram of bucket list lengths
  -W --wide              Allow output width to exceed 80 characters
  @<file>                Read options from <file>
  -H --help              Display this information
  -v --version           Display the version number of readelf

```

---

### Post by monkeyking on 2009-02-19
try this one instead
```

readelf -h hello

```

but also

```
ls -lah hello
```

---

### Post by bgs100 on 2009-02-20
> **monkeyking said:**
> try this one instead
```

readelf -h hello

```

but also

```
ls -lah hello
```

```
>readelf -h hello
ELF Header:
  Magic:   7f 45 4c 46 01 01 01 00 00 00 00 00 00 00 00 00 
  Class:                             ELF32
  Data:                              2's complement, little endian
  Version:                           1 (current)
  OS/ABI:                            UNIX - System V
  ABI Version:                       0
  Type:                              EXEC (Executable file)
  Machine:                           Intel 80386
  Version:                           0x1
  Entry point address:               0x80482e0
  Start of program headers:          52 (bytes into file)
  Start of section headers:          5892 (bytes into file)
  Flags:                             0x0
  Size of this header:               52 (bytes)
  Size of program headers:           32 (bytes)
  Number of program headers:         8
  Size of section headers:           40 (bytes)
  Number of section headers:         36
  Section header string table index: 33
>ls -lah hello
-rwxr-xr-x 1 ian ian 8.8K 2009-02-19 21:46 hello
```

---

### Post by bgs100 on 2009-03-07
bump

---

### Post by monkeyking on 2009-03-07
I thought you have solved it already.

please post the following.

Your .cpp file
and the commands you use to compile and run.

The subject of this thread is something about a linked program.
But is this just the hello world program?

---

### Post by monkeyking on 2009-03-07
you can check if something is wrong with your build system by using codepad
Try this link as a reference
[http://codepad.org/9gEY0FTu](http://codepad.org/9gEY0FTu)

---

### Post by T.J. on 2009-03-07
Does it have execution permissions?  You can make certain by:

chmod +x ./hello

Then run it by:

./hello

---

