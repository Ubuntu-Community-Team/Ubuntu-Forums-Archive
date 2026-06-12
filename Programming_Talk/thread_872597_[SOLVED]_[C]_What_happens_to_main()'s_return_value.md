---
title: "[SOLVED] [C] What happens to main()'s return value?"
date: 2008-07-28
forum: Programming Talk
---

### Post by nvteighen on 2008-07-28
Hi!

A possibly silly question: We all know in C, and C++, main() should always return an int. My question is, how do I catch that return value and pass it to another application? I guess the value should passed through the shell somehow... or is it possible to make a C code detect another application's (with popen()?) exit code?

Just curious... I'm not trying to do anything with it. I've been wondering on this because the gdb debugger prints main()'s return value after execution has finished.

Thanks!

---

### Post by lisati on 2008-07-28
I haven't had the opportunity to use it in a Linux environment yet (so I don't know the Linux equivalent) but in MS-DOS (and presumably Windows too) a batch file can use the ERRORLEVEL function to test the return code, and it is also available to calling programs.

---

### Post by dribeas on 2008-07-28
> **nvteighen said:**
> Hi!

A possibly silly question: We all know in C, and C++, main() should always return an int. My question is, how do I catch that return value and pass it to another application? I guess the value should passed through the shell somehow... or is it possible to make a C code detect another application's (with popen()?) exit code?

Not sure about C here, but in C++ actually returning a value is optional (main() is the only function that is not required to return even if it has a non-void return value, an implicit 0 is returned). That value is passed to whatever program started your application.

That is, if you launch the program from a shell, the shell will get the return value. Read your shell's man page to learn how to access that value. If you only care whether it succeeded (success is 0) in sh/bash you can test it with if:

```

#!/bin/sh
if myapp
then
   echo Execution succeeded
else
   echo Execution failed
fi

# or:
myapp && echo Success || echo Failed

```

---

### Post by samjh on 2008-07-28
Exit codes are typically used by scripts when running automated tasks.  If a program in the script fails, then the script will need to deal with the problem.

Generally if you are just running the program manually, nothing happens.

---

### Post by Bachstelze on 2008-07-28
You can use the special [font="Courier New"]$?[/font] shell variable to get the return value of the last process:

```
firas@nobue ~ % cat return0.c; ./return0; echo $?
int main(void)
{
        return 0;
}

0
firas@nobue ~ % cat return1.c; ./return1; echo $?
int main(void)
{
        return 1;
}

1

```

---

### Post by LaRoza on 2008-07-28
> **nvteighen said:**
> Hi!

A possibly silly question: We all know in C, and C++, main() should always return an int. My question is, how do I catch that return value and pass it to another application? I guess the value should passed through the shell somehow... or is it possible to make a C code detect another application's (with popen()?) exit code?

Just curious... I'm not trying to do anything with it. I've been wondering on this because the gdb debugger prints main()'s return value after execution has finished.

Thanks!

You'll see that all programs have an exit code (0 for success usually), and it is, in the shell, represented by $? (return value of last command). This is typically used in shell scripts. Technically, it is whatever value happens to be in that register, so if you don't have a return value (if main returns void) it will just have whatever happened to be in that register when the program ended.

---

### Post by nvteighen on 2008-07-28
Thanks to you all! I got it now (and played around with some shell scripts to test it).

Marking as solved.

---

