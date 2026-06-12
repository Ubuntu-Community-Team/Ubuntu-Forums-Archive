---
title: "c programming not to sure i did it right tho"
date: 2012-02-17
forum: Programming Talk
---

### Post by bathacid on 2012-02-17
I am trying to create a program that will help me make random numbers between 1-255 in the first if statement and one i finish i will have are a part in the else if statement that will randomly create ip address's and cider subnetmask to practice subnetting i only have the first if statement done so far just want to make sure i did it right. ooo btw im really new to programming so be easy on me lol a better copy of this is at [http://pastebin.com/dmbt5yBv](http://pastebin.com/dmbt5yBv)  


#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main()
{
	
	int scanfunc; //This int is ment to choose the binary or subnetting asked in first question
	int x; //This int is here to continue looping the binary part as long as this value is set to 1 by the user
	printf( "What kind of Subnetting do you wish to do?\n1.)binary conversions\n2.)subnetting\n" );
	scanf( "%d", &scanfunc );
	if ( scanfunc ==1 ) {
		do {
			srand(time(NULL));
			int rc;
			rc = (rand() % (255 + 1) + 1);
			printf( "Your number is: %d", rc );
			printf( "\nto create a new number press 1 and enter. To exit press 2 then enter\n" );
			scanf( "%d", &x );
		} while ( x == 1 );
	}
	else if ( scanfunc == 2 ) {
		printf( "function not created yet 2" );
	}
	else {
		printf( "You did not type a 1 or a 2" );
	}
	getchar();
	return 0;
}

---

### Post by Bachstelze on 2012-02-17
Firstly, please wrap CODE tags around code, so that formatting (in particular, indentation) is preserved.

Second, your code compiles without warnings even with -pedantic -Wall -Wextra. Not a lot of new programmers can achieve that. If you are really new, you were taught very well. :)

Third, the use of scanf() is generally discouraged in production code, for reasons explained [here](http://c-faq.com/stdio/scanfprobs.html). For example, try typing [font=monospace]1[/font], then [font=monospace]1[/font], then [font=monospace]a[/font]...

Fourth, you seem to have a problem with line 17. First you take its remainder modulo 256, that will produce an integer in the range 0-255. Then you add 1, that will produce an integer in the range 1-256. That's probably not what you want...

---

### Post by bathacid on 2012-02-17
```
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main()
{
	
	int scanfunc; //This int is ment to choose the binary or subnetting asked in first question
	int x; //This int is here to continue looping the binary part as long as this value is set to 1 by the user
	printf( "What kind of Subnetting do you wish to do?\n1.)binary conversions\n2.)subnetting\n" );
	scanf( "%d", &scanfunc );
	if ( scanfunc ==1 ) {
		do {
			srand(time(NULL));
			int rc;
			rc = (rand() % 255) + 1);
			printf( "Your number is: %d", rc );
			printf( "\nto create a new number press 1 and enter. To exit press 2 then enter\n" );
			scanf( "%d", &x );
		} while ( x == 1 );
	}
	else if ( scanfunc == 2 ) {
		printf( "function not created yet 2" );
	}
	else {
		printf( "You did not type a 1 or a 2" );
	}
	getchar();
	return 0;
}
```
sorry i didn't know about the code wrap feature. To be honest this is my very fist program in c i just kinda used google to find "cheat's sheets" on the syntax. I do want a range of only 1-255 because that is the most that a octet can hold in a ip address. i hope this makes it more clear? thank you for the link about the scanf problems ill try to get them implemented.

---

### Post by Bachstelze on 2012-02-17
Then you should do

```
rc = (rand() % 255)+1
```

remainder modulo 255 will generate an integer in the range 0-254, and adding 1 you get 1-255.

---

