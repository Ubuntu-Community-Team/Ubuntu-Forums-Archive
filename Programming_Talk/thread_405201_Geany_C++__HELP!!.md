---
title: "Geany C++  HELP!!"
date: 2007-04-09
forum: Programming Talk
---

### Post by Ch0p5t1ckB01 on 2007-04-09
Hi, I just recently started to use Geany. Previously using Bloodshed Dev-C++ and love it.
 When I was trying it out with a "Hello World" printf statement. My compiler gives me an error. Can someone help me out?

Here's my code:

#include <stdio.h>
#include <stdlib.h>
#include <conio.h>
main()
{
printf("Hello World");
system("pause");
}


This is the error I get:

gcc -Wall -c "untitled" (in directory: /home/ch0p5t1ckb01)
gcc: untitled: linker input file unused because linking not done
Compilation finished successfully.

Does not allow me to execute the file.

Any help is greatly appreciated!!

---

### Post by DoubleQuadword on 2007-04-09
> **Ch0p5t1ckB01 said:**
> Does not allow me to execute the file.

Because you're providing the 'compile only' option to the compiler. Try doing this:

```
gcc -Wall untitled
```

Please note the fact that this option '-c' is missing.

> **Ch0p5t1ckB01 said:**
> 
main()
{
printf("Hello World");
system("pause");
}


Try to declare your main function this way:

```

int main (int, char **) or int main (int, char*[])

```

Both arguments and the return type are important.

> **Ch0p5t1ckB01 said:**
> system("pause"); 

If you're planning to execute this application in Linux try to remove that line. 'Pause' is a Microsoft DOS command not a one supported in Bash.

Regards.

---

### Post by maddog39 on 2007-04-09
Um acutally its just because you didnt save the file before hand. You might want to use:
```
system("sleep 1");
```
for a replacement to the PAUSE command in dos.

---

### Post by samjh on 2007-04-10
Or else use getchar() instead of system("whatever").

With getchar() you just have to press a key, so you can stare at the greeting and feel really good for as long as you want. :p

---

### Post by slavik on 2007-04-10
press F9 to actually build the file (where it also links), F8 only compiles (to check for syntax errors)

and remove that system()/getcahr() nonsense, if you have latest geany it will put in appropriate wrapper code to keep the shell open.

---

### Post by Rosver on 2009-01-06
Wow, Slavik. I also had the same problem. Your solution works quick. Ha ha ha. I feel foolish for making such a small error.

---

### Post by efexD on 2009-01-06
PLEASE don't ever use system()

---

### Post by Zugzwang on 2009-01-07
> **efeXor said:**
> PLEASE don't ever use system()

Reason?

---

### Post by Sinkingships7 on 2009-01-07
> **Zugzwang said:**
> Reason?

Not cross-platform and relies too much on the outside world. Trivial and irrelevant for this situation, but foolish to use in a larger program where there's an alternative.

---

### Post by hundredwatt on 2009-01-07
> **Sinkingships7 said:**
> Not cross-platform and relies too much on the outside world. Trivial and irrelevant for this situation, but foolish to use in a larger program where there's an alternative.

Try this instead:
```

cout << "Press enter to continue..";
cin.get();
```

---

### Post by C_Bomb on 2010-12-23
okay, well what about clearing the screen and all the other functions?

I'm also new to C++ for Linux.

My program works perfectly fine in Windows, but in Linux I get errors to the system() commands.

---

