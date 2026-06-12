---
title: "Compiling Ada with gcc"
date: 2008-07-16
forum: Programming Talk
---

### Post by ceclauson on 2008-07-16
Hello.

I'm trying to compile Ada with gcc.  Here's the program, a simple "hello, world":

```

with Ada.Text_IO;

procedure Hello is
begin
   Ada.Text_IO.Put_Line("Hello, world!");
end Hello;

```

When I try ```
gcc hello.adb
``` on the command line, I get the following message:
```

gcc: -c or -S required for Ada

```

If I use the -S switch, I get assembly, and if I use the -o switch, I get an object file.  I can't link the object file, because it contains these symbols (nm hello.o) that the linker can't resolve:
```

00000000 r C.0.390
         U __gnat_eh_personality
00000000 T _ada_hello
         U ada__text_io__put_line__2

```

Does anyone know how to compile an Ada program, or what objects or libraries I could use to link the object outputs against?

Thanks,
Cooper

---

### Post by Zugzwang on 2008-07-16
You might want to have a look at the following web page/book: [http://oopweb.com/Ada/Documents/AdaLinux/Volume/book.html]("http://oopweb.com/Ada/Documents/AdaLinux/Volume/book.html")

---

### Post by samjh on 2008-07-16
First, install GNAT (GNU New York University Ada Translator):
```
sudo apt-get install gnat
```

And use this command to compile:
```
gnat make hello.adb
```


If you *insist* in compiling Ada programs using gcc, then follow these steps:

1. Run gcc to compile to object file:
```
gcc -c hello.adb
```

2. Run gnatbind to produce binder output:
```
gnatbind hello.ali
```

3. Run gnatlink to link and produce executable output:
```
gnatlink hello
```

Take note that you still need to have gnat installed.

Also take note that "gnatbind" is the same as "gnat bind", "gnatlink" is the same as "gnat link", and "gnatmake" is the same as "gnat make".

But seriously, save yourself a bunch of keystrokes and just use gnatmake. :)

---

### Post by ceclauson on 2008-07-16
Sweet!  Gnatmake it is.  Thanks so much!

-Cooper

---

