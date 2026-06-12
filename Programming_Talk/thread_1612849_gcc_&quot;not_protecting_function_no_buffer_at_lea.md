---
title: "gcc &quot;not protecting function: no buffer at least 8 bytes long&quot;"
date: 2010-11-03
forum: Programming Talk
---

### Post by 65 mustang on 2010-11-03
I have enabled in gcc 4.5.1:
```

-fstack-protector
-Wstack-protector

```
and i get:
> warning: not protecting function: no buffer at least 8 bytes long

Problem:
I don't have a code example of what to look for to fix.  Could someone point me to a guide to fix this warning.  Another problem is the line number for the warning is on the int main() of the program.

:confused:

---

### Post by Tony Flury on 2010-11-03
[http://stackoverflow.com/questions/1629685/when-and-how-to-use-gccs-stack-protection-feature](http://stackoverflow.com/questions/1629685/when-and-how-to-use-gccs-stack-protection-feature)

Does that help ?

---

### Post by 65 mustang on 2010-11-04
> **Tony Flury said:**
> [http://stackoverflow.com/questions/1629685/when-and-how-to-use-gccs-stack-protection-feature](http://stackoverflow.com/questions/1629685/when-and-how-to-use-gccs-stack-protection-feature)

Does that help ?

Thanks for the reply.  I have seen that page and i was unable to find an example of what would cause this and how to fix it.

For example do i only need to worry about overflowing argv and argc? Or do i need to check all my local variables in main to see if they are getting a overflow?

Or is the compiler sending me on a wild goose chase because of a overflow somewhere else and is just defaulting out to the line number of the main?

---

### Post by dwhitney67 on 2010-11-04
Why don't you post your code (that is located in main()).

The compiler is not generating the warning for this trivial program:
```

int main(int argc, char** argv)
{
   return 0;
}

```
Thus it must be something else that you have coded.

---

### Post by 65 mustang on 2010-11-04
> **dwhitney67 said:**
> Why don't you post your code (that is located in main()).

The compiler is not generating the warning for this trivial program:
```

int main(int argc, char** argv)
{
   return 0;
}

```
Thus it must be something else that you have coded.

Unfortunately i cannot post my code.  Sorry.

---

### Post by Arndt on 2010-11-04
> **65 mustang said:**
> Unfortunately i cannot post my code.  Sorry.

Then try removing things until you have a minimal function with the problem, and see if you can post just that.

---

### Post by spjackson on 2010-11-04
> **dwhitney67 said:**
> Why don't you post your code (that is located in main()).

The compiler is not generating the warning for this trivial program:
```

int main(int argc, char** argv)
{
   return 0;
}

```Thus it must be something else that you have coded.
I haven't used these gcc options before; however, this program does produce the warning (gcc 4.4.3):
```

int main(int argc, char** argv)
{
   char x[3];
   return 0;
}

```gcc -fstack-protector -Wstack-protector  -o p p.c

What puzzles me though, is that from the man page I would expect -fstack-protector-all to get rid of the warning, but it doesn't.

---

### Post by johnl on 2010-11-04
> **65 mustang said:**
> I have enabled in gcc 4.5.1:
```

-fstack-protector
-Wstack-protector

```
and i get:


Problem:
I don't have a code example of what to look for to fix.  Could someone point me to a guide to fix this warning.  Another problem is the line number for the warning is on the int main() of the program.

:confused:

Hi,

It sounds to me like gcc is just telling you that it is not generating a stack-smashing protection code for this function, likely because there is no array on the stack (for a buffer overflow to occur from), or because the array on the stack falls below it's threshold, which is 8 bytes.

Options:
1. if your function does not have a stack-based array variable in it, ignore this warning.

2. if your function does have a stack-based array variable, with length less than 8, you can either increase the size of your array to 8 or more members, or pass **--param ssp-buffer-size=X** to gcc where **X** is the minimum buffer size you want to cause stack protection to be generated.

*I don't know what the overhead (if any) is of tweaking this parameter.*
e.g.

```

int main(int argc, char* argv[])
{
    char x[3];
    
    return 0;
}

// output
~$ gcc -Wall -fstack-protector -Wstack-protector -c test.c -o test.o
test.c:1: warning: not protecting function: no buffer at least 8 bytes long

~$ gcc -Wall -fstack-protector -Wstack-protector --param ssp-buffer-size=3 -c test.c -o test.o
<no warning>

```

---

### Post by 65 mustang on 2010-11-04
> **spjackson said:**
> 
What puzzles me though, is that from the man page I would expect -fstack-protector-all to get rid of the warning, but it doesn't.

```
-fstack-protector-all
```
Will enable even stricter stack protection.  Note this option is depreciated in gcc 4.5 which only has "-fstack-protector".

```
-Wno-stack-protector
```
This is what you are looking for to turn off the warnings.  But i don't want to turn them off.  I want to fix all of them.  :)

---

### Post by 65 mustang on 2010-11-04
> **johnl said:**
> Hi,
2. if your function does have a stack-based array variable, with length less than 8, you can either increase the size of your array to 8 or more members, or pass **--param ssp-buffer-size=X** to gcc where **X** is the minimum buffer size you want to cause stack protection to be generated.
[/code]

Thank you!  You got it!  The line generating the error was:
```
char test[6];
```
when i changed the size of the array to 8 the warning went away.
```
char test[8];
```

I now am wondering what the performance hit will be for setting it down to one:
> --param ssp-buffer-size=**1**

---

### Post by 65 mustang on 2010-11-04
Some info on the performance hit:
[https://groups.google.com/group/muc.lists.netbsd.port.i386/browse_thread/thread/a37bfdf0516639d1?hl=pt](https://groups.google.com/group/muc.lists.netbsd.port.i386/browse_thread/thread/a37bfdf0516639d1?hl=pt)

---

