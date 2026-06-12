---
title: "printf several times to same place on terminal?"
date: 2007-12-13
forum: Programming Talk
---

### Post by monkeyking on 2007-12-13
Hi, I'm doing a program in c/c++, that needs to do billions of calculations.
It will end up taking some days to calculate.

It is simply an optimization, over all permutations.
each perm. takes like 5 minutes,
so I'd like to see which perm is currently being optimized.

Is there someway to update what has been written to the teminal?

I could always use something like ncurses,
but I really need something that works crossplatform.

Thanks in advance.

---

### Post by slavik on 2007-12-13
[php]#include <stdio.h>
#include <unistd.h>

int main(int argc, char** argv)
{
	printf("Hello World");
	//flush the stream so that it appears right away.
	fflush(stdout);
	sleep(5);
	//8 is the hex number for backspace (note that backspace moves the carret a space back and doesn't erase the letter).
	printf("%c%c%c%c%c-----",8,8,8,8,8);
	return 0;
}[/php]

---

### Post by monkeyking on 2007-12-13
Ok, that was easy,
thank you.
I hadn't realised that it could be done that simple.

I found the following somewhat more intuitive

```

printf("\b");//backspaces on char
printf("\r");//return to beginning of line

```

---

### Post by slavik on 2007-12-13
I was too lazy to look up the escape sequence :P

---

