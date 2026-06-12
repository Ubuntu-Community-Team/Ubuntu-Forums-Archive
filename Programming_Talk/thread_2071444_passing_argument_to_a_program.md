---
title: "passing argument to a program"
date: 2012-10-15
forum: Programming Talk
---

### Post by IAMTubby on 2012-10-15
Hey,
When I type at the shell saying
```

$./Name_Of_My_Executable this is a list of arguments

```

It goes inside the main as 
```

int main(int argc, char** argv)
{

}

```
Who makes sure that the count of arguments goes to int argc and that *argv holds "the" and *(argv+1) holds "is" etc. ?

**Is it the the shell itself ?**

Thanks.

---

### Post by trent.josephsen on 2012-10-15
Yes and no.

In Unix-like systems, the shell does part of the work -- parsing (actually, lexing or tokenizing) the command line you type into individual arguments. Then it fork()s itself, creating a child process, which calls execve() (or a closely related function) to do the rest of the work.

execve() is a system call that replaces the current *process image* (executable code and data that makes up a running program) with a new image, one constructed from the file given as its first argument. Since it's a system call, it's actually a request for the OS to do the necessary work. In Unix-likes, the part of the OS that does this job (constructing a new process image and loading it in place of the old one) is called the [loader](http://en.wikipedia.org/wiki/Loader_%28computing%29).

It's important to realize that main() is only significant for C programs because the C standard defines it as the entry point to a C program. It's the job of the linker to generate (at compile time) the code that will actually run when the program is started, which may involve things that happen before main() is called for the first time. The linker creates the "real" program entry point, _start, which is where the loader transfers control once it finishes its other preparations.

None of this is defined by the C standard and TBH I have no idea how much of it is defined by POSIX, so the previous three paragraphs should be taken as a brief and probably very inaccurate overview of how Linux does things, not as deep truths or principles of OS design.

tl;dr: It's complicated.

Edit: I didn't really make clear how this relates to command line arguments. Each stage -- shell, loader, and your compiled program -- is responsible for a different part of the setup, which includes the arguments that eventually get passed to main(). The shell reads them and passes them to execve(), which summons the loader, which puts them on the stack and starts the program, which (possibly) has other things to do before it actually passes them on to main(). Hope that's clear as mud. ;)

---

### Post by lisati on 2012-10-15
My understanding is that the values for argc & argv are filled in via code provided by the compiler and/or the language's run-time libraries, based on information provided by the OS

---

### Post by ssam on 2012-10-16
this is quite a detail explanation.

[http://eli.thegreenplace.net/2012/08/13/how-statically-linked-programs-run-on-linux/](http://eli.thegreenplace.net/2012/08/13/how-statically-linked-programs-run-on-linux/)

---

