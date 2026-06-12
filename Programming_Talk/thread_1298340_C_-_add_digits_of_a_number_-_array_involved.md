---
title: "C - add digits of a number - array involved"
date: 2009-10-22
forum: Programming Talk
---

### Post by ApEkV2 on 2009-10-22
Ok, so I am trying to solve a hard easy problem. How do you take a number "1234" and add the digits "1+2+3+4"?
I would like to take a number from the first row of the array, add that number's digits, and then input the result to the next row of the array.
I started to try solving it, but then a brick breakfast happened. 

[color=red]EDIT - This problem is solved, the code has been updated[/color]

[php]#include <ctype.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#define Z_NL 4294967295

int SumCif(int n)
{
	int s = 0;

	while (n != 0) 
        {
		s += n%10;
		n /= 10;
        }
	return s;
}

int main(void)
{

unsigned int z_in, z_array[6][100] = {0};
int count, x = 0, y = 0;
srand((unsigned)time(NULL));

for (count = 0; count <= 100; count++)
{
	z_in = rand()%Z_NL;

	if (y <= 100) { 
		z_array[0][y] = z_in; 
		++y; }
}

for (y = 0; y <= 99; y++) {
	z_array[1][y] = SumCif(z_array[0][y]);
		}

for (y = 0; y <= 99; y++) {
	printf(" %11u%11u%11u%11u%11u%11u\n", z_array[0][y], z_array[1][y], z_array[2][y], z_array[3][y], z_array[4][y], z_array[5][y]);
		}

	return 0;
}[/php]

---

### Post by Wistful on 2009-10-22
>  How do you take a number "1234" and add the digits "1+2+3+4"? 

[PHP]/* 
 * ===  FUNCTION  =======================================================
 *         Name:  SumCif
 *  Description:  Sum of a number's digits
 *                e.g. n = 1234 ; sum = 1+2+3+4 = 10 ;
 * ======================================================================
 * ===
 */
int SumCif(int n)
{
        int s = 0;
        
        while(n!=0)
        {
                s+=n%10;
                n/=10;
        }
        
        return s;
}
[/PHP]

---

### Post by Can+~ on 2009-10-22
> **Wistful said:**
> [PHP]/* 
 * ===  FUNCTION  =======================================================
 *         Name:  SumCif
 *  Description:  Sum of a number's digits
 *                e.g. n = 1234 ; sum = 1+2+3+4 = 10 ;
 * ======================================================================
 * ===
 */
int SumCif(int n)
{
        int s = 0;
        
        while(n!=0)
        {
                s+=n%10;
                n/=10;
        }
        
        return s;
}
[/PHP]

Funny that you translated my exact thought into code.

---

### Post by ApEkV2 on 2009-10-22
Where is my Easy button? *slam*.....I feel kinda tarded now. Thanks though for the speedy-ness of your reply.
[php]#include <stdlib.h>
#include <string.h>
#include <ctype.h>
#include <stdio.h>
#include <unistd.h>
#include <limits.h>
#define Z_NL 4294967295

int SumCif(int n)
{
	int s = 0;
	while (n != 0) 
        {
		s += n%10;
		n /= 10;
        }
	return s;
}  

int main(void)
{

unsigned int z_in, z_array[4][100] = {0};
int x, y = 0, z = 1, Cc, z_sum = 0, z_dif = 0;
srand((unsigned)time(NULL));

for (Cc = 0; Cc <= 100; Cc++) {
	z_in = rand()%Z_NL;
	if (z && y <= 100) { z_array[0][y] = z_in; ++y; }
	if (z && y == 100) { x = 0; y = 0; z = 0; }
	}

for (y = 0; y <= 99; y++) {
	z_array[1][y] = SumCif(z_array[0][y]);
		}

for (y = 0; y <= 99; y++) {
	printf("|%d| %u\t\t\t%u\t\t%u\t\t%u\n", y, z_array[0][y], z_array[1][y], z_array[2][y], z_array[3][y]);
		}

	return 0;
}[/php]

---

### Post by Can+~ on 2009-10-22
> **ApEkV2 said:**
> Where is my Easy button? *slam*.....I feel kinda tarded now. Thanks though for the speedy-ness of your reply.
[php]#include <stdlib.h>
#include <string.h>
#include <ctype.h>
#include <stdio.h>
#include <unistd.h>
#include <limits.h>
#define Z_NL 4294967295

int SumCif(int n)
{
	int s = 0;
	while (n != 0) 
        {
		s += n%10;
		n /= 10;
        }
	return s;
}  

int main(void)
{

unsigned int z_in, z_array[4][100] = {0};
int x, y = 0, z = 1, Cc, z_sum = 0, z_dif = 0;
srand((unsigned)time(NULL));

for (Cc = 0; Cc <= 100; Cc++) {
	z_in = rand()%Z_NL;
	if (z && y <= 100) { z_array[0][y] = z_in; ++y; }
	if (z && y == 100) { x = 0; y = 0; z = 0; }
	}

for (y = 0; y <= 99; y++) {
	z_array[1][y] = SumCif(z_array[0][y]);
		}

for (y = 0; y <= 99; y++) {
	printf("|%d| %u\t\t\t%u\t\t%u\t\t%u\n", y, z_array[0][y], z_array[1][y], z_array[2][y], z_array[3][y]);
		}

	return 0;
}[/php]

On the other hand, what's going on with your indentation? And variable naming? It's pretty messy.

---

### Post by ApEkV2 on 2009-10-22
I wasn't aware I was being judged lol.....is this better?
[php]#include <ctype.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#define Z_NL 4294967295

int SumCif(int n)
{
	int s = 0;
	while (n != 0) 
        {
		s += n%10;
		n /= 10;
        }
	return s;
}

int main(void)
{

unsigned int z_in, z_array[4][100] = {0};
int count, x = 0, y = 0;
srand((unsigned)time(NULL));

for (count = 0; count <= 100; count++)
{
	z_in = rand()%Z_NL;

	if (y <= 100) { 
		z_array[0][y] = z_in; 
		++y; }
}

for (y = 0; y <= 99; y++) {
	z_array[1][y] = SumCif(z_array[0][y]);
		}

for (y = 0; y <= 99; y++) {
	printf(" %u\t\t\t%u\t\t%u\t\t%u\n", z_array[0][y], z_array[1][y], z_array[2][y], z_array[3][y]);
		}

	return 0;
}[/php]

---

### Post by Can+~ on 2009-10-22
That's a weird mix between Allman's (first function), K&R's (the "for"s at the end) and Whitesmith's.

Also, it's a good idea to leave an empty line between declarations and working code.

Here's the code in all Allman's:

[PHP]#include <ctype.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#define Z_NL 4294967295

int SumCif(int n)
{ 
	int s = 0;
	
	while (n != 0)
	{
		s += n%10;
		n /= 10;
	}
	
	return s; 
} 

int main(void) 
{
	unsigned int z_in, z_array[4][100] = {0};
	int count, x = 0, y = 0;
	srand((unsigned)time(NULL));
	
	for (count = 0; count <= 100; count++)
	{ 
		z_in = rand()%Z_NL;

		if (y <= 100)
		{  
			z_array[0][y] = z_in;
			++y;
		}
	}

	for (y = 0; y <= 99; y++)
	{
		z_array[1][y] = SumCif(z_array[0][y]);
	}

	for (y = 0; y <= 99; y++)
	{
		printf(" %u\t\t\t%u\t\t%u\t\t%u\n", z_array[0][y], z_array[1][y], z_array[2][y], z_array[3][y]);
	}

	return 0;
}
[/PHP]

Legibility is important, code is more read than written.

---

### Post by ApEkV2 on 2009-10-22
I thought it was encouraged to stick to one style, but was not mandatory.

---

