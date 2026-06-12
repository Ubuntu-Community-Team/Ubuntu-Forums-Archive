---
title: "C Question"
date: 2007-08-12
forum: Programming Talk
---

### Post by DerangedDingo on 2007-08-12
I was trying to make a simple C program that converts a character to hex or to ASCII, by giving you the choice (although I'm not sure if it's possible to convert a key to hex.. I don't know much about it)

I'm getting the warning: ```
Convert.c:21: warning: passing argument 1 of &#8216;atoi&#8217; makes pointer from integer without a cast

```
It's just a warning, so the program compiles, but then it crashes immediately after printing "You pressed the blah character"

Here's the source: ```
/* Small program for converting values. My first attempt at 'if' and I haven't read the chapter that introduces it. I just skipped over to find the format.
<stdlib.h> is for atoi, though I think my version of gcc doesn't need that library
Made by DerangedDingo */

#include <stdio.h>
#include <stdlib.h>    


int main()
{
  char key;
  char num; 
  int decide;

	printf("Press a key you want converted to ASCII or hex. ");
	key=getchar();

	printf("The %c key was entered.\n",key);
	printf("Press 1 if you want ASCII, 2 for hex. ");
	num=getchar();
	decide=atoi(num);

	if(decide==1) 
	{
	printf("The value of %c in ASCII is %i.\n",key,key);
	}
	if(decide==2)
	{
	printf("The value of %c in hexadecimal is %x.\n",key,key);
	}
  
  return(0);
}

```

Would anyone here be kind enough to point out the problem for me?
I don't fully understand the warning message gcc gives
Thanks

(My guess is it's something with my variables)

---

### Post by heimo on 2007-08-12
Here's debugging tip. ;-) Simplify your program, comment out parts from the end of the program until it works as expected. Then modify it to just read two characters in sequence (without ifs) and print out numerical values of those characters. Figure out what's wrong with your original program.

---

### Post by lloyd_b on 2007-08-12
From the atoi() man page:
```
int atoi(const char *nptr);

The  atoi() function converts the initial portion of the string pointed
to by nptr to int.

```

Please note the type of argument that atoi() is expecting, and compare that to the type of argument you're passing it...

Lloyd B.

---

### Post by bapoumba on 2007-08-12
Moved to "Programming Talk".

---

