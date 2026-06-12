---
title: "Compilling error with g77"
date: 2007-04-19
forum: Programming Talk
---

### Post by Schjoh on 2007-04-19
Hi

I'm a n00b in linux and fortran, so here is probable a stupid question.
I'm trying to compile a fortran code using g77, so typed, and got:

```
g77 template.f
/usr/bin/ld: crt.0: No such file: No such file or directory
collect2: ld returned 1 exit status
```

It seems like I need some sort of files, but I don't know what files it is. Or is there something else wrong?

---

### Post by thnogueira on 2007-04-19
It seems the gnu linker (ld) is not installed on your machine. Try to install binutils package

EDIT:

Sorry, forget what I sad.

---

### Post by LaRoza on 2007-04-19
Did what I said help?

---

### Post by Schjoh on 2007-04-19
No it didn't LaRoza. I still get the same message

---

### Post by WW on 2007-04-19
Can you compile other fortran programs?

For example, here is hello.f:
```

      program hello
      write (*,*) 'Hello, world!'
      stop
      end

```
You can compile and run it like this:
```

$ g77 hello.f -o hello
$ ./hello
 Hello, world!
$
```
Does that work for you?

---

### Post by Schjoh on 2007-04-19
No, I get the same message when I wrote the hello.f

---

### Post by gusanto on 2007-07-15
> **WW said:**
> Can you compile other fortran programs?

For example, here is hello.f:
```

      program hello
      write (*,*) 'Hello, world!'
      stop
      end

```
You can compile and run it like this:
```

$ g77 hello.f -o hello
$ ./hello
 Hello, world!
$
```
Does that work for you?

After compiling with following syntax, 
g77 hello.f -o hello
I have to run it with ./hello
I want to run it by only typing hello, what should I change?
Thanks.

---

### Post by xadder on 2007-07-15
You need to add your current directory (.) to your path. I also usually add my own bin directory.

In your .bashrc file, do something like:


# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=.:~/bin:"${PATH}"
fi

export PATH

(If you don't want to use the ~/bin option, just do export PATH=.:"${PATH}" instead of all the above)

Start a new shell, and do "echo $PATH" to check it worked.
Some people raise security concerns with having current path by default in $PATH, but I hate having to type ./a.out or whatever.

---

