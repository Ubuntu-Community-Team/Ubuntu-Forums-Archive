---
title: "Old Challenges 3: Palindrome Fun"
date: 2008-05-11
forum: Programming Talk
---

### Post by JupiterV2 on 2008-05-11
Task 1: Check if given input is a palindrome.

Task 2: If input is a number, and is not a palindrome, convert it to the lowest possible palindrome higher than the number given. (ie: 812 ->818 or 1234->1331)

I decided to solve the task using standard C. I know I posted using the old thread but a) it is now closed; and, b) my algorithm for creating the palindrome from a number was...well..absolutely terrible. It didn't work. The new one does, however.

As always, constructive criticism welcome. I really enjoy your input.


[PHP]#include <stdio.h>
#include <string.h>

int is_palindrome(const char* str)
{
	// test whether or not the given string is a palindrome 
	int len = strlen(str);
	
	int x, y;
	char cx, cy;
	
	for(x = 0, y = (len - 1); x < y;)
	{
		cx = str[x], cy = str[y];
		
		// switch from upper case to lower case
		if( cx > 64 && cx < 90 ) cx += 32;
		if( cy > 64 && cy < 90 ) cy += 32;
		
		// non-lowercase alpha-numerics are ignored
		if( (cx < 97 || cx > 122) && (cx < 48 || cx > 57) )
		{
			x++;
			continue;
		}
		
		if( (cy < 97 || cy > 122) && (cy < 48 || cy > 57) )
		{
			y--;
			continue;
		}
		
		if( cx != cy ) return 0;
		
		x++;
		y--;
	}
		
	return 1;
}

int make_palindrome(char* str)
{
	int len = strlen(str);
	int x = 0, y = len - 1;
	
	while( !is_palindrome(str) && x <= y)
	{		
		if( str[x] < str[y] )
		{
			str[y] = str[x];
			
			while( y >= 0 )
			{
				if( ++str[--y] > 57 ) str[y] = 48;
				else
				{
					// reset and start again
					x = 0;
					y = len - 1;
					break;
				}
			}
			continue;
		}
		else str[y] = str[x];
		
		x++, y--;
	}
}

int is_number(const char* str)
{
	// tests whether the given string represents a number
	int len = strlen(str), x = 0;
	
	while( x < len )
	{
		if( str[x] < 48 || str[x] > 57 ) return 0;
		x++;
	}
	
	return 1;
}

int main(int argc, char** argv)
{
	if( argc != 2 )
	{
		printf("Usage: %s <value>\n", argv[0]);
		return 1;
	}
	
	if( is_number(argv[1]) ) 
	{
		make_palindrome(argv[1]);
		printf("The next lowest palindrom higher than the number entered "
			"is: %s\n", argv[1]);
	}
	else printf("Is %s a palindrome? %s\n", argv[1], 
			(is_palindrome(argv[1]) ? "yes" : "no"));	
}[/PHP]

---

### Post by Jessehk on 2008-05-11
Didn't we already establish that you shouldn't be creating new threads for these preexisting challenges? Reply to the old threads.

---

### Post by WW on 2008-05-11
> **Jessehk said:**
> Didn't we already establish that you shouldn't be creating new threads for these preexisting challenges? Reply to the old threads.

Did you read JupiterV2's post?  LaRoza has closed the old thread.

---

### Post by Jessehk on 2008-05-11
> **WW said:**
> Did you read JupiterV2's post?

Now I'm embarrassed. Sorry. :oops:

---

