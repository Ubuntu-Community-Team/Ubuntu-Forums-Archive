---
title: "C question: Converting a string to a unsigned long int?"
date: 2007-11-11
forum: Programming Talk
---

### Post by fredscripts on 2007-11-11
Hi! I'm working in a program in C that reads a file like:

John
Smith
55585913


And then makes some stuff and writes on another file the output.

In order to read the three values, I first thought in use fscanf,but I realized that that function stopped with a white character, so there could be problems with that. I took a look at fgets , which seems fine because read line by line and returns an string. 

I need to compute something with the numerical value of the text, so I need to convert the string that fgets gives to me to a unsigned long int. 

Any standard library offers me that conversion with a function?


Thank you very much!!!

---

### Post by elctb on 2007-11-11
Take a look at:
    atoi
    atol

You must include stdlib.h

---

### Post by fredscripts on 2007-11-11
oh yes! atol it's what I was looking for! Thanks!

Another newbie question, fgets gives me a line of the textfile which includes the newline character '\n', I would like to remove it from my string. Of course I could do a little function to do that but if theres something on the standard library that makes this work would be fantastic!!

Thank you very much for your help again! I'm just starting C and I think I like it!

---

### Post by fredscripts on 2007-11-11
I did start making the little function to remove the newline character from the string that fgets gives me, and I'm having some trouble:

```
fgets(string_in , MAX_SIZE , texfile);

/* Here I'm trying to remove the 'nl' from string_in */

int i;

for ( i = 0; i < MAX_SIZE ; i++) {
      if ( string_in[i]  == 'nl' ) {
        /* don't know what to do here :( */
}
```

Isn't any function on any library like "remove"? I'm little used to the java way so I don't know how to cope with it :(

Thanks for your help!!!

---

### Post by fredscripts on 2007-11-11
I'm thinking on another way of doing this, I thought I was on the right way doing this:
```

fgets(string_in , MAX_SIZE , texfile);

/* removes the nl character */

char *nlptr = strchr(string_in,'\n');
*nlptr = '\0'


```

But the compiler says to me: on the line of "char..." : Expression sytax in function main

I don't understand exactly the problem, I must define before somewhere nlptr?

Thanks!

---

### Post by Compyx on 2007-11-11
> **fredscripts said:**
> I'm thinking on another way of doing this, I thought I was on the right way doing this:
```

fgets(string_in , MAX_SIZE , texfile);

/* removes the nl character */

char *nlptr = strchr(string_in,'\n');
*nlptr = '\0'


```

But the compiler says to me: on the line of "char..." : Expression sytax in function main

I don't understand exactly the problem, I must define before somewhere nlptr?

Thanks!

In C90 you cannot declare variables in the middle of a block, you need to declare them at the start of a block. So declare char *nlptr at the start of the function.

Also, consider using strtoul(3), ato* functions don't indicate whether an error occurred during conversion. You also don't check the return value of fgets(), fgets returns NULL on error, check for it and handle it.

Next time post the exact error message (copy & paste), don't retype, I have a feeling GCC's error messages don't contain words like 'sytax' (unless you declare an object named 'sytax').

---

### Post by slavik on 2007-11-11
I would use fgets to read in a line into a buffer and then sscanf to read stuff from buffer ...

---

### Post by Meneldir on 2007-11-17
I recommend strtoul() to convert the string to unsigned long int. If the string does not represent an unsigned long, with strtoul() you may see if that worked. strtoul() is part of stdlib.h
Then, to remove the nl:
```

/*with nlptr declared as: char *nlptr; at the beginning of the function */
if(( nlptr = strchr( string, '\n' )) != NULL )
  *nlptr = '\0';
/* it's wrapped by an IF to check if the string really had one. 
fgets() will read only MAX_SIZE chars, so, it may not read up to a nl char. */

```

---

### Post by dwhitney67 on 2007-11-18
Using strtok() presents a solution as well:

```
#include <stdio.h>
#include <string.h>


int main()
{
  FILE *fp = fopen( "data.txt", "r" );

  if ( fp != NULL )
  {
    char buf[ 80 ] = { '\0' };

    while ( fgets( buf, sizeof buf, fp ) != NULL )
    {
      char *str = strtok( buf, "\n" );
      printf( "str = %s\n", str );
    }
    fclose( fp );
  }
  return 0;
}
```

If you wish to consider using your strchr() idea, then here's the code:

```
#include <stdio.h>
#include <string.h>


int main()
{
  FILE *fp = fopen( "data.txt", "r" );

  if ( fp != NULL )
  {
    char buf[ 80 ] = { '\0' };

    while ( fgets( buf, sizeof buf, fp ) != NULL )
    {
      char *nlPtr = 0;

      if ( (nlPtr = strchr( buf, (int)'\n' )) != NULL )
      {
        *nlPtr = '\0';
      }

      printf( "buf = %s\n", buf );
    }
    fclose( fp );
  }
  return 0;
}
```

---

### Post by samjh on 2007-11-18
> **fredscripts said:**
> I need to compute something with the numerical value of the text, so I need to convert the string that fgets gives to me to a unsigned long int. 

Any standard library offers me that conversion with a function?

Use the strtoul function, as mentioned in Meneldir's post.  Here's a commented example.

```
#include <stdio.h>
#include <string.h>

int main(void)
{
	/*
	 * the_str = value to be assigned by console input
	 * newline = pointer to \n in the_str
	 * the_ulong = the unsigned long integer
	 */
	char the_str [20];
	char *newline;
	unsigned long the_ulong;

	/* Fetch user input from console */
	fgets(the_str, 20, stdin);

	/* Use strchr to find \n in the_str.
	 * strchr returns NULL if no \n was found.
	 * If strchr was successful in finding \n:
	 * 	replace the \n with \0.
	 */
	newline = strchr(the_str, '\n');
	if (newline != NULL) {
		*newline = '\0';
	}

	/* Convert the_str to unsigned long and assign to the_ulong.
	 * Parameters for strtoul:
	 * 	the_str is the source string
	 * 	ignore the second parameter, it is not used in this example
	 * 	10 means base-10, so convert the_str to base-10 unsigned long
	 */
	the_ulong = strtoul(the_str, NULL, 10);

	printf("%lu\n", the_ulong);

	return 0;
}
```

Beware that if the string represents a number too big for an unsigned long, your result will not be correct.

strtoul is supposed to set errno to ERANGE and return ULONG_MAX when converted value is out of range, but it doesn't actually do so!

---

### Post by dwhitney67 on 2007-11-18
I get the following when using a ridiculously long number (as shown in buf):

```
buf = 1234567890123456789012345678901234567890
val = 4294967295, errno = 34, strerror = Numerical result out of range
```

That output was generated by:
```
      ...
      unsigned long val = strtoul( buf, NULL, 10 );
      printf( "val = %lu, errno = %d, strerror = %s\n", val, errno, strerror( errno ) );
      ...
```

I tried this on both my Ubuntu (7.04) and Fedora 7 systems.  On both systems I have GCC 4.1.2.

---

### Post by samjh on 2007-11-18
That's weird, I'm not getting that at all.

Here's my result trying to use errno, the first value is the input string, the errno = is the errno after strtoul, and the third number is the unsigned long:
```
~/projects/c$ ./fgetsconv
1324
errno = 0
1324
~/projects/c$ ./fgetsconv
123413412341234
errno = 0
1822057970
~/projects/c$ ./fgetsconv
1341234123412341342141234
errno = 0
1050673758
~/projects/c$ gcc --version
gcc (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```

This is the relevant portion of my source code:
```
 35     the_ulong = strtoul(the_str, NULL, 10);
 36 
 37     printf("errno = %d\n", errno);
 38 
 39     printf("%lu\n", the_ulong);
```

I'm using Xubuntu 7.10 amd64, with gcc version listed as above.

---

### Post by dwhitney67 on 2007-11-18
The only other "special" thing I did to my program was to include the <errno.h> header file.

But what you are seeing is strange.

---

