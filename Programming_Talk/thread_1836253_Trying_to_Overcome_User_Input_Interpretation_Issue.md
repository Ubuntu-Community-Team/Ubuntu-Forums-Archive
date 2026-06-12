---
title: "Trying to Overcome User Input Interpretation Issues in C"
date: 2011-08-30
forum: Programming Talk
---

### Post by kevinharper on 2011-08-30
I've posted a few versions of hangman and have come a long way since the first one, I think. My biggest issue now is properly handling and checking user input. Before my first version of hangman, I created a few other simpler programs. Here is the source to one of them.
```

/* area_of_geometrical_shapes.c
   By: Kevin Harper :: Date: Aug 30th, 2011
   Program calculates the area of various geometrical shapes. */

#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>
#include <string.h>
#include <ctype.h>

/* constant declarations */
#define NUM_SHAPES 3 /* number of shapes for which this program
				can find areas */
#define PI 3.14
#define MAX 255

/* function prototypes */
void	clrscrn(void);
void	clrstdin(void);
int	display_main_menu(void);
bool	is_float(const char *);
int	area_of_circle(void);
int	area_of_rectangle(void);
int	area_of_square(void);

int main(void)
{
	clrscrn();

	for (;;)
	{
		switch(display_main_menu())
		{
			default:
				exit(EXIT_SUCCESS);
			case 1:
			{
				area_of_circle();
				break;
			}
			case 2:
			{
				area_of_rectangle();
				break;
			}
			case 3:
			{
				area_of_square();
				break;
			}
		}

	}

	return EXIT_SUCCESS;
}
/* clrscrn() clears terminal by inserting 30 blank lines */
void clrscrn(void)
{
	for (int x = 0; x < 30; x++ )
		printf("\n");
}

/* clrstdin() clears stdin stream */
void clrstdin(void)
{
	int ch = 0;

	while ((ch = getchar()) != '\n' && ch != EOF)
		;
}

/* main_menu() prompts user to enter the shape with which he/she
	would like to work */
int display_main_menu(void)
{
	int menu_choice = NUM_SHAPES + 1;

	while (menu_choice < 0 || menu_choice > NUM_SHAPES)
	{
		/* prompts user
			explains what program does */
		printf("\n");
		puts("===============================================================");
		puts("This program calculates the area of various geometrical shapes.");
		puts("Please type the number that corresponds to the shape whose");
		puts("\tarea you wish to calculate and press the \"Enter\" key.");
		puts("NOTE: Each shape requires you to enter different information");
		puts("\t(ie: for a circle, you will need to enter the radius");

		/* Menu options */
		puts("1 for circle");
		puts("2 for rectangle");
		puts("3 for square");
		printf("\n");
		puts("0 to quit");
		menu_choice = getchar() - 0x30;

		clrstdin();
	}

	return menu_choice;
}

/* check_is_flat() gets input string and checks each character
	to make sure it is either a number or a period.
   the function returns false (invalid float) if a non-digit, or
	more than one period is encountered. */
bool check_is_float(const char *b)
{
	int b_length = strlen(b);
	int periods = 0;

	/* if user only entered a period, flag input as invalid */
	if (b_length == 1 && b[0] == '.')
		return false;

	for (int i = 0; i < b_length; i++ )
	{
		/* if character is not a letter or a period,
			flag as invalid */
		if (!isdigit(b[i]) && b[i] != '.')
			return false;
		/* if character is a period, set period count to 1. */
		if (b[i] == '.')
			periods++;

		/* user input can have, at most, 1 period.
			if a second one is encountered, mark invalid */
		if (periods < 2)
			continue;
		else
			return false;
	}

	return true;
}

/* area_of_circle() calculates the area of a circle
   user inputs radius */
int area_of_circle(void)
{
	char buf[MAX], *newline;
	bool is_float = false;
	double radius = 0.0;

	clrscrn();

	while (!is_float)
	{
		puts( "You have chosen to calculate the area of a circle." );
		puts( "To go back to the main menu, type \"0\" and press \"Enter\"." );
		printf( "What is the radius?\n(Type and press the \"Enter\" key) " );
		fgets(buf, sizeof(buf), stdin);
		newline = strchr(buf, '\n'); /* check for trailing newline char */

		if (newline)
			*newline = '\0';   /* replace newline with a null character */
		is_float = check_is_float(buf);
		if(!is_float)
		{
			clrscrn();
			puts("You've entered something unexpected.");
			puts("Please enter a number.");
		}
	}

	radius = strtod(buf, NULL);

	if (radius == 0)
		return 0;
	else
	{
		clrscrn();

		/* FORMULA AREA OF A CIRCLE: A = pi * r^2 */
		printf("The area of a circle with the radius you entered is %f", PI * radius * radius);
	}

	return 0;
}

/* area_of_rectangle() calculates the area of a rectangle
	user inputs length & width */
int area_of_rectangle(void)
{
	char buf[MAX], *newline;
	float length = 0, width  = 0;
	bool is_float = false;

	while (!is_float)
	{
		puts( "You have chosen to calculate the area of a rectangle." );
		puts( "To go back to the main menu, type \"0\" and press \"Enter\"." );
		printf( "What is the length (side 1) of the rectangle?\n(Type and press the \"Enter\" key) " );
		fgets(buf, sizeof(buf), stdin);
		newline = strchr(buf, '\n'); /* check for trailing newline char */

		if (newline)
			*newline = '\0';   /* replace newline with a null character */
		is_float = check_is_float(buf);
		if (!is_float)
		{
			clrscrn();
			puts("You've entered something unexpected.");
			puts("Please enter a number.");
		}
	}

	length = strtod(buf, NULL);

	if (length == 0)
		return 0;

	is_float = false;

	while (!is_float)
	{
		printf( "What is the width (side 2) of the rectangle?\n(Type and press the \"Enter\" key) " );
		fgets(buf, sizeof(buf), stdin);
		newline = strchr(buf, '\n');

		if (newline)
			*newline = '\0';

		is_float = check_is_float(buf);
		if (!is_float)
		{
			clrscrn();
			puts("You've entered something unexpected.");
			puts("Please enter a number.");
		}
	}

	width = strtod(buf, NULL);

	if (width == 0)
		return 0;
	else
	{
		clrscrn();

		/* FORMULA AREA OF RECTANGLE: A = length * width */
		 printf( "The area of a rectangle with the length and width you provided is: %f", length * width );
	}

	return 0;
}

/* area_of_square() calculates the area of a square
	user inputs the length of one side */
int area_of_square(void)
{
	char buf[MAX], *newline;
	float length = 0;
	bool is_float = false;

	while (!is_float)
	{
		puts( "You have chosen to calculate the area of a square." );
		puts( "To go back to the main menu, type \"0\" and press \"Enter\"." );
		printf( "What is the length of one of the sides of the square?\n(Type and press the \"Enter\" key) " );
		fgets(buf, sizeof(buf), stdin);
		newline = strchr(buf, '\n'); /* check for trailing newline char */

		if (newline)
			*newline = '\0';   /* replace newline with a null character */
		is_float = check_is_float(buf);
		if (!is_float)
		{
			clrscrn();
			puts("You've entered something unexpected.");
			puts("Please enter a number.");
		}
	}

	length = strtod(buf, NULL);

	if (length == 0)
		return 0;
	else
	{
		clrscrn();

		/* FORMULA AREA OF SQUARE: A = length * length */
		 printf( "The area of a square with the length provided is: %f", length * length );
	}

	return 0;
}

```
It displays a menu and asks the user to select a shape for which he/she would like the area. The program then goes to his/her selection, asks for certain input and calculates the area.

This is a second version. My first had no input checks at all - it assumed the user entered ints when prompted (and nothing else).

Am I wrong in using "fgets" and then checking the string and then converting to double? This is how I've made sure that what the user enters is, indeed, a float value.

Also... is there a way to dinamically format trailing zero's in output? Say, user enters 8 and 1.1 for a rectangle. Is there a way to ONLY display 8.8? But if user enters 1 and 8.888 have it print 8.888.

---

### Post by Bachstelze on 2011-08-30
Your check_is_float function is not necessary. Just run sscanf on the string and check its return value to know whether the conversion suceeded or not.

---

### Post by Longinus00 on 2011-08-30
> **kevinharper said:**
> Also... is there a way to dinamically format trailing zero's in output? Say, user enters 8 and 1.1 for a rectangle. Is there a way to ONLY display 8.8? But if user enters 1 and 8.888 have it print 8.888.

Just parse the sigfigs from the input string and use that for printf's precision.

---

### Post by dwhitney67 on 2011-08-30
@ kevinharper -

Aside from the worthy advice to use sscanf(), also make sure that inputs that pertain to *dimensions* are greater than or equal to 0.

Here's a small program that demonstrates sscanf() in action.
```

#include <stdio.h>
#include <string.h>
#include <stdbool.h>

int main(void)
{
   double value;
   bool   inputGood = false;

   while (!inputGood)
   {
      char input[80];
      char garbage[80];

      printf("Enter a number greater than or equal to zero: ");

      if (fgets(input, sizeof input, stdin))
      {
         char* newline = strchr(input, '\n');

         if (newline)
         {
            *newline = '\0';
         }

         if (sscanf(input, "%lf%s", &value, garbage) == 1 && value >= 0.0)
         {
            inputGood = true;
         }
         else
         {
            printf("Invalid input; try again...\n\n");
         }
      }
      else
      {
         printf("\nInput aborted; try again...\n\n");
      }
   }

   /* do something with 'value' */
   printf("You entered: %lf\n", value);

   return 0;
}

```

P.S.  When comparing a double or float to a hard-coded value (such as I have shown above), there are risks that the stored floating point value is not "exactly" equal to what was inputted.  Thus it is wise to perform comparisons using a certain known precision, rather than depend on the system to make the raw determination.

Also, in case you are wondering about the use of the 'garbage' variable above, it is to catch erroneous input; for example "1.2.3", or "1.2abc", etc.

---

### Post by Arndt on 2011-08-30
> **kevinharper said:**
> 

```

#define PI 3.14


```


There is a symbol M_PI in <math.h>.

---

### Post by Bachstelze on 2011-08-31
> **Arndt said:**
> There is a symbol M_PI in <math.h>.

Not standard C, though. With glibc and -std=c99, it won't be defined.

---

### Post by Arndt on 2011-08-31
> **Bachstelze said:**
> Not standard C, though. With glibc and -std=c99, it won't be defined.

Apparently, you can obtain it by using --std=gnu99. The gcc man page says

```
           gnu99
           gnu9x
               GNU dialect of ISO C99.  When ISO C99 is fully implemented in
               GCC, this will become the default.  The name gnu9x is
               deprecated.

```

This seems to indicate that gcc without any --std option will continue to support M_PI, so we can continue using it from math.h, unless there are special requirements of using exactly C99 and no extensions.

---

### Post by Bachstelze on 2011-08-31
> **Arndt said:**
> 
This seems to indicate that gcc without any --std option will continue to support M_PI, so we can continue using it from math.h, unless there are special requirements of using exactly C99 and no extensions.

No, you got it backwards. We must not rely on M_PI being provided by the platform unless there is an explicit requirement to target only POSIX systems (since M_PI is a POSIX extension). Of course we can always do

```
#ifndef M_PI
#define M_PI 3.14159265358979323846
#endif
```

and then we can use it everywhere.

---

### Post by Arndt on 2011-08-31
> **Bachstelze said:**
> No, you got it backwards. We must not rely on M_PI being provided by the platform unless there is an explicit requirement to target only POSIX systems (since M_PI is a POSIX extension). Of course we can always do

```
#ifndef M_PI
#define M_PI 3.14159265358979323846
#endif
```

and then we can use it everywhere.

If the platform does not support POSIX, we will have many more portability problems. Are you thinking of embedded operating systems? Do you have an actual example?

---

### Post by Bachstelze on 2011-08-31
> **Arndt said:**
> If the platform does not support POSIX, we will have many more portability problems.

Of what kind, please?

> Are you thinking of embedded operating systems? Do you have an actual example?

No. I'm thinking of, you know, an OS that has something like a 95% market share. Besides, I'm sorry but I program in C, not in a GNU dialect, so I always use -std=c99 and M_PI is not defined.

---

### Post by kevinharper on 2011-08-31
> Your check_is_float function is not necessary. Just run sscanf on the string and check its return value to know whether the conversion suceeded or not.
sscanf() keeps being suggested in my examples. @dwhitney67 Thank you for your example. I will go through it carefully and also get acquainted w/ sscanf() in general.

> make sure that inputs that pertain to dimensions are greater than or equal to 0. Currently, user input of 0 for any dimension that represent a length (radius, length, width, etc) kicks user back to the main menu. And, from the main menu, input of 0 exits the program.

>  When comparing a double or float to a hard-coded value (such as I have shown above), there are risks that the stored floating point value is not "exactly" equal to what was inputted. Thus it is wise to perform comparisons using a certain known precision, rather than depend on the system to make the raw determination.

Also, in case you are wondering about the use of the 'garbage' variable above, it is to catch erroneous input; for example "1.2.3", or "1.2abc", etc.Will take a little time to digest this.

> There is a symbol M_PI in <math.h>. I couldn't fully follow your guys' discussion about the OSs. But I chose to declare a PI constant because the place where I got the idea for this program suggested it.

This brings up a doubt I've had every time I declare a MAX constant. gedit colors it pink as if it was a reserved keyword/constant or something. Should I not do:
```

#define MAX 255
[/CODE}
Should I choose a different name for that constant? I usually use it when declaring arrays
[CODE]
char array[MAX];

```

---

### Post by karlson on 2011-08-31
> **kevinharper said:**
>  Should I not do:
```

#define MAX 255

```
Should I choose a different name for that constant? I usually use it when declaring arrays
```

char array[MAX];

```

Make the constant Name a little more descriptive.

---

### Post by Arndt on 2011-08-31
> **Bachstelze said:**
> Of what kind, please?



For example threads, signals, subprocesses, pipes, time, sockets. I grant you you can write a useful portable numerical program without any of these, and maybe that's your main activity, but in system programming, you need a richer interface to the operating system.

See "man standards".
> 

No. I'm thinking of, you know, an OS that has something like a 95% market share.

Surely it has a name? If you google a little, you will see that there are solutions there too.

---

### Post by Bachstelze on 2011-08-31
> **Arndt said:**
> For example threads, signals, subprocesses, pipes, time, sockets. I grant you you can write a useful portable numerical program without any of these, and maybe that's your main activity, but in system programming, you need a richer interface to the operating system.

See "man standards".


Surely it has a name? If you google a little, you will see that there are solutions there too.

I don't know if you're serious or just trying to argue for the sake of arguing. Do you see threads, signals, subprocesses, pipes or sockets used here? No. If you use them, then it might be necessary to make assumptions about the OS. Here, it is not.

*EDIT:* And I know about "man standards", thank you very much. Unlike you, though, I do not feel the need to require POSIX when it is absolutely unnecessary.

---

### Post by kevinharper on 2011-08-31
> if (sscanf(input, "%lf%s", &value, garbage) == 1 && value >= 0.0)

sscanf(), in this case, looks through string input for a long float and places it in value, and throws the remaining chars (that do not belong to the float) into garbage? I'm assuming that the scanf() function-family returns 1 if completed without error. value >= 0.0 is added on there because no length can be 0, right?

Wow.. seems like a simplified version of what I did w/ fgets() and the function to check it.

Will consider this in the future.. thanks a lot!

Back to a more focused question about the topic of this thread...
Can you guys find an instance that I did not check for? Can user input break this code or produce unexpected results? Did I cover my bases?

---

### Post by Bachstelze on 2011-08-31
> **kevinharper said:**
>  I'm assuming that the scanf() function-family returns 1 if completed without error.

Don't assume, look at the man page, that's what it's for!

> value >= 0.0 is added on there because no length can be 0, right?

No, it is to check whether the value entered is positive (because a negative distance is absurd), and if it is not, treat it as invalid input.


> Back to a more focused question about the topic of this thread...
Can you guys find an instance that I did not check for? Can user input break this code or produce unexpected results? Did I cover my bases?

Will look at it after dinner.

---

### Post by kevinharper on 2011-08-31
> Will look at it after dinner.
bon appetit

> No, it is to check whether the value entered is positiveI said this in a very dumb way... but is what I meant.

---

### Post by kevinharper on 2011-08-31
> **Bachstelze said:**
> Don't assume, look at the man page, that's what it's for!
Couldn't find it in man page so I posted the assumption here.

But just read that "On success, the function returns the number of variables filled.".

Sadly.... I just found it in man page.

---

### Post by Bachstelze on 2011-08-31
> **kevinharper said:**
> Couldn't find it in man page so I posted the assumption here.

```
man sscanf
```

If you don't have it, install the package manpages-dev.

---

### Post by Bachstelze on 2011-08-31
```
menu_choice = getchar() - 0x30;
```

This is bad. Once again, you assume that the input will be a digit, there is no reason to assume this.

---

### Post by Arndt on 2011-08-31
> **Bachstelze said:**
> I don't know if you're serious or just trying to argue for the sake of arguing. Do you see threads, signals, subprocesses, pipes or sockets used here? No. If you use them, then it might be necessary to make assumptions about the OS. Here, it is not.

*EDIT:* And I know about "man standards", thank you very much. Unlike you, though, I do not feel the need to require POSIX when it is absolutely unnecessary.

My original point, and it remains, is that M_PI is there if you want it. If you don't, you don't have to. If nothing else, you can copy its value from math.h if you want to define it yourself.

---

### Post by Bachstelze on 2011-08-31
> **Arndt said:**
> My original point, and it remains, is that M_PI is there if you want it.

You are assuming a POSIX system *and* that OP is willing to program in a language that is close to C, but not quite the real thing. Never in OP is it mentioned, therefore the assumption is unreasonable.

*EDIT:* Now if OP says "I don't care about non-POSIX systems and I don't mind the GNU extensions that conflict with the C standard", then it's fine. But he has not said it, so don't pull an Apple and think you know better than him what he wants to do.

---

### Post by kevinharper on 2011-08-31
This is the updated version:
```

/* area_of_geometrical_shapes.c
   By: Kevin Harper :: Date: Aug 30th, 2011
   Program calculates the area of various geometrical shapes. */

#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>
#include <string.h>
#include <ctype.h>

/* constant declarations */
#define NUM_SHAPES 3 /* number of shapes for which this program
				can find areas */
#define PI 3.14
#define MAX 255

/* function prototypes */
void	clrscrn(void);
void	clrstdin(void);
int	display_main_menu(void);
bool	is_float(const char *);
int	area_of_circle(void);
int	area_of_rectangle(void);
int	area_of_square(void);

int main(void)
{
	clrscrn();

	for (;;)
	{
		switch(display_main_menu())
		{
			default:
				exit(EXIT_SUCCESS);
			case 1:
			{
				area_of_circle();
				break;
			}
			case 2:
			{
				area_of_rectangle();
				break;
			}
			case 3:
			{
				area_of_square();
				break;
			}
		}

	}

	return EXIT_SUCCESS;
}
/* clrscrn() clears terminal by inserting 30 blank lines */
void clrscrn(void)
{
	for (int x = 0; x < 30; x++ )
		printf("\n");
}

/* clrstdin() clears stdin stream */
void clrstdin(void)
{
	int ch = 0;

	while ((ch = getchar()) != '\n' && ch != EOF)
		;
}

/* main_menu() prompts user to enter the shape with which he/she
	would like to work */
int display_main_menu(void)
{
	int menu_choice = NUM_SHAPES + 1;

	while (menu_choice < 0 || menu_choice > NUM_SHAPES)
	{
		/* prompts user
			explains what program does */
		printf("\n");
		puts("===============================================================");
		puts("This program calculates the area of various geometrical shapes.");
		puts("Please type the number that corresponds to the shape whose");
		puts("\tarea you wish to calculate and press the \"Enter\" key.");
		puts("NOTE: Each shape requires you to enter different information");
		puts("\t(ie: for a circle, you will need to enter the radius");

		/* Menu options */
		puts("1 for circle");
		puts("2 for rectangle");
		puts("3 for square");
		printf("\n");
		puts("0 to quit");
		menu_choice = getchar();
		clrstdin();

		if (isdigit(menu_choice) && menu_choice != EOF)
			menu_choice -= 0x30;
	}

	return menu_choice;
}

/* check_is_flat() gets input string and checks each character
	to make sure it is either a number or a period.
   the function returns false (invalid float) if a non-digit, or
	more than one period is encountered. */
bool check_is_float(const char *b)
{
	int b_length = strlen(b);
	int periods = 0;

	/* if user only entered a period, flag input as invalid */
	if (b_length == 1 && b[0] == '.')
		return false;

	for (int i = 0; i < b_length; i++ )
	{
		/* if character is not a letter or a period,
			flag as invalid */
		if (!isdigit(b[i]) && b[i] != '.')
			return false;
		/* if character is a period, set period count to 1. */
		if (b[i] == '.')
			periods++;

		/* user input can have, at most, 1 period.
			if a second one is encountered, mark invalid */
		if (periods < 2)
			continue;
		else
			return false;
	}

	return true;
}

/* area_of_circle() calculates the area of a circle
   user inputs radius */
int area_of_circle(void)
{
	char buf[MAX], *newline;
	bool is_float = false;
	double radius = 0.0;

	clrscrn();

	while (!is_float)
	{
		puts( "You have chosen to calculate the area of a circle." );
		puts( "To go back to the main menu, type \"0\" and press \"Enter\"." );
		printf( "What is the radius?\n(Type and press the \"Enter\" key) " );
		fgets(buf, sizeof(buf), stdin);
		newline = strchr(buf, '\n'); /* check for trailing newline char */

		if (newline)
			*newline = '\0';   /* replace newline with a null character */
		is_float = check_is_float(buf);
		if(!is_float)
		{
			clrscrn();
			puts("You've entered something unexpected.");
			puts("Please enter a number.");
		}
	}

	radius = strtod(buf, NULL);

	if (radius == 0)
		return 0;
	else
	{
		clrscrn();

		/* FORMULA AREA OF A CIRCLE: A = pi * r^2 */
		printf("The area of a circle with the radius you entered is %f", PI * radius * radius);
	}

	return 0;
}

/* area_of_rectangle() calculates the area of a rectangle
	user inputs length & width */
int area_of_rectangle(void)
{
	char buf[MAX], *newline;
	float length = 0, width  = 0;
	bool is_float = false;

	while (!is_float)
	{
		puts( "You have chosen to calculate the area of a rectangle." );
		puts( "To go back to the main menu, type \"0\" and press \"Enter\"." );
		printf( "What is the length (side 1) of the rectangle?\n(Type and press the \"Enter\" key) " );
		fgets(buf, sizeof(buf), stdin);
		newline = strchr(buf, '\n'); /* check for trailing newline char */

		if (newline)
			*newline = '\0';   /* replace newline with a null character */
		is_float = check_is_float(buf);
		if (!is_float)
		{
			clrscrn();
			puts("You've entered something unexpected.");
			puts("Please enter a number.");
		}
	}

	length = strtod(buf, NULL);

	if (length == 0)
		return 0;

	is_float = false;

	while (!is_float)
	{
		printf( "What is the width (side 2) of the rectangle?\n(Type and press the \"Enter\" key) " );
		fgets(buf, sizeof(buf), stdin);
		newline = strchr(buf, '\n');

		if (newline)
			*newline = '\0';

		is_float = check_is_float(buf);
		if (!is_float)
		{
			clrscrn();
			puts("You've entered something unexpected.");
			puts("Please enter a number.");
		}
	}

	width = strtod(buf, NULL);

	if (width == 0)
		return 0;
	else
	{
		clrscrn();

		/* FORMULA AREA OF RECTANGLE: A = length * width */
		 printf( "The area of a rectangle with the length and width you provided is: %f", length * width );
	}

	return 0;
}

/* area_of_square() calculates the area of a square
	user inputs the length of one side */
int area_of_square(void)
{
	char buf[MAX], *newline;
	float length = 0;
	bool is_float = false;

	while (!is_float)
	{
		puts( "You have chosen to calculate the area of a square." );
		puts( "To go back to the main menu, type \"0\" and press \"Enter\"." );
		printf( "What is the length of one of the sides of the square?\n(Type and press the \"Enter\" key) " );
		fgets(buf, sizeof(buf), stdin);
		newline = strchr(buf, '\n'); /* check for trailing newline char */

		if (newline)
			*newline = '\0';   /* replace newline with a null character */
		is_float = check_is_float(buf);
		if (!is_float)
		{
			clrscrn();
			puts("You've entered something unexpected.");
			puts("Please enter a number.");
		}
	}

	length = strtod(buf, NULL);

	if (length == 0)
		return 0;
	else
	{
		clrscrn();

		/* FORMULA AREA OF SQUARE: A = length * length */
		 printf( "The area of a square with the length provided is: %f", length * length );
	}

	return 0;
}

```
To
> ```
menu_choice = getchar() - 0x30;
```This is bad. Once again, you assume that the input will be a digit, there is no reason to assume this.
I added the following:
```

		menu_choice = getchar();
		clrstdin();

		if (isdigit(menu_choice) && menu_choice != EOF)
			menu_choice -= 0x30;
                else
                        continue;

```

---

### Post by Arndt on 2011-09-01
> **kevinharper said:**
> 
```

menu_choice -= 0x30;

```


It's more clear what the intention is if you use '0' instead of 0x30.

---

### Post by dwhitney67 on 2011-09-01
Unfortunately this non-sense will not go away; it's like the putrid smell of a rotting banana peel that has been left in the garbage over a weekend.
```

is_float = check_is_float(buf);

```

P.S.  Consider this alternative (which is not bullet-proof):
```

#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <stdbool.h>

bool getSingleValueInput(const char* prompt, const char* format, void* input);

int main()
{
   const char* prompt = "You have chosen to calculate the area of a square.\n"
                        "What is the length of the side of the square? ";
   double      length = 0;

   if (getSingleValueInput(prompt, "%lf", &length) == true)
   {
      printf("\n\nThe area of a square with sides of length %lf is %lf\n", length, length * length);
   }
   else
   {
      printf("Operation aborted; goodbye!\n");
   }

   return 0;
}

   
bool getSingleValueInput(const char* prompt, const char* format, void* input)
{
   bool   inputGood = false;
   size_t formatLen = strlen(format);
   char*  extendFormat = malloc(formatLen + 2 + 1);

   sprintf(extendFormat, "%s%%79s", format);

   if (extendFormat)
   {
      while (!inputGood)
      {
         char str_input[80];
         char garbage[80];

         printf("%s", prompt);

         if (fgets(str_input, sizeof str_input, stdin))
         {
            char* newline = strchr(str_input, '\n');

            if (newline)
            {
               *newline = '\0';
            }

            if (sscanf(str_input, extendFormat, input, garbage) == 1)
            {
               inputGood = true;
            }
            else
            {
               printf("Invalid input; try again...\n\n");
            }
         }
         else
         {
            printf("\nInput aborted...\n\n");
            break;
         }
      }

      free(extendFormat);
   }

   return inputGood;
}

```
The function getSingleValueInput() can be used for different data types (at least from the minor testing I've done).

---

### Post by dwhitney67 on 2011-09-01
I was curious about the following code:
```

/* clrstdin() clears stdin stream */
void clrstdin(void)
{
	int ch = 0;

	while ((ch = getchar()) != '\n' && ch != EOF)
		;
}

```
It does not work unless the operator enters a newline (or aborts input using ctrl-D), which is probably not what you intended.

You may need to toggle the behavior of stdin so that it is in a non-blocking mode before calling the function above.  Once stdin has been cleared, then you need to toggle stdin back to blocking mode.

```

// The following code is Linux specific (it may work under Unix, but definitely not under M$ Windows)
//
#include <termios.h>
#include <unistd.h>
#include <string.h>

// When 'enable' is 1, set non-blocking mode on the given 'fileno'.
// When 'enable' is 0, set blocking mode on the given 'fileno'.
int setNonBlocking(int enable, int fileno)
{
   static struct termios old;

   if (enable)
   {
      struct termios tmp;

      if (tcgetattr(fileno, &old))
      {
         return -1;
      }

      memcpy(&tmp, &old, sizeof(old));

      tmp.c_lflag &= ~ICANON & ~ECHO;

      if (tcsetattr(fileno, TCSANOW, (const struct termios*) &tmp))
      {
         return -1;
      }
  }
  else
  {
     tcsetattr(fileno, TCSANOW, (const struct termios*) &old);
  }

  return 0;
}

```

---

### Post by Arndt on 2011-09-01
> **kevinharper said:**
> 
Also... is there a way to dinamically format trailing zero's in output? Say, user enters 8 and 1.1 for a rectangle. Is there a way to ONLY display 8.8? But if user enters 1 and 8.888 have it print 8.888.

Look at the formatting directive %g for printf.

---

### Post by kevinharper on 2011-09-02
> this non-sense will not go away; it's like the putrid smell of a rotting banana peel that has been left in the garbage over a weekend. This feels like the time I cracked a rib grappling in an MMA class - something would make me laugh and it'd hurt so much that I'd have tears running down my cheeks but then I'd laugh harder because it was funny I was crying and because it hurt to laugh, and the cycle was never-ending.

But Captain America's shield is nothing compared to my armor so all comments openly (and equally) accepted. :)

@dwhitney67 I know that the check_is_float() function should not be there. I was trying to fix this program in pieces and was focused more on the getchar() part within are_of_circle().

Something that isn't obvious to me, and that no one has explained, is why it is incorrect to use such a function. I know it's unnecessary if I use sscanf() to parse the input. But what's the drawback of having such a function? Am I giving up performance? Is there a security issue? Can it crash the program? I've read that it's common for beginners to create functions to do something that a library function could do already. Is this an example of that (or is the code simply not even close to being functional)? I ask because it works the way it is (not saying I'm not willing to improve it). I would just like to know why it isn't kosher for me to do that.

> You may need to toggle the behavior of stdin so that it is in a non-blocking mode before calling the function above. Once stdin has been cleared, then you need to toggle stdin back to blocking mode.
what do you mean by "non-blocking" and "blocking" mode?

> It's more clear what the intention is if you use '0' instead of 0x30.Thanks Arndt. Will use that in the future.

PS: Sorry for this delayed response... had very little time to get online in the past couple of days.

---

### Post by Bachstelze on 2011-09-02
> **kevinharper said:**
> 
Something that isn't obvious to me, and that no one has explained, is why it is incorrect to use such a function. I know it's unnecessary if I use sscanf() to parse the input. But what's the drawback of having such a function?

It is bad to have unnecessary things because the more code you write, the more bugs there will be in it. Write less code = less bugs. It's a rule of good programming, not specific to this case.

---

### Post by Arndt on 2011-09-02
> **kevinharper said:**
> 
This brings up a doubt I've had every time I declare a MAX constant. gedit colors it pink as if it was a reserved keyword/constant or something. Should I not do:
```

#define MAX 255
[/CODE}
Should I choose a different name for that constant? I usually use it when declaring arrays
[CODE]
char array[MAX];

```

I looked up the places among the include files where a macro MAX is defined:

```
$ find /usr/include/ | xargs grep '#define[ \t]*[^A-Z_]MAX[^A-Z_]'
/usr/include/glib-2.0/glib/gmacros.h:#define MAX(a, b)  (((a) > (b)) ? (a) : (b))
/usr/include/sys/param.h:#define	MAX(a,b) (((a)>(b))?(a):(b))
/usr/include/jpegint.h:#define MAX(a,b)	((a) > (b) ? (a) : (b))
/usr/include/glib-1.2/glib.h:#define MAX(a, b)  (((a) > (b)) ? (a) : (b))
/usr/include/X11/Xregion.h:#define MAX(a,b) (((a) > (b)) ? (a) : (b))
/usr/include/directfb/direct/util.h:#define MAX(a,b) ((a) > (b) ? (a) : (b))

```

So it's defined here and there - interestingly always to the same thing.

If your code happens to include one of those files, directly or indirectly, you will get a clash with your different definition for MAX, and you will have to change it, but until that happens, I think it's fine to use it. I might change it anyway, to stop the editor from having irritating opinions on my code.

If you keep to strict C99, as Bachstelze recommends, and which works with your current projects, you won't run any risk of polluting your namespace with symbols from these files.

I don't use gedit. What happens if you define your MAX like above? Does it still colour it red?

---

### Post by Arndt on 2011-09-02
> **kevinharper said:**
> 
I know that the check_is_float() function should not be there. I was trying to fix this program in pieces and was focused more on the getchar() part within are_of_circle().

Something that isn't obvious to me, and that no one has explained, is why it is incorrect to use such a function. I know it's unnecessary if I use sscanf() to parse the input. But what's the drawback of having such a function? Am I giving up performance? Is there a security issue? Can it crash the program? I've read that it's common for beginners to create functions to do something that a library function could do already. Is this an example of that (or is the code simply not even close to being functional)? I ask because it works the way it is (not saying I'm not willing to improve it). I would just like to know why it isn't kosher for me to do that.


Your check_is_float does not do the same thing as sscanf and strtod - it does not allow exponents in the input. If you have a very good reason to disallow the exponent syntax, then you need a checking function of your own, but if it is meant to do the same thing as the library functions, then there is no point to it, except as an exercise, but that is better done in a special-purpose program.

---

### Post by kevinharper on 2011-09-02
> What happens if you define your MAX like above? Does it still colour it red?
Nope... I did:
```

#include <stdio.h>
#include <util.h>

#define MAX

```
and it kept it the same color as #include... :D

Thanks for that tip. I'll stop using it to define poss max vals of an array.

> It is bad to have unnecessary things because the more code you write, the more bugs there will be in it. Write less code = less bugs. It's a rule of good programming, not specific to this case.Makes sense. Thanks for the info and all of your (and everyone elses' on this forum) help.

I definitely want to keep my code as concise as possible.

I'll resubmit the a working copy of the script without that function and w/ the use of sscanf() on Monday or Tuesday.

---

