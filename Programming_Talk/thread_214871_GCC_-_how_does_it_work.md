---
title: "GCC - how does it work ?"
date: 2006-07-13
forum: Programming Talk
---

### Post by ThaDoctor99 on 2006-07-13
Hi.
Could anyone please give me some explaination on how this compiler works, please keep it to basics.

Thanks in advance.
greetings Tobias

---

### Post by yota on 2006-07-13
Mhh... you should be a little more specific: what do you mean with 'work'? How can be invoked to compile something you have written yourself or how can be used to compile an already made package?

Anyway have a look at [http://gcc.gnu.org/](http://gcc.gnu.org/) there are faqs, manuals, docs and wiki; every question is probably already answered there.

---

### Post by ThaDoctor99 on 2006-07-13
mainly self written software but also already written package also have interest...

---

### Post by yota on 2006-07-13
If you are going to compile you own code the basic use is:
```

gcc <sourcefile.name> -o <compiledbinaryfile.name>

```
like:
> 
yota@linbook:~/sorgenti$ cat hello.c++
#include <iostream>
int main ()
{
        std::cout << "Hello, world!\n";
}

yota@linbook:~/sorgenti$ g++ hello.c++ -o hello
yota@linbook:~/sorgenti$ ./hello
Hello, world!
yota@linbook:~/sorgenti$


Usually source packages contain an executable configuration script (that verify system requirements and prepares the package for compilation) and a 'Makefile'.
The latter contains compilation instructions and is to be parsed by the tool 'make'.
So if you want to compile an already made package (probably it will be in a .tar.gz or .tar.bz2 file) you have to:
[LIST=1]
[*]uncompress the archive with 'tar -xzf plackage.tar.gz'
[*]enter the package dir 'cd package'
[*]launch the configure script './configure'
[*]compile with 'make'
[*]install with 'make install'
[/LIST]

Again I invite you to search documentation at htp://gcc.gnu.org, there you'll find much more than I can put on this thread!

---

### Post by ThaDoctor99 on 2006-07-13
The file should that be with or without
<> or not ?

---

### Post by elettronicha on 2006-07-13
without, see the example above.

---

### Post by tzulberti on 2006-07-13
I recommend you to read about make files...

---

### Post by Note360 on 2006-07-13
```

gcc path/to/file -o filname_you_want.out

```

Then

```

path/to/filname.out

```

If the file name is in the current directory

```

./filname.out

```

---

### Post by mostwanted on 2006-07-14
> **Note360 said:**
> ```

gcc path/to/file -o filname_you_want.out

```

Then

```

path/to/filname.out

```

If the file name is in the current directory

```

./filname.out

```

Naming you file with an .out-extension is not the norm in UNIX. The norm is to not have any extension; take a look at the /usr/bin folder, when was the last time you had to write firefox.out or gedit.out to start you program?

---

