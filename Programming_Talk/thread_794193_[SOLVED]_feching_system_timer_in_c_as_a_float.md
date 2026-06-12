---
title: "[SOLVED] feching system timer in c as a float"
date: 2008-05-14
forum: Programming Talk
---

### Post by natirips on 2008-05-14
How do I fetch the system timer in c as a float? I only know how to catch the unix time in seconds (time(NULL)), but I need something to use with sync-ing in miliseconds, like the system timer; but anythig else will do (like number of miliseconds from the program start time or a function that waits for a given number of miliseconds).

---

### Post by dwhitney67 on 2008-05-14
Try using gettimeofday().  For info, refer to the man-page.

Simple example:
[PHP]
#include <sys/time.h>
#include <time.h>
#include <stdio.h>

int main()
{
  struct timeval tv;

  gettimeofday( &tv, NULL );

  double theTime = tv.tv_sec + (0.000001f * tv.tv_usec);

  printf( "time as double = %f\n", theTime );
  printf( "sys time sec   = %d\n", (unsigned int)tv.tv_sec );
  printf( "sys time usec  = %d\n", (unsigned int)tv.tv_usec );
  printf( "sys time       = %d\n", (unsigned int)time(0) );

  return 0;
}
[/PHP]

---

### Post by natirips on 2008-05-14
> **dwhitney67 said:**
> Try using gettimeofday().  For info, refer to the man-page.

Simple example:
[PHP]
#include <sys/time.h>
#include <time.h>
#include <stdio.h>

int main()
{
  struct timeval tv;

  gettimeofday( &tv, NULL );

  double theTime = tv.tv_sec + (0.000001f * tv.tv_usec);

  printf( "time as double = %f\n", theTime );
  printf( "sys time sec   = %d\n", (unsigned int)tv.tv_sec );
  printf( "sys time usec  = %d\n", (unsigned int)tv.tv_usec );
  printf( "sys time       = %d\n", (unsigned int)time(0) );

  return 0;
}
[/PHP]

Thank you for the above, it works like a charm, but right now my program hangs at the marked (with comments) point:
```
#include <sys/time.h>
#include<stdio.h>
#include<stdlib.h>
#include<time.h>
int main(int argc, char *argv[]){

FILE *a=fopen(argv[1],"rb");
long double foo;
char b;
struct timeval tv;
 gettimeofday( &tv, NULL );
double v=(double)tv.tv_sec + ((foo=0.000001f) * tv.tv_usec);

if(!a)exit(1);//exit if can't open file

printf("\n%lf\n",v); //I'm checking what kind of time format I got
b=fgetc(a);

do{
	printf("%c",b);
	b=fgetc(a);
	///////////////////////////////////////////////
	while(((double)tv.tv_sec + ((foo=0.000001f) * tv.tv_usec) - v)   <   0.1);		
	/////////////////////////////////////////////
	v=(double)tv.tv_sec + ((foo=0.000001f) * tv.tv_usec);
}while(b!=EOF);

;;;;
printf("\n");
fclose(a);
return 0;}

```
If I comment out that line it works, but with it it just hangs. What did I do wrong?
Here's a simlified version of that line:

while(current_time - last_cheched_time < 0.1);

So it is supposed to wait 100ms and continue the program...

---

### Post by dwhitney67 on 2008-05-14
The gettimeofday() function returns the current snapshot of the system time.

It appears from your code that this was not understood.  You are setting the variable 'v' each time in the loop as if you are expecting it to change... it won't.

What are trying to accomplish?  Specifying your requirements might provide more insight on how to approach solving the problem rather than just seeing your solution.

---

### Post by natirips on 2008-05-14
> **dwhitney67 said:**
> The gettimeofday() function returns the current snapshot of the system time.

It appears from your code that this was not understood.  You are setting the variable 'v' each time in the loop as if you are expecting it to change... it won't.

What are trying to accomplish?  Specifying your requirements might provide more insight on how to approach solving the problem rather than just seeing your solution.

I'm not expacting the "v" to change, I put a ; after the while, so I'm expacting the current_time - v to increase over time as "v" is fixed inside the while, and the current time is increasing.

---

### Post by natirips on 2008-05-14
I got it to work:
```
do{
	printf("%c",b);
	b=fgetc(a);
	///////////////////////////////////////////////
	for(

 gettimeofday( &tv, NULL ),
v1=(double)tv.tv_sec + ((foo=0.000001f) * tv.tv_usec);

	  (( v1- v)   <   0.5)   ;

	 gettimeofday( &tv, NULL ),
v1=(double)tv.tv_sec + ((foo=0.000001f) * tv.tv_usec));
	/////////////////////////////////////////////
	v=(double)tv.tv_sec + ((foo=0.000001f) * tv.tv_usec);
}while(b!=EOF);
```
I know it looks horrible, but it works:). "v1" is a double.

---

### Post by dwhitney67 on 2008-05-14
> **natirips said:**
> I got it to work:
```
do{
	printf("%c",b);
	b=fgetc(a);
	///////////////////////////////////////////////
	for(

 gettimeofday( &tv, NULL ),
v1=(double)tv.tv_sec + ((foo=0.000001f) * tv.tv_usec);

	  (( v1- v)   <   0.5)   ;

	 gettimeofday( &tv, NULL ),
v1=(double)tv.tv_sec + ((foo=0.000001f) * tv.tv_usec));
	/////////////////////////////////////////////
	v=(double)tv.tv_sec + ((foo=0.000001f) * tv.tv_usec);
}while(b!=EOF);
```
I know it looks horrible, but it works:). "v1" is a double.

Sure does!  :)

It seems to me that you want to read a file, character by character, every half-second (0.5 secs).  Is that correct?  If so, consider using usleep().

Here's an example:
[PHP]
#include <stdio.h>
#include <unistd.h>

int main()
{
  FILE *fp = fopen( "./slowOutput.c", "r" );
  char c;

  while ( (c = fgetc(fp)) != EOF )
  {
    printf( "%c", c );
    fflush(stdout);
    usleep( 500000 );
  }

  return 0;
}
[/PHP]

P.S.  Why do you set 'foo' when using the 0.000001f value??  Ugly!

---

### Post by natirips on 2008-05-14
> **dwhitney67 said:**
> Sure does!  :)

It seems to me that you want to read a file, character by character, every half-second (0.5 secs).  Is that correct?  If so, consider using usleep().

Here's an example:
[PHP]#include <unistd.h>
#include <stdio.h>

int main()
{
  for ( int i = 0; i < 10; ++i )
  {
    printf( "I'm awake!  Now going back to sleep...\n" );
    usleep( 500000 );  // sleep 500000 usecs = 0.5 seconds
  }

  return 0;
}[/PHP]

P.S.  Why do you set 'foo' when using the 0.000001f value??  Ugly!

I by mistake thought that 0.00001f would round to zero during calculation so I put it as a long double... I know there are better ways but....

This usleep() function works great (much simpler than all the mess I originally used:)). 

But now I got to a new problem, I noticed it only writes the characters out when the newline appears, so if I write each new char every 0.5s, and there are 10 chars in a line, the whole line will appear suddenly after 5seconds.

---

### Post by natirips on 2008-05-14
This is my program now:[PHP]//#include <sys/time.h>
#include<stdio.h>
#include<stdlib.h>
#include<time.h>
#include <unistd.h>

int main(int argc, char *argv[]){
FILE *a=fopen(argv[1],"rb");	if(!a)exit(1);//exit if can't open file
char b;
b=fgetc(a);

do{
	fprintf(stdout,"%c",b);
	b=fgetc(a);
	usleep(200000);
}while(b!=EOF);
;;;;
printf("\n");
fclose(a);
return 0;}
[/PHP]It almost does what I want it to...

---

### Post by natirips on 2008-05-14
Made it! Now it works completely, I added fflush after printf.[PHP]//#include <sys/time.h>
#include<stdio.h>
#include<stdlib.h>
#include<time.h>
#include <unistd.h>

int main(int argc, char *argv[]){
FILE *a=fopen(argv[1],"rb");	if(!a)exit(1);//exit if can't open file
char b;
b=fgetc(a);

do{
	fprintf(stdout,"%c",b);fflush(stdout);
	b=fgetc(a);
	usleep(200000);
}while(b!=EOF);
;;;;
printf("\n");
fclose(a);
return 0;}
[/PHP]
If read a file given as the argument to the screen, character by character and acctually writes them to the screen that way.

---

