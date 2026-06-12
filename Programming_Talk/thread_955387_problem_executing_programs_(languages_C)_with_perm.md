---
title: "problem executing programs (languages C) with permission denied but... this doesn't"
date: 2008-10-22
forum: Programming Talk
---

### Post by SuckerBlood on 2008-10-22
Hi!,

Recently I compile a difference programs in my Ubuntu 8.04 with all updates.
One of this programs was a GTK+C program (i'm learning GTK).
I try to compile, OK. I try to execute **with the _corresponding permission_**, seems correct.

But no! I have and error that return:
```
bash: ./program: Permiso denegado
```
-----------

Include using sudo!:
```
sudo: unable to execute ./hello: Permission denied
```

I try with a simple program (Hello World!!) and i have the same response.

```
#include <stdio.h>

int main() {
	printf("Hello World");
	return 0;
}
```

```
$ gcc hello.c -o hello -W -pedantic
bash: ./hello: Permiso denegado
```
---------
or sudo:
```
sudo: unable to execute ./hello: Permission denied
```

I don't know what is doing... but i need compile in C++ for the University!

Please.

PS: good byeee, I'm spanish. Sorry for my understandable English

---

### Post by jespdj on 2008-10-22
Strange. Is the program executable? Try:
```
chmod u+x hello
./hello
```
GCC should do this by default, so it would be strange if your compiled program isn't executable.

---

### Post by SuckerBlood on 2008-10-22
> **jespdj said:**
> Strange. Is the program executable? Try:
```
chmod u+x hello
./hello
```
GCC should do this by default, so it would be strange if your compiled program isn't executable.

No... :(:(
I also understand it :(
I **need** compileee :(

---

### Post by snova on 2008-10-22
Perhaps a misconfigured umask? GCC *should* be generating executable files.

The only other thing I can think of right now is that the hard drive partition your program is resident on was mounted with the 'noexec' option.

"sudo" doesn't do anything but run a program as adminstrator. It won't help here.

---

