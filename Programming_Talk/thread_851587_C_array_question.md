---
title: "C array question"
date: 2008-07-06
forum: Programming Talk
---

### Post by thefestival on 2008-07-06
I'm trying to match a user input word against a word in an array.  Is this possible? ie:

```
#include <stdio.h>
#include <string.h>
int main() {
		char *arr[] = { "John", "Joe", "Brendan" };
        int i;
		char name;

		printf("Enter your name: ");
		scanf("%s", &name);

		for (i = 0; i < (&arr); i++) {
			if (arr[i] == name)
			    	printf("OK.");
		}
		
		return 0;
}
```

This runs until the for loop kicks in then it gives me a segfault(which is curious as I'm not allocating memory here).

Thanks in advance.

---

### Post by lisati on 2008-07-06
> **thefestival said:**
> I'm trying to match a user input word against a word in an array.  Is this possible? ie:

```
#include <stdio.h>
#include <string.h>
int main() {
        char *arr[] = { "John", "Joe", "Brendan" };
        int i;
        char name;

        printf("Enter your name: ");
        scanf("%s", &name);

        for (i = 0; i < (&arr); i++) {
            if (arr[i] == name)
                    printf("OK.");
        }
        
        return 0;
}
```This runs until the for loop kicks in then it gives me a segfault(which is curious as I'm not allocating memory here).

Thanks in advance.
Doing "if (arr[i] == name)" might work in BASIC, but C usually requires a slightly different approach. Try:```
if (strcmp(arr[i],name)==0)
```

---

### Post by CptPicard on 2008-07-06
You need to either write your own character by character comparison of the strings or use strcmp from the standard library.

What you are doing with == is actually a pointer comparison of the addresses of the first character of each string...

---

### Post by Can+~ on 2008-07-06
```
for (i = 0; i < (&arr); i++) {
```

&arr?

arr is an array, is a pointer to the first element to the array, using & is requesting where that pointer resides.

There are multiple problems on your approach, first, a string is a sequence of characters, and doing

```
char *arr[] = { "John", "Joe", "Brendan" };
```

The loop is going outside of boundries, therefore reading extra stuff on the memory; you need to know the amount of elements inside the array, so your loop can navigate through each of them (and don't go outside) and to compare strings, C has no == operation for strings, but you can use [FONT="Courier New"]strcmp[/FONT] on the [FONT="Courier New"]<string.h>[/FONT] library.

***edit***
While writing my post two persons answered your question already, awesome.

Why not start with other language?

[PHP]namelist = ["John", "Joe", "Brendan"]

if raw_input("Enter your name: ") in namelist:
    print "OK"[/PHP]

*takes shelter from the upcoming flamewar*

---

### Post by lisati on 2008-07-06
> **CptPicard said:**
> You need to either write your own character by character comparison of the strings or use strcmp from the standard library.

What you are doing with == is actually a pointer comparison of the addresses of the first character of each string...
Nicely said, and more eloquently than I could have.

(Lisati wanders off, muttering something about "Denny Crane")

---

### Post by thefestival on 2008-07-06
> **CptPicard said:**
> You need to either write your own character by character comparison of the strings or use strcmp from the standard library.

What you are doing with == is actually a pointer comparison of the addresses of the first character of each string...

Thanks for the responses.  How do I write my own character comp? 

Just saw an answer.

I've got a C course coming up and was looking to get a head start.  BTW how is that for loop going out of bounds?

---

### Post by issih on 2008-07-06
```
#include <stdio.h>
#include <string.h>
int main() {
		char *arr[] = { "John", "Joe", "Brendan" };
        int i;
		char name;

		printf("Enter your name: ");
		scanf("%s", &name);

		for (i = 0; i < (&arr); i++) {
			if (arr[i] == name)
			    	printf("OK.");
		}
		
		return 0;
}
```

There are a few errors here...
This line looks very dodgy to me:
    char *arr[] = { "John", "Joe", "Brendan" };
you create a single character array, then try to assign three separate character arrays of varying length (john, joe and brendan) into it.

The syntax char arr[] = "hello" is a special one, that is only really allowed for strings. In the background it statically allcoates an array with room for 6 characters (the 5 in hello and the terminating null) you can't then put more than 6 characters in it without causing trouble.

You also can't use it quite the way you have at all, as you are trying to create an array of pointers to character arrays, where this special syntax doesn't apply, you must instead specify an array size:

Something like this should work...

char * arr[3];
char str1[] = "John";
char str2[] = "Joe";
char str3[] = "Brendan";
arr[0] = &str1;
arr[1] = &str2;
arr[2] = &str3;


This line is also completely wrong
for (i = 0; i < (&arr); i++)

here you iterate from 0 to the value of the integer formed from the implicit conversion of the pointer address of the start of the badly assigned array arr to an int. This will be a big number, and utterly entirely wrong

instead you need to use something like:
for (i = 0; i < 3; i++)

Hope you follow that :)

---

### Post by thefestival on 2008-07-06
> **issih said:**
> ```
#include <stdio.h>
#include <string.h>
int main() {
		char *arr[] = { "John", "Joe", "Brendan" };
        int i;
		char name;

		printf("Enter your name: ");
		scanf("%s", &name);

		for (i = 0; i < (&arr); i++) {
			if (arr[i] == name)
			    	printf("OK.");
		}
		
		return 0;
}
```

There are a few errors here...
This line looks very dodgy to me:
    char *arr[] = { "John", "Joe", "Brendan" };
you create a single character array, then try to assign three separate character arrays of varying length (john, joe and brendan) into it.

The syntax char arr[] = "hello" is a special one, that is only really allowed for strings. In the background it statically allcoates an array with room for 6 characters (the 5 in hello and the terminating null) you can't then put more than 6 characters in it without causing trouble.

You also can't use it quite the way you have at all, as you are trying to create an array of pointers to character arrays, where this special syntax doesn't apply, you must instead specify an array size:

Something like this should work...

char * arr[3];
char str1[] = "John";
char str2[] = "Joe";
char str3[] = "Brendan";
arr[0] = &str1;
arr[1] = &str2;
arr[2] = &str3;


This line is also completely wrong
for (i = 0; i < (&arr); i++)

here you iterate from 0 to the value of the integer formed from the implicit conversion of the pointer address of the start of the badly assigned array arr to an int. This will be a big number, and utterly entirely wrong

instead you need to use something like:
for (i = 0; i < 3; i++)

Hope you follow that :)

I will eventually.  It seems I have a lot to learn :)

---

### Post by Can+~ on 2008-07-06
[PHP]#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(int argc, char** argv)
{
	const unsigned int arrlength=3, strlength=10;
	unsigned int i;
	char arr[arrlength][strlength], name[strlength];
	
	// Copy stuff into each row of the array.
	strcpy(arr[0], "John");
	strcpy(arr[1], "Joe");
	strcpy(arr[2], "Brendan");
	
	// Request name
	printf("Enter your name: ");
	scanf("%s", name);
	
	// Loop in arrlength
	for (i=0; i<arrlength; i++)
		if (strcmp(arr[i], name) == 0)
			printf("OK\n");
	
	return 0;
}[/PHP]

I usually use a lot of unsigned and const, to avoid some other faults, it's easier to debug.

---

### Post by thefestival on 2008-07-06
> **Can+~ said:**
> [PHP]#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(int argc, char** argv)
{
	const unsigned int arrlength=3, strlength=10;
	unsigned int i;
	char arr[arrlength][strlength], name[strlength];
	
	// Copy stuff into each row of the array.
	strcpy(arr[0], "John");
	strcpy(arr[1], "Joe");
	strcpy(arr[2], "Brendan");
	
	// Request name
	printf("Enter your name: ");
	scanf("%s", name);
	
	// Loop in arrlength
	for (i=0; i<arrlength; i++)
		if (strcmp(arr[i], name) == 0)
			printf("OK\n");
	
	return 0;
}[/PHP]

I usually use a lot of unsigned and const, to avoid some other faults, it's easier to debug.

Two questions: How are unsigned/const's easier to debug?
And why did you add int argc, char **argv when there is no need for command line parameters?

---

### Post by lisati on 2008-07-06
> **thefestival said:**
> Two questions: How are unsigned/const's easier to debug?
And why did you add int argc, char **argv when there is no need for command line parameters?
With a short program like the one we're looking at here, the decision to include argc & argv doesn't matter too much. If, however, you want to expand the program in the future, you might want to leave it in.

Edit: BTW, argv[0] can provide the name of the executable file with many compilers (but not all).

---

### Post by dwhitney67 on 2008-07-06
> **issih said:**
> ```
#include <stdio.h>
#include <string.h>
int main() {
		char *arr[] = { "John", "Joe", "Brendan" };
        int i;
		char name;

		printf("Enter your name: ");
		scanf("%s", &name);

		for (i = 0; i < (&arr); i++) {
			if (arr[i] == name)
			    	printf("OK.");
		}
		
		return 0;
}
```

There are a few errors here...
This line looks very dodgy to me:
    char *arr[] = { "John", "Joe", "Brendan" };
you create a single character array, then try to assign three separate character arrays of varying length (john, joe and brendan) into it.

The syntax char arr[] = "hello" is a special one, that is only really allowed for strings. In the background it statically allcoates an array with room for 6 characters (the 5 in hello and the terminating null) you can't then put more than 6 characters in it without causing trouble.

You also can't use it quite the way you have at all, as you are trying to create an array of pointers to character arrays, where this special syntax doesn't apply, you must instead specify an array size:

Something like this should work...

char * arr[3];
char str1[] = "John";
char str2[] = "Joe";
char str3[] = "Brendan";
arr[0] = &str1;
arr[1] = &str2;
arr[2] = &str3;


This line is also completely wrong
for (i = 0; i < (&arr); i++)

here you iterate from 0 to the value of the integer formed from the implicit conversion of the pointer address of the start of the badly assigned array arr to an int. This will be a big number, and utterly entirely wrong

instead you need to use something like:
for (i = 0; i < 3; i++)

Hope you follow that :)
What is dodgy is your conclusion that the declaration that was given in the OP is incorrect.

The following declaration is actually legal and syntactically correct:
[PHP]char *arr[] = { "John", "Joe", "Brendan" };[/PHP]

What is wrong with the code in the OP is the for-loop conditional, where the value of 'i' is compared with the address of the array 'arr'.  Secondly, the comparison between the i-th string of 'arr' and the name given by the user cannot be compared using the == operator.  I believe both of these problems have been previously mentioned.  Lastly, the declaration of 'name' is incorrect if a string needs to be stored within it.

Here's some better code, but perhaps not the only solution:
[PHP]#include <stdio.h>
#include <string.h>

int main()
{
  const char *arr[] = { "John", "Joe", "Brendan" };
  const size_t arr_size = sizeof(arr) / sizeof(char *);

  char name[80] = {0};

  printf( "Enter your name: " );
  fgets( name, sizeof(name), stdin );

  for ( unsigned int i = 0; i < arr_size; ++i )
  {
    if ( strncmp( name, arr[i], strlen(arr[i]) ) == 0 )
    {
      printf( "OK, name is accepted.\n" );
    }
  }

  return 0;
}[/PHP]

---

### Post by Can+~ on 2008-07-07
> **thefestival said:**
> Two questions: How are unsigned/const's easier to debug?
And why did you add int argc, char **argv when there is no need for command line parameters?

I always have int argc and argv, in case I need them for later.

And unsiged and const's have the great advantage on functions, example:

[PHP]
int function(const int something, const char otherting)
{
    doStuff
}
[/PHP]

You'll rarely change the values given on an argument, say that you accidentally do inside the function and that alter the results; when using const, that will not happen, and it will raise an error properly, instead of causing a segfault.

Depends on how you implement it.

---

### Post by issih on 2008-07-07
I'd been wondering if I was right about the legality of that declaration. the more I thought about it the more likely it seemed the compiler would have choked if it had been wrong.

I'm a c++ bod these days, so I'd have used a string object several hours ago, hence the confusion, thanks for clearing it up.

Good spot on the name input buffer needing a size too

---

### Post by thefestival on 2008-07-07
Thanks for your replies.  I had no idea that name needed an input buffer and still don't exactly know why.

Lots to think about and learn.

Till the next program brings me to tears.

---

### Post by lisati on 2008-07-07
There are probably several ways of tackling this program.
Unless I'm mistaken, another way of determining the array size can sometimes be something like:
```
[COLOR=#000000][COLOR=#007700] const [/COLOR][COLOR=#0000bb]size_t arr_size [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]sizeof[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]arr[/COLOR][COLOR=#007700]) / [/COLOR][COLOR=#0000bb]sizeof(arr[0]); [/COLOR][/COLOR]
```
which will adjust itself to whatever is in arr[0]

---

### Post by dwhitney67 on 2008-07-07
> **lisati said:**
> There are probably several ways of tackling this program.
Unless I'm mistaken, another way of determining the array size can sometimes be something like:
```
[COLOR=#000000][COLOR=#007700] const [/COLOR][COLOR=#0000bb]size_t arr_size [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]sizeof[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]arr[/COLOR][COLOR=#007700]) / [/COLOR][COLOR=#0000bb]sizeof(arr[0]); [/COLOR][/COLOR]
```
which will adjust itself to whatever is in arr[0]
It doesn't adjust to whatever is in arr[0], but merely returns the size of what arr[0] represents, which is a character pointer.  A char(acter) pointer is 4 bytes long, which in this case contains the address pointing to the null-terminated string.

So your example is correct.  You have merely provided another way to calculate the size of the array.  It is acceptable to use your method or the one I posted earlier.

---

### Post by rnodal on 2008-07-08
Why the use of fgets and not gets? gets gets the string from stdin so why type more? :)

---

### Post by nvteighen on 2008-07-08
> **rnodal said:**
> Why the use of fgets and not gets? gets gets the string from stdin so why type more? :)

Because gets may produce a buffer overflow.

From **man gets**:
> 
Never use gets(). Because it is impossible to tell without knowing the data in advance how many characters gets() will read, and because gets() will continue to store characters past the end of the buffer, it is extremely dangerous to use. It has been used to break computer security. Use fgets() instead.


---

### Post by dwhitney67 on 2008-07-08
The same issue with gets() applies to scanf() too!

P.S.  Well, not entirely as unsafe, but close.  One needs to specify the max number of characters to accept for the character array where the string will be stored.
[PHP]
char name[10] = {0};
...
scanf( "%9s", name );[/PHP]

---

### Post by rnodal on 2008-07-08
I figured that all that information was known ahead of time any ways so why bother specifying the array size or that it's coming from stdin. Don't get me wrong it is a neat solution so I was just wondering. Anything in C has the potential of being exploited if proper care is not taken :).


-r

---

