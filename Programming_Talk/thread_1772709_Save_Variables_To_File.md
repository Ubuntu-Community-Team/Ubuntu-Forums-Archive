---
title: "Save Variables To File?"
date: 2011-06-01
forum: Programming Talk
---

### Post by UBuntinator on 2011-06-01
Hello, I'm trying to write a c program to calculate the cost of candy(My Simple(ish)Project.).

He're is my source:

```

#include <stdio.h>

int main()
{
	int numcandy1; // declare a number variable
	int numcandy2; // declare a number variable
	int candy; // declare candy type
	double cost1; // declare a variable that can store decimals
	double cost2; // declare a variable that can store decimals
	double cash; // ask for amount of money
	char name; // ask for name
	printf("Hello, what's you're name?\n");
        scanf("%s", &name); // check cash
	printf("How much money do you have?\n");
        scanf("%lf", &cash); // check cash
        printf("If you want a lollipop, press one, if you want a cookie, press 2\n");
        scanf("%d", &candy); // select candy
        if (candy == 1)
        {
	printf("How many lollipops do you want: ");
	scanf("%d", &numcandy1); // get input from user
	cost1 = 0.25 * numcandy1; // do some math
	if (cash < cost1)
	{
	printf("You do not have enough money. sorry.\n");
	}
	else
	{
	printf("\nThat will cost %f. \n", cost1);
	}
	}
	else if (candy == 2)
	{
	printf("How many cookies do you want: ");
	scanf("%d", &numcandy2); // get input from user
	cost2 = 0.50 * numcandy2; // do some math
	if (cash < cost2)
	{
	printf("You do not have enough money. sorry.\n");
	}
	else
	{
	printf("\n That will cost %f.\n", cost2);
	}
	}
	FILE *fp;
      int i;
   
      fp = fopen("Data.txt", "");
      if (fp == NULL) {
         printf("Error. Could'nt Access File.\n");
      }
   
      for (i=0; i<=10; ++i)
         printf(name, "|", "%d, %d\n", candy "|", cost1 "|", cost2);
   
      return 0;
}
}

```

 And I get these error's with gcc:

Hello.c: In function ‘main’:
Hello.c:55: error: expected ‘)’ before string constant
Hello.c:55: warning: passing argument 1 of ‘printf’ makes pointer from integer without a cast
/usr/include/stdio.h:339: note: expected ‘const char * __restrict__’ but argument is of type ‘char’
Hello.c: At top level:
Hello.c:59: error: expected identifier or ‘(’ before ‘}’ token

I'm new to c, and have little experience in others. Can Someone help?

---

### Post by Some Penguin on 2011-06-01
Most people on the forum have better things to do than enter people's code into text editors so they can check the line numbers.

```

  printf(name, "|", "%d, %d\n", candy "|", cost1 "|", cost2);

```

That's never going to compile.  It's not the compiler's job to figure out to interpret something like 

```

candy "|"

```

for instance.  Start by reading the manual page for printf.

---

### Post by r-senior on 2011-06-01
Is your code really indented like that?

I tried pushing it through "indent". You might also like to consider the error message it gives:

```

$ indent -linux test.c
indent: test.c:59: Error:Stmt nesting error.

```

In other words, overall your braces don't match.

I know it's not a huge program but there's quite a long way to go to get this working. I'd genuinely suggest that you rewrite it a small part at a time and get each part working before you move onto the next.

---

### Post by dazman19 on 2011-06-01
Lets start at the top..

You want to put someones name. (which is more than 1 character I assume) into a piece of memory which has been declared as a single char?

1) this is not going to work.

I would use a size of about 80 characters.
char name[80];

then when using scanf to get a character array(string), you can put the value into the char using the name. you dont need the reference when useing %s. If you were getting an interger, then you would need to use %d and an &.

programming will be easier to learn if you take it in steps. Writing an entire program and then trying to figure out why it wont complile is generally harder than writing a part of a program, testing what you have written and then building on it.
When you get stuck you can ask, or check out the c/c++ libs.
```

#include <stdio.h>

int main() 
{
	char name[80];
	printf("please enter your name");
	scanf("%s", name);
	printf("%s", name);
}

```

---

### Post by Petrolea on 2011-06-01
> **UBuntinator said:**
> Hello, I'm trying to write a c program to calculate the cost of candy(My Simple(ish)Project.).

He're is my source:

```

#include <stdio.h>

int main()
{
	int numcandy1; // declare a number variable
	int numcandy2; // declare a number variable
	int candy; // declare candy type
	double cost1; // declare a variable that can store decimals
	double cost2; // declare a variable that can store decimals
	double cash; // ask for amount of money
	char name; // ask for name
	printf("Hello, what's you're name?\n");
        scanf("%s", &name); // check cash
	printf("How much money do you have?\n");
        scanf("%lf", &cash); // check cash
        printf("If you want a lollipop, press one, if you want a cookie, press 2\n");
        scanf("%d", &candy); // select candy
        if (candy == 1)
        {
	printf("How many lollipops do you want: ");
	scanf("%d", &numcandy1); // get input from user
	cost1 = 0.25 * numcandy1; // do some math
	if (cash < cost1)
	{
	printf("You do not have enough money. sorry.\n");
	}
	else
	{
	printf("\nThat will cost %f. \n", cost1);
	}
	}
	else if (candy == 2)
	{
	printf("How many cookies do you want: ");
	scanf("%d", &numcandy2); // get input from user
	cost2 = 0.50 * numcandy2; // do some math
	if (cash < cost2)
	{
	printf("You do not have enough money. sorry.\n");
	}
	else
	{
	printf("\n That will cost %f.\n", cost2);
	}
	}
	FILE *fp;
      int i;
   
      fp = fopen("Data.txt", "");
      if (fp == NULL) {
         printf("Error. Could'nt Access File.\n");
      }
   
      for (i=0; i<=10; ++i)
         printf(name, "|", "%d, %d\n", candy "|", cost1 "|", cost2);
   
      return 0;
}
}

```

 And I get these error's with gcc:

Hello.c: In function ‘main’:
Hello.c:55: error: expected ‘)’ before string constant
Hello.c:55: warning: passing argument 1 of ‘printf’ makes pointer from integer without a cast
/usr/include/stdio.h:339: note: expected ‘const char * __restrict__’ but argument is of type ‘char’
Hello.c: At top level:
Hello.c:59: error: expected identifier or ‘(’ before ‘}’ token

I'm new to c, and have little experience in others. Can Someone help?

Wow, you sure got a mess here. Printf isn't print like in Java or PHP, you can't just put a variable and then braces and repeat this 3 times. First, you tell printf where to put your variables, then put their names in correct order: printf("%d%d", a, b) - would print a and b. First %d is for a, second is for b (assuming they are integers).

When declaring a char, if not stated otherwise, it will always use 1 as capacity. So if you store 20 characters into that variable it won't work. Use strings or arrays for that.

Take a good look at C/C++ variables as it is a big problem for beginners to understand them.

---

