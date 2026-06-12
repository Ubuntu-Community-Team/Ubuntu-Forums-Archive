---
title: "Problem executing my programs"
date: 2007-02-08
forum: Programming Talk
---

### Post by draco86 on 2007-02-08
Hi!

If i compile a (correct) suorce code in the terminal using the command: gcc file.c  I didn't get any errors but if then I try to execute the program the terminal print "command not found", even if gcc have created the executable file.

Why?

PS: This happened even if i try to execute an Hello world! suorce code!

---

### Post by dannyboy79 on 2007-02-08
um, I am not compiling expert but I believe in order to install from source you are suppose to use these 3 commands.

1. configure

2. make

3. make install (I would use checkinstall, this will create a .deb so you can install that, then if you want to remove it you can use synaptic.)

make sure you have the build-essential package first.

check out this thread if you're confussed.

[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

---

### Post by nereid on 2007-02-08
Just a simple question but if you compile your little app like this

Simple Hello World in C (for example saved as hw.c)
```

#include <stdio.h>

int main (int argc, char * argv[]) {
        printf("Hello World\n");
        return 0;
}

```

with the following command

```

gcc -o hw hw.c

```

You should be able to execute the file

```

./hw

```

By the way, is the file allowed to execute? If not just change the execute bit

```

chmod +x hw

```

Hope I could help.

---

### Post by pmasiar on 2007-02-08
> **draco86 said:**
> If i compile a (correct) suorce code in the terminal using the command: gcc file.c  I didn't get any errors but if then I try to execute the program the terminal print "command not found", even if gcc have created the executable file.

Why?

Maybe your current working directory (where your executable is) is not in your PATH. Prefix program name with ./ to tell that it is in current directory:

instead executing myprogram.ext try: ./myprogram.ext

---

### Post by draco86 on 2007-02-08
Thanks,  I didn't know that I have to write "./" before the name of the executable file.

---

