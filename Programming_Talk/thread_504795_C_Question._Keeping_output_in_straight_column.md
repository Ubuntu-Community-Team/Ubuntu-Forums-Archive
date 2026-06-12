---
title: "C Question. Keeping output in straight column"
date: 2007-07-19
forum: Programming Talk
---

### Post by TreeFinger on 2007-07-19
Hello, all. 

I have a question about formatting output in C. I know in C++ you can align text and stuff. My C book hasn't covered this topic yet if it is even part of the language.

Anyways I wrote a program this afternoon that prints out the multiplication table from 0-12. It doesn't look good though! I am wondering how I could get my columns to align with each other?

Here is my code followed by the output.

```

/* Programming exercises. Chapter 8-4
*  Created by Samuel Chodur Jr.
*  Program: Print out Multiplication Table
*/

#include <stdio.h>
int horiz_count;
int vert_count;
int num_count;
int main () {

printf("I will print he 0-12 mulitplication table for you.\n");

horiz_count = 0;
vert_count = 0;
num_count = 0;
while ( horiz_count < 13 ) { /* Prints top row. No multiplication involved */
	if ( horiz_count == 0 )
		printf("X  ");
	printf("  %d  ", num_count);
	++horiz_count;
	if ( num_count == 12 ) {
		printf("\n");
		horiz_count = 0;
		break;
	}
	++num_count;
}
while ( horiz_count < 13 ) {
	if ( horiz_count == 0 )
		printf("%d  ", vert_count);
	printf("  %d  ", vert_count * horiz_count);
	++horiz_count;
	if ( horiz_count > 12 ) {
		printf("\n");
		horiz_count = 0;
		++vert_count;
		if ( vert_count > 12 )
			break;
	}
}
return 0;
}

```

```

./8-4
I will print he 0-12 mulitplication table for you.
X    0    1    2    3    4    5    6    7    8    9    10    11    12  
0    0    0    0    0    0    0    0    0    0    0    0    0    0  
1    0    1    2    3    4    5    6    7    8    9    10    11    12  
2    0    2    4    6    8    10    12    14    16    18    20    22    24  
3    0    3    6    9    12    15    18    21    24    27    30    33    36  
4    0    4    8    12    16    20    24    28    32    36    40    44    48  
5    0    5    10    15    20    25    30    35    40    45    50    55    60  
6    0    6    12    18    24    30    36    42    48    54    60    66    72  
7    0    7    14    21    28    35    42    49    56    63    70    77    84  
8    0    8    16    24    32    40    48    56    64    72    80    88    96  
9    0    9    18    27    36    45    54    63    72    81    90    99    108  
10    0    10    20    30    40    50    60    70    80    90    100    110    120  
11    0    11    22    33    44    55    66    77    88    99    110    121    132  
12    0    12    24    36    48    60    72    84    96    108    120    132    144  

```

---

### Post by LaRoza on 2007-07-19
There is a way, but I forget and all of my resources are at home. There are other formating options, maybe your book has them? Sorry I couldn't be more helpful.

---

### Post by Wybiral on 2007-07-19
[http://gd.tuwien.ac.at/languages/c/programming-bbrown/c_108.htm](http://gd.tuwien.ac.at/languages/c/programming-bbrown/c_108.htm)

---

### Post by rodo-&gt;dave on 2007-07-19
Well, one way is to copy the int into a char * using sprintf and then printf with the format you want.
I hope you don't mind that I modified your prog a little:

```

/* Programming exercises. Chapter 8-4
*  Created by Samuel Chodur Jr.
*  Program: Print out Multiplication Table
*/

#include <stdio.h>
int horiz_count;
int vert_count;
int num_count;
int main()
{
	char s[100];

    printf("I will print he 0-12 mulitplication table for you.\n");

    horiz_count = 0;
    vert_count = 0;
    num_count = 0;
    while (horiz_count < 13) {	/* Prints top row. No multiplication involved */
	if (horiz_count == 0)
	    printf("X  ");

	sprintf(s, "%d", num_count);

	printf("%3s ", s);

	++horiz_count;
	if (num_count == 12) {
	    printf("\n");
	    horiz_count = 0;
	    break;
	}
	++num_count;
    }
    while (horiz_count < 13) {
	if (horiz_count == 0) {
		sprintf(s, "%d", vert_count);
	    printf("%3s", s);
	}

	sprintf(s, "%d", vert_count * horiz_count);
	printf("%3s ", s);

	++horiz_count;
	if (horiz_count > 12) {
	    printf("\n");
	    horiz_count = 0;
	    ++vert_count;
	    if (vert_count > 12)
		break;
	}
    }
    return 0;
}


```

output:
```

$ a
I will print he 0-12 mulitplication table for you.
X    0   1   2   3   4   5   6   7   8   9  10  11  12
  0  0   0   0   0   0   0   0   0   0   0   0   0   0
  1  0   1   2   3   4   5   6   7   8   9  10  11  12
  2  0   2   4   6   8  10  12  14  16  18  20  22  24
  3  0   3   6   9  12  15  18  21  24  27  30  33  36
  4  0   4   8  12  16  20  24  28  32  36  40  44  48
  5  0   5  10  15  20  25  30  35  40  45  50  55  60
  6  0   6  12  18  24  30  36  42  48  54  60  66  72
  7  0   7  14  21  28  35  42  49  56  63  70  77  84
  8  0   8  16  24  32  40  48  56  64  72  80  88  96
  9  0   9  18  27  36  45  54  63  72  81  90  99 108
 10  0  10  20  30  40  50  60  70  80  90 100 110 120
 11  0  11  22  33  44  55  66  77  88  99 110 121 132
 12  0  12  24  36  48  60  72  84  96 108 120 132 144

```

I am using a cygwin shell at work on winXP.

---

### Post by Wybiral on 2007-07-19
You can use printf without a buffer...

```

/* Programming exercises. Chapter 8-4
*  Created by Samuel Chodur Jr.
*  Program: Print out Multiplication Table
*/

#include <stdio.h>
int horiz_count;
int vert_count;
int num_count;
int main () {

printf("I will print he 0-12 mulitplication table for you.\n");

horiz_count = 0;
vert_count = 0;
num_count = 0;
while ( horiz_count < 13 ) { /* Prints top row. No multiplication involved */
	if ( horiz_count == 0 )
		printf(" X");
	printf(" %3d", num_count);
	++horiz_count;
	if ( num_count == 12 ) {
		printf("\n");
		horiz_count = 0;
		break;
	}
	++num_count;
}
while ( horiz_count < 13 ) {
	if ( horiz_count == 0 )
		printf("%2d", vert_count);
	printf(" %3d", vert_count * horiz_count);
	++horiz_count;
	if ( horiz_count > 12 ) {
		printf("\n");
		horiz_count = 0;
		++vert_count;
		if ( vert_count > 12 )
			break;
	}
}
return 0;
}

```

---

### Post by TreeFinger on 2007-07-19
Wybiral - Your method worked, it was the only one I tested but I also have no idea what it did.

I removed the extra spaces that I had before. I guess it comes down to the parts like

```

printf(" %3d", num_count);

```

What does that 3 actually do in front of the d?
Is it just adding spaces?

ahh any tutorials that explain this? What is it actually called?

---

### Post by rodo-&gt;dave on 2007-07-19
> **Wybiral said:**
> You can use printf without a buffer...

...
I seem to recall some compat problems across unices many years ago when formatting the int in printf... but either way, it works on my cygwin too! good job.

---

### Post by rodo-&gt;dave on 2007-07-19
> **TreeFinger said:**
> Wybiral - Your method worked, it was the only one I tested but I also have no idea what it did.

I removed the extra spaces that I had before. I guess it comes down to the parts like

```

printf(" %3d", num_count);

```

What does that 3 actually do in front of the d?
Is it just adding spaces?

ahh any tutorials that explain this? What is it actually called?
TreeFinger, forgive me if you already know this, but are you familiar with the "man" command. man is the "online manual" pages... you should be able to "man printf" and see the format options...
later.
dave O

---

### Post by TreeFinger on 2007-07-19
> **rodo->dave said:**
> TreeFinger, forgive me if you already know this, but are you familiar with the "man" command. man is the "online manual" pages... you should be able to "man printf" and see the format options...
later.
dave O

Thanks, I didn't know man worked for C commands. I thought it was just things I would use in the terminal like 'man ls'.

---

### Post by rodo-&gt;dave on 2007-07-19
Let me boot up my 7.04 in a vm here at work and see if I can find the package you need to install from synaptic...


maybe manpages-dev????
sorry, can't find the exact package

---

### Post by TreeFinger on 2007-07-19
Don't worry about it **rodo->dave**.

I checked out the C reference guide and I am gaining some understanding of formatting options.

Here is the link, [http://www.acm.uiuc.edu/webmonkeys/book/c_guide/2.12.html#printf](http://www.acm.uiuc.edu/webmonkeys/book/c_guide/2.12.html#printf)

---

