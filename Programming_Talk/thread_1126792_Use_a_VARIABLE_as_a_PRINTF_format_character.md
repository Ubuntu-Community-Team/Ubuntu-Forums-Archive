---
title: "Use a VARIABLE as a PRINTF format character?"
date: 2009-04-15
forum: Programming Talk
---

### Post by Krupski on 2009-04-15
Hi all,

Simple question... is it possible to use a variable as a formatting character for PRINTF?

Look at this code (specifically the part in red):

```

// memory.c
// show how data is stored in memory

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define TYPE long int

char *readln(FILE*);

int main(int argc, char *argv[])
{
	union {
		TYPE num;
		unsigned char c[sizeof(TYPE)];
	} count;

	double n;
	int i;
	char buffer[BUFSIZ];

	fprintf(stdout, "Enter a number: ");
	strcpy(buffer, readln(stdin));

	n = atof(buffer);
	count.num = (n < 0) ? (n - 0.5) : (n + 0.5);

	fprintf(stdout,	"\nThe original number is: 0x[COLOR="Red"]**%016X**[/COLOR]\n", count.num);

	fprintf(stdout,	"\nIn memory, the data is: 0x");

	for(i = 0; i < (int)sizeof(TYPE); i++) {
		fprintf(stdout,	"%02X",
		count.c[i]);
	}

	fprintf(stdout, "\n\n");
	return 0;
}


char *readln(FILE *fp)
{
	char buf[BUFSIZ];
	char *p1;
	int len;

	buf[0] = 0;
	fgets(buf, BUFSIZ, fp);
	len = strlen(buf);

	while(len >= 0) {
		if (buf[len] == 32 ||
			buf[len] == 13 ||
			buf[len] == 10 ||
			buf[len] ==  9 ||
			buf[len] ==  0) { buf[len] = 0; len--; }
		else { break; }
	}

	len++;
	buf[len] = 0;
	p1 = buf;
	return p1;
}

```

The output of this program is something like:

```

root@michael:~/c-progs# ./memory 
Enter a number: 10000

The original number is: 0x0000000000002710

In memory, the data is: 0x1027000000000000


```

Note that because I'm examining a long int, I know it's going to take 8 bytes and therefore I print 16 hex digits (each hex digits being 2 characters = 16).

I'm able to use sizeof() in other parts of the program, but I don't know how to do it for PRINTF.

I would like to have a formatting string something like "%0(sizeof(TYPE)*2)X", but obviously this doesn't work. :)

I want to expand this program to show chars, ints, long ints, floats, doubles, etc... and automatically print the proper number of characters.

Any way this can be done?

Thanks in advance!

-- Roger

---

### Post by kknd on 2009-04-15
You can build the format string first, using sprintf for example, and then passing it as the format for the printf, like:

```

char* buffer[20];
sprintf(buffer, "your dynamic format");
printf(buffer, yourvar);

```

---

### Post by odyniec on 2009-04-15
You can use snprintf() to insert the proper size into the format string:
```
char format[100];

/* ... */

snprintf(format, 100, "\nThe original number is 0x%%0%dX\n", sizeof(TYPE)*2);
fprintf(stdout, format, count.num);
```

---

### Post by Krupski on 2009-04-15
> **odyniec said:**
> You can use snprintf() to insert the proper size into the format string:
```
char format[100];

/* ... */

snprintf(format, 100, "\nThe original number is 0x%%0%dX\n", sizeof(TYPE)*2);
fprintf(stdout, format, count.num);
```

AH!!!!! I see! Thank you so much to **odyniec** and **kknd**!

That's exactly what I needed. Thank you both! [IMG]http://www.gunsnet.net/forums/images/smilies/xyxthumbs.gif[/IMG]

---

### Post by happyhamster on 2009-04-15
Also possible:

```

int width = sizeof(TYPE) * 2;
..
..
fprintf(stdout,	"\nThe original number is: 0x%0*X\n", width, count.num);

```

---

### Post by Krupski on 2009-04-15
> **happyhamster said:**
> Also possible:

```

int width = sizeof(TYPE) * 2;
..
..
fprintf(stdout,	"\nThe original number is: 0x%0*X\n", width, count.num);

```

Now how did I miss that? It's right on page 154 of "THE" book (Kernighan & Ritchie's "The C Programming Language" book).

Thanks!

---

