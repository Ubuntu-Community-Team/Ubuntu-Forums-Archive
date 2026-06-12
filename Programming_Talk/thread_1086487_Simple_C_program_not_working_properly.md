---
title: "Simple C program not working properly"
date: 2009-03-04
forum: Programming Talk
---

### Post by alkamid on 2009-03-04
What's wrong with this code?
```
#include <stdio.h>
#include <conio.h>

main()
{
	char z;

	printf("Give me a letter: ");
	scanf("%c", &z);
	printf("The letter you gave me is: %c", z);
	getch();
}
```

When I compile it under Windows XP (Dev C++), I get what I want.
Under Ubuntu, I remove conio and getch(), then run
```
gcc test.c -o test
./test
```
It prints "Give me a letter: ", then I click a letter and ENTER, then the program crashes (it quits without executing the last instruction).

---

### Post by veda87 on 2009-03-04
its working properly for me.... i don't get any problem....

---

### Post by alkamid on 2009-03-04
Well, I suppose my Ubuntu is missing something (minimal install here).
Edit: I just added "printf("\n");" at the end of the program and it works fine.

I have another question. As it is another simple program, I write this in the same topic:
```
#include <stdio.h>

	main()
	{
		int c;
		float d;
		char t;
		char r[20];
		
		printf("Integer: ");
		scanf("%d", &c);
		printf("\nFloat: ");
		scanf("%f", &d);
		printf("\nCharacter: ");
		fflush(stdin);	
		scanf("%c", &t);
		printf("\nString: ");
		scanf("%s", r);
		printf("\nYour integer is %d", c);
		printf("\nCharacter you've chosen is: %c", t);
		printf("\n");

	}
```
Why it just skips "Character" part and goes directly to string? I thought it's because of standard input value, hence the "fflush" before.

---

### Post by sujoy on 2009-03-04
```
#include <stdio.h>

int main()
{
	int c;
	float d;
	char t;
	char r[20];
	
	printf("Integer: ");
	scanf("%d", &c);

	printf("\nFloat: ");
	scanf("%f", &d);

	printf("\nCharacter: ");
	scanf(" %c", &t);

	printf("\nString: ");
	scanf("%s", r);

	printf("\nYour integer is %d", c);
	printf("\nCharacter you've chosen is: %c", t);
	printf("\n");
	return 0;
}
```

you need to put a <space> before '%c'

from scanf 's manpage

%c -> The usual skip of leading white space is suppressed. To skip white  space  first,  use  an explicit space in the format.

i suppose pressing enter in the previous scanf causes this, but i am not sure why.

can anyone explain this ?

---

### Post by aishwarya on 2009-03-04
try like this...it works..
> #include <stdio.h>

        main()
        {
                int c;
                float d;
                char t;
                char r[20];

                printf("\nCharacter: ");
                t=getc(stdin);
                printf("\nString: ");
                scanf("%s", r);
                printf("Integer: ");
                scanf("%d", &c);
                printf("\nFloat: ");
                scanf("%f", &d);
                printf("\nYour integer is %d", c);
                printf("\nCharacter you've chosen is: %c", t);
                printf("\n");

        }


---

### Post by dwhitney67 on 2009-03-04
> **aishwarya said:**
> try like this...it works..

By reorganizing the code, you have "danced" around the problem the OP was having.

The issue is that when entering a value (int, float, double, etc) or a string, the newline is not used by the scanf() to fill the value.  Thus the newline remains on the input stream.  This affects the next call to scanf() or getc(), should the sought after input be a character.

My knowledge of using input/output format statements in C is fading over time, but here's a solution that not only prompts the user for the character, but also covers the application from a buffer overrun by using fgets() in lieu of scanf() to read in the string.
```

#include <stdio.h>
#include <string.h>

int main()
{
  int   i;
  float f;
  char  c;
  char  s[20];

  printf("String: ");
  //scanf("%s", s);              // <--- never use scanf() to read strings
  fgets(s, sizeof(s), stdin);
  if (strchr(s, '\n'))
  {
    s[ strlen(s) - 1 ] = '\0';
  }

  printf("Integer: ");
  scanf("%d", &i);

  printf("Float: ");
  scanf("%f%*c", &f);   // <--- gobble up undesired newline character

  printf("Character: ");
  scanf("%c", &c);

  printf("\nYour string is %s", s);
  printf("\nYour integer is %d", i);
  printf("\nYour float is %f", f);
  printf("\nCharacter you've chosen is: %c\n", c);

  return 0;
}

```

---

### Post by abhilashm86 on 2009-03-04
hey you wont need any conio.h under ubuntu, also getch()  means you are quitting after hitting a character, but you are seeing output at terminal, so new window is required as to turbo c in windows XP,
check out following

> 
#include <stdio.h>
main()
{
        char z;

        printf("Give me a letter: ");
        scanf("%c", &z);
        printf("The letter you gave me is: %c\n", z);

}
~                



abhilash@abhi:~$ gcc cpgm.c -o cpgm
abhilash@abhi:~$ ./cpgm
Give me a letter: a
The letter you gave me is: a

---

### Post by sujoy on 2009-03-04
> **dwhitney67 said:**
> By reorganizing the code, you have "danced" around the problem the OP was having.

The issue is that when entering a value (int, float, double, etc) or a string, the newline is not used by the scanf() to fill the value.  Thus the newline remains on the input stream.  This affects the next call to scanf() or getc(), should the sought after input be a character.

My knowledge of using input/output format statements in C is fading over time, but here's a solution that not only prompts the user for the character, but also covers the application from a buffer overrun by using fgets() in lieu of scanf() to read in the string.
```

#include <stdio.h>
#include <string.h>

int main()
{
  int   i;
  float f;
  char  c;
  char  s[20];

  printf("String: ");
  //scanf("%s", s);              // <--- never use scanf() to read strings
  fgets(s, sizeof(s), stdin);
  if (strchr(s, '\n'))
  {
    s[ strlen(s) - 1 ] = '\0';
  }

  printf("Integer: ");
  scanf("%d", &i);

  printf("Float: ");
  scanf("%f%*c", &f);   // <--- gobble up undesired newline character

  printf("Character: ");
  scanf("%c", &c);

  printf("\nYour string is %s", s);
  printf("\nYour integer is %d", i);
  printf("\nYour float is %f", f);
  printf("\nCharacter you've chosen is: %c\n", c);

  return 0;
}

```

yes fgets should always be used to input strings rather than scanf, but for character input, a simple space before '%c' does the job :)

---

### Post by alkamid on 2009-03-05
> **dwhitney67 said:**
> (...)covers the application from a buffer overrun by using fgets() in lieu of scanf() to read in the string.

Could you explain this part, please? Does scanf use all 20 places in the string table, which fgets does not? Or am I getting it wrong?

---

### Post by dwhitney67 on 2009-03-05
> **alkamid said:**
> Could you explain this part, please? Does scanf use all 20 places in the string table, which fgets does not? Or am I getting it wrong?

If the operator enters N-characters (where N >= 20) for their string, then scanf() will read N-characters and place them into the buffer, never knowing that the buffer is only 20-characters long.  If any variables on the stack had been declared after the buffer, it is probable that the data within them would be trashed if a buffer overrun occurs.

In C (and C++), when passing an array to a function, the function only sees a pointer to the array, but has no idea what is the allocated size for the array.  With fgets(), one is able to provide that bit of information, thus instructing fgets() to accept no more than N-1 characters for the buffer.  The last character is reserved for the null-termination byte.

---

### Post by alkamid on 2009-03-05
Thank you very much!

---

