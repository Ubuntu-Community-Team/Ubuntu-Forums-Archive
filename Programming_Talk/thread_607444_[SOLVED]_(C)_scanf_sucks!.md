---
title: "[SOLVED] (C) scanf sucks!"
date: 2007-11-08
forum: Programming Talk
---

### Post by Can+~ on 2007-11-08
I need to get an input in a console application. Normally, this would be a simple task with scanf (I know scanf is old, but I'm learning in my University, and they teach us that, looks like later we will use iostream). So my problem begins that I need to ask for a name, last name and phone number, but that name should contain spaces.

Normally, I use the following line:
> scanf("%[^\n]", &myvariable);

But under ubuntu this doesn't work, so I started looking for other functions, or workarounds:

> gets(&myvariable);
gets(); works nice, but for some reason, I have three gets' and the first is skipped, even if I use "fflush(stdin);".

So my question, what's the best way to eat an empty space from the input? either windows or linux with C.

Thanks in advance.

---

### Post by gradedcheese on 2007-11-08
Hmm...

```

#include <stdio.h>

int main(void)
{
        char buffer[128];

        if(scanf("%[^\n]", buffer) == 1)
                printf("I read: \"%s\"", buffer);
        return 0;
}

```

works fine for me when I enter input containing whitespace and press Enter.  Are you sure it "doesn't work"?

---

### Post by samjh on 2007-11-09
My gets() has no problem with spaces.

For example, this works fine with spaces:
```
#include <stdio.h>

int main(void)
{
	char firstname[30];
	char lastname[30];

	printf("Hi!  What is your first name? ");
	gets(firstname);					// First gets.

	printf("...and last name? ");
	gets(lastname);						// Second gets.

	printf("Hello, %s %s!\n", firstname, lastname);

	return 0;
}
```

---

### Post by public_void on 2007-11-09
Don't use gets. Quote from the [libc manual]("http://www.gnu.org/software/libc/manual/")
>  - Deprecated function: char * gets (char *S)

...

 *Warning:* The `gets' function is *very dangerous* because it
     provides no protection against overflowing the string S.  The GNU
     library includes it for compatibility only.  You should *always*
     use `fgets' or `getline' instead.  To remind you of this, the
     linker (if using GNU `ld') will issue a warning whenever you use
     `gets'.You should pay attention to warnings. In most cases, the compiler/linker knows best.
```
/tmp/ccSm8rHi.o: In function `main':
test.c:(.text+0x24): warning: the `gets' function is dangerous and should not be used.

```

---

### Post by Can+~ on 2007-11-09
Thank you for all the replies:

public_void:
Yes, I know is unsafe to use that function. But in this assignment, this doesn't matter.

For everyone else:
I discovered what the issue was. I was using "fflush(stdin);" to clear the buffer, but apparently, this didn't. For example:

The user comes from a menu screen where he selected a number and hit enter.

Case 1: fflush(stdin);
> fflush(stdin);
printf("Nombre del contacto (%d):\n", last);
scanf("%[^\n]", mainlist->name);

This, doesn't work at all. Instead of doing anything, it just jumps through out all the code.

Case 2: Using a getchar();
> buffdump = getchar();
printf("Nombre del contacto (%d):\n", last);
scanf("%[^\n]", mainlist->name);

Works surprisingly good! Looks like I'm gonna stick to getchar, create a special function that eats the \n.

:guitar:

And I also wonder, why gets receives a warning, since scanf sucks twice as much. It leaves the linefeed around in the buffer to screw the next input.

---

