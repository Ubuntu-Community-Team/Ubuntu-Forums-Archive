---
title: "Project Euler problem 164"
date: 2008-07-13
forum: Programming Talk
---

### Post by spadewarrior on 2008-07-13
Anyone had a go at this one?

[http://projecteuler.net/index.php?section=problems&id=164](http://projecteuler.net/index.php?section=problems&id=164)

I started a python program for it but it's so slow I decided to rewrite it in C. Unfortunately I can't work out how to use 20-digit numbers in C - nothing seems to be big enough to hold them.

Any ideas on how to get my amateurish code running (a lot) faster? 

Python:

[PHP]def calc(string):
	count = 0
	temp = 0
	j = 0
	while j <= len(string) - 3 and temp == 0:
		h = j + 1
		k = j + 2
		if (int(string[j]) + int(string[h]) + int(string[k])) > 9:
			temp +=1
		j += 1
	if temp == 0:
		count += 1
		print string, "OK!"
	return count
	
def makeList(n, MAX):
	count = 0 
	while n <= MAX:
		if calc(str(n)) == 1:
			count += 1
		n += 1
	
	return count

n = 10000000000000000000
MAX = 99999999999999999999


answer = makeList(n, MAX)
print "The answer is", answer


[/PHP]

C:

[PHP]#include <stdio.h>
#include <stdlib.h>
#include <string.h>


long calc(char * p);
unsigned long long int makeList(long n, long MAX);

int main(void)
{
	unsigned long long int n  = 		1000000000ULL;
	unsigned long long int MAX =	 	9999999999ULL;
	long answer = makeList(n, MAX);
	printf ("\n%ld\n", answer);

	return 0;
}


unsigned long long int makeList(long n, long MAX)
{
	unsigned long long int count = 0ULL;
	char numStr[100];
	char *p = numStr;
	while (n < MAX)
	{
		sprintf( numStr, "%ld", n);
		p = numStr;
		if( calc( p ) == 1)
		{
			count ++;
		}
		n++;
	}
	return count;
}

long calc(char *p)
{
	unsigned long long int count = 0ULL;
	int temp = 0;
	int j = 0;
	int len = strlen(p);
	int a, b, c;

	while ( j <= (len - 3) && temp == 0)
	{
		sscanf(&p[j], "%1d%1d%1d", &a, &b, &c);
		
		if ( a + b+ c > 9 )
		{
			temp++;
		}
		j++; // move through the string
	}
	if ( temp == 0 )
	{
		count++;
		printf( "\n%s OK!", p);
	}
	
	return count;
}
[/PHP]

If I try to use 20-digit numbers in the C program I get these warnings:

```
euler164.c:11: warning: this decimal constant is unsigned only in ISO C90
euler164.c:11: warning: integer constant is too large for ‘long’ type
euler164.c:12:33: warning: integer constant is too large for its type
euler164.c:12: warning: integer constant is too large for ‘long’ type
```

Thanks for reading.

---

### Post by thornmastr on 2008-07-13
I've done a few (very few) of the Project Euler brain crunchers. If I remember correctly, they give you a bit of an edge on time if you use Python. It's not much of an edge, but it is a good running start that you should consider taking advantage of before going to C, or C++, or Lisp. One of the problems that nailed me on Euler using C++ is that you are stuck fighting numeric data types. It took me a while to realize if I was going to leave Python for C or C++, I was really going to have to find a very good Big Integer library to incorporate into the program. You might want to look at what is available since you are turning your back on what Python does for you automatically.

Just my 2 cents worth.

Robert

---

### Post by Lster on 2008-07-13
You are right, even a 64bit unsigned int is unable to store values as high as that. I remember thinking this one looked hard myself a while ago, but it isn't really at all once you work out what you need to do. Bare in mind that even if you could test 10^10 numbers per second (which is faster than my laptop!), it would take more than 300 years!

I'd certainly be happy to give you a hint or two via PM if you would like. I would post publicly but it seems many people at Project Euler find that objectionable as it can aid people who simply "google answers".

Good luck,
Lster

---

