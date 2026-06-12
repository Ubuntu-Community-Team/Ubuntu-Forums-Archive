---
title: "C char** or char[][] strlen"
date: 2010-02-18
forum: Programming Talk
---

### Post by matmatmat on 2010-02-18
Is there a function that finds the longest char array in an array of char arrays (char[][]) or a pointer array of a pointer array (char**) in c? I've tried making one myself:
```

int strlenMultiArray(char array[100][100]){
	int longest = -1;
	for(int i=0; array[i][0]!='\0'; i++){
		int len = strlen(array[i]);
		printf("%s\n", array[i]);
		if(len > longest)
			longest = len;
	}
	return longest;
}

```
The above didn't work and even if it did it isn't a very good solution. I also tried a while(*array) *array++ loop, but that didn't work either.

---

### Post by Zugzwang on 2010-02-18
Technically, that function isn't too bad. First of all, note that by giving the size of the arrays in the function declaration, the array will be passed by value, which is not needed. So you might want to use "char**" instead. Then, you assume that the last string is empty. I wonder if it isn't better to give the number of strings as argument to the function. Thus you would have:
```

int strlenMultiArray(char **array, uint nofStrings){
	int longest = -1;
	for(uint i=0; u<nofStrings; i++){
		int len = strlen(array[i]);
		printf("%s\n", array[i]);
		if(len > longest)
			longest = len;
	}
	return longest;
}

```
This should work (warning: it is untested). I however do not know if it is legal to cast a char[100][100] to a char**. From a technical point of view, that *might* cause problems. Probably someone else knows more about this.

---

### Post by dwhitney67 on 2010-02-18
zugzwang, you are close with your attempt.  However through my own experimentation (and it took me a few tries), I realized that it is inappropriate to compare a signed int with a size_t (unsigned int) as returned by strlen().

I came up with the following, which is similar to yours:
```

#include <string.h>
#include <stdio.h>

#define max(a,b) ((a) > (b) ? (a) : (b))

size_t longestCmdArg(int argc, char** argv)
{
   size_t longest = 0;

   for (int i = 0; i < argc; ++i)
   {
      longest = max(longest, strlen(argv[i]));
   }

   return longest;
}

int main(int argc, char** argv)
{
   if (argc < 2)
   {
      printf("Usage: %s <arg1> [<arg2> ... <argN>]\n", argv[0]);
      return -1;
   }

   --argc; ++argv;

   printf("The longest cmd line arg given is %u characters long.\n",
          longestCmdArg(argc, argv));

   return 0;
}

```

---

### Post by dribeas on 2010-02-18
Array decay into pointer is kind of tricky when you are using multidimensional arrays. Only the actual array decays into a pointer, so the real equivalent signatures are (Note that arrays are never passed by value, no copies of the array are performed):

```

void foo1( int array[100][100] );
void foo2( int (*array)[100] );   // takes a pointer to array of 100 int

void not_foo( int **array ); // not equivalent
int main()
{
   int array[100][100];
   foo1(array);         // ok
   foo2(array);         // ok
   // not_foo(array);   // error
}

```

Which is what you would expect if you think about the memory layout of arrays. When the compiler sees a call to *foo1(array)* with *array* being an actual array, it translates the call to *&array[0]*, that with the definition above is an array of 100 integers, and not a pointer.

From the text above you can infer that you cannot really provide a single function that performs the max length calculation in both an array of literals (*char * array[100]*) and an array of arrays of characters (*char array[100][100]*) as the signatures of the two functions differ. 

If you only want to deal with arrays of pointers to characters, the solution provided by @dwhitney67 is fine. I would just take the result of the *strlen()* in the for loop into a local variable and use that in the macro instead of passing *strlen()* directly. As it is, *strlen()* is evaluated twice for each string that is larger than the previous maximum length.

---

### Post by akvino on 2010-02-18
> **dribeas said:**
> Array decay into pointer is kind of tricky when you are using multidimensional arrays. Only the actual array decays into a pointer, so the real equivalent signatures are (Note that arrays are never passed by value, no copies of the array are performed):

```

void foo1( int array[100][100] );
void foo2( int (*array)[100] );   // takes a pointer to array of 100 int

void not_foo( int **array ); // not equivalent
int main()
{
   int array[100][100];
   foo1(array);         // ok
   foo2(array);         // ok
   // not_foo(array);   // error
}

```

Which is what you would expect if you think about the memory layout of arrays. When the compiler sees a call to *foo1(array)* with *array* being an actual array, it translates the call to *&array[0]*, that with the definition above is an array of 100 integers, and not a pointer.

From the text above you can infer that you cannot really provide a single function that performs the max length calculation in both an array of literals (*char * array[100]*) and an array of arrays of characters (*char array[100][100]*) as the signatures of the two functions differ. 

If you only want to deal with arrays of pointers to characters, the solution provided by @dwhitney67 is fine. I would just take the result of the *strlen()* in the for loop into a local variable and use that in the macro instead of passing *strlen()* directly. As it is, *strlen()* is evaluated twice for each string that is larger than the previous maximum length.

But strlen() will not work on arrays!

I stand corrected it will work on arrays but not how he is using it:

This should not be confused with the size of the array that holds the string. For example:

char mystr[100]="test string";

defines an array of characters with a size of 100 chars, but the C string with which mystr has been initialized has a length of only 11 characters. Therefore, while sizeof(mystr) evaluates to 100, strlen(mystr) returns 11.

---

### Post by dwhitney67 on 2010-02-18
> **akvino said:**
> But strlen() will not work on arrays!

Who said they did?  strlen() works only on null-terminated strings.

---

### Post by dwhitney67 on 2010-02-18
> **dribeas said:**
> ...
As it is, *strlen()* is evaluated twice for each string that is larger than the previous maximum length.

Yes, my bad.  It is for this reason why I dislike macros; they obfuscate the "real" code.

---

### Post by MadCow108 on 2010-02-18
edit: tried it, following is not applicable to this case, please ignore:

you could consider this premature optimization.
lets have a look at the strlen in string.h

extern size_t strlen (__const char *__s)
     __THROW __attribute_pure__ __nonnull ((1));

strlen is declared pure which means the compiler can pull it out of the loop if the memory is not modified during iterations

---

### Post by dribeas on 2010-02-18
> **akvino said:**
> But strlen() will not work on arrays!

No, it works on pointers, but when you use an array as argument, the array will decay into a pointer to the first element, so the actual argument is not the array, but a pointer to the first element.

```

char array[100] = {};
strlen( array );  // translated by the compiler into: strlen( &array[0] )

```

> **MadCow108 said:**
> you could consider this [moving strlen outside of the macro] premature optimization.
lets have a look at the strlen in string.h

The standard does not require that. Your compiler can have that optimization, then you try to compile with a different (previous) version of the compiler, or you change the compiler and then your application starts running slower. In fact this is closer to the definition of **premature pesimization**. Changing the loop to:

```

   for (int i = 0; i < argc; ++i)
   {
      size_t len = strlen(argv[i]);
      longest = max(longest, len);
   }

```

will not make it less readable and is guaranteed not to be slower than the original version, and possibly faster if the compiler does not rewrite the macro expansion to avoid the double call to the function.

---

### Post by MadCow108 on 2010-02-18
yes you are completely right, this was a case of premature posting :)

it can't even remove the call because there are pointer operations in the loop.

---

