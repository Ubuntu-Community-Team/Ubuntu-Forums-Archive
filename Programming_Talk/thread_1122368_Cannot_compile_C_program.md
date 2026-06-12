---
title: "Cannot compile C program"
date: 2009-04-11
forum: Programming Talk
---

### Post by SMohr on 2009-04-11
First time using Linux and C.  I'm trying to compile a simple hello program and I'm not having luck.  The file is saved as hello.c and I'm using the command gcc -o hello hello.c and I'm getting the errors below.  One thing I should note is that I don't have the Linux OS installed on my computer, I'm using a pc provided by my college.  thx

hello.c:1: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âbufferâ
hello.c:1: error: missing terminating ' character
hello.c:2: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âyouâ
hello.c:3: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âenterâ
hello.c:3: error: missing terminating ' character
In file included from /usr/include/_G_config.h:44,
                 from /usr/include/libio.h:32,
                 from /usr/include/stdio.h:72,
                 from hello.c:6:
/usr/include/gconv.h:72: error: expected declaration specifiers or â...â before âsize_tâ
/usr/include/gconv.h:88: error: expected declaration specifiers or â...â before âsize_tâ
/usr/include/gconv.h:97: error: expected declaration specifiers or â...â before âsize_tâ
/usr/include/gconv.h:174: error: expected specifier-qualifier-list before âsize_tâ
In file included from /usr/include/stdio.h:72,
                 from hello.c:6:
/usr/include/libio.h:329: error: expected specifier-qualifier-list before âsize_tâ
/usr/include/libio.h:361: error: expected declaration specifiers or â...â before âsize_tâ
/usr/include/libio.h:370: error: expected declaration specifiers or â...â before âsize_tâ
/usr/include/libio.h:486: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â_IO_sgetnâ
In file included from hello.c:6:
/usr/include/stdio.h:308: error: expected declaration specifiers or â...â before âsize_tâ
/usr/include/stdio.h:315: error: expected declaration specifiers or â...â before âsize_tâ
/usr/include/stdio.h:357: error: expected declaration specifiers or â...â before âsize_tâ
/usr/include/stdio.h:359: error: format string argument not a string type
/usr/include/stdio.h:361: error: expected declaration specifiers or â...â before âsize_tâ
/usr/include/stdio.h:610: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âfreadâ
/usr/include/stdio.h:616: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âfwriteâ
/usr/include/stdio.h:638: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âfread_unlockedâ
/usr/include/stdio.h:640: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âfwrite_unlockedâ

---

### Post by lisati on 2009-04-11
If it was an Ubuntu system I'd suggest:
```
sudo apt-get build-essential
```

But since it isn't, I'll ask this instead: What sort of system is it? Mac? Windows? Which compiler?

---

### Post by cmay on 2009-04-11
> ello.c:1: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âbufferâ
hello.c:1: error: missing terminating ' character
hello.c:2: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âyouâ
hello.c:3: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âenterâ
hello.c:3: error: missing terminating ' character
In file included from /usr/include/_G_config.h:44,
                 from /usr/include/libio.h:32,
                 from /usr/include/stdio.h:72,
                 from hello.c:6:
these errors looks like you have forgot the '#' sign in the include and the error that tells you missing terminating ' character i assume is a forgotten " in the puts or printf statements but i never seen those characters in my system. i use a Danish keyboard layout but still have language set to english. so with out the code in question i am not sure if anyone can see exactly what those errors means. can you post the code please.

 also which system do you use. mac , bsd or solaris. i only know bsd and solaris but i never seen the warnings such as these on those systems eihter. so i am just guessing what they might mean.

---

### Post by Sinkingships7 on 2009-04-11
It would be nice if you provided any sort of code along with your errors. Also, and I'm not positive if it matters, but I think gcc is supposed to be used like this:
```

gcc in.c -o out

```
The location of the -o flag can change, I know, but I think the input source file has to come before the desired name for the output binary.

---

### Post by sujoy on 2009-04-11
> **Sinkingships7 said:**
> It would be nice if you provided any sort of code along with your errors. Also, and I'm not positive if it matters, but I think gcc is supposed to be used like this:
```

gcc in.c -o out

```
The location of the -o flag can change, I know, but I think the input source file has to come before the desired name for the output binary.

no, the order of output filename and sourcefile doesnt matter as long as the option flags are used correctly.

hard to tell where the problem is though, without the code

---

### Post by SMohr on 2009-04-11
here is the code for the program

#include <stdio.h>

int main()
{
  printf("hello, world\n");
}

---

### Post by SMohr on 2009-04-11
> **lisati said:**
> If it was an Ubuntu system I'd suggest:
```
sudo apt-get build-essential
```

But since it isn't, I'll ask this instead: What sort of system is it? Mac? Windows? Which compiler?

The compiler is Bloodshed I believe.  This is a school computer from which I can log on remotely.

---

### Post by lisati on 2009-04-11
I've had another look at the error messages. Amongst other things, it looks like the compiler is complaining about something in the file stdio.h 
The only time I've had anything quite like that is when I've made some kind of mistake with the compiler options.

---

### Post by Sinkingships7 on 2009-04-11
> **SMohr said:**
> The compiler is Bloodshed I believe.  This is a school computer from which I can log on remotely.

If you're using the bloodshed IDE, then there should be a compile button on the upper left. Compiling manually with gcc isn't necessary. Also, your code looks fine, excluding the fact that you didn't return an integer from an integer-returning function.

EDIT: I believe that, because bloodshed is a C++ development environment, you'll have to use the C-ported-for-C++ libraries, such that your include will now be:
```

#include <cstdio>

```

---

