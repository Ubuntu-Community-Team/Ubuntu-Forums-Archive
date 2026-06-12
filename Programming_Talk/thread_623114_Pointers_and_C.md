---
title: "Pointers and C"
date: 2007-11-25
forum: Programming Talk
---

### Post by Anonii on 2007-11-25
Greetings,

once again I turn to you for my programming troubles!
I've been teaching myself C, and I'm having serious problems understanding some aspects of pointers. I'm learning from the K&R book, but in my quest to understand pointers I read some Stanford articles (also the Binky video), a guide of Ted Jensen, and some random forum threads, and I still don't get it (Hooray retarded me!)!

So let's start with some examples directly off K&R and my questions on them:

_[SIZE="5"]1) [/SIZE]_
```

int *x;
x = "now is the time";
printf("%d", x);

```

Alright, from what I see by running this, **x** carries a memory address, but I'm sure that I assigned it to "now is the time"! And how can I dereference x now? And when I dereference it, will I get "n" or "now is the time"? I tried to make and run another program to answer my questions, but I always get errors.

**[SIZE="5"]2)[/SIZE]**
```

void strcopy(char *s, char *t)
{
int i;

i=0;
while ((s[i] = t[i]) != '/0')
i++;
}

```

We must call strcopy from main() like this: strcopy(&a[0], &b[0]) (or strcopy(a,b)), right? **Also, we don't use pointers at all inside that function, shouldn't that only copy local copies of s and t, and not a and b? **(This question is the real mind**** for me. I actually spent 20 minutes just thinking of how to ask it, so that I can get answers related to what I'm interested)

**[SIZE="5"]3)[/SIZE]**
```

   #include <stdio.h>
   #include <string.h>

   #define MAXLINES 5000     /* max #lines to be sorted */

   char *lineptr[MAXLINES];  /* pointers to text lines */

   int readlines(char *lineptr[], int nlines);
   void writelines(char *lineptr[], int nlines);

   void qsort(char *lineptr[], int left, int right);

   /* sort input lines */
   main()
   {
       int nlines;     /* number of input lines read */

       if ((nlines = readlines(lineptr, MAXLINES)) >= 0) {
           qsort(lineptr, 0, nlines-1);
           writelines(lineptr, nlines);
           return 0;
       } else {
           printf("error: input too big to sort\n");
           return 1;
       }
   }

   #define MAXLEN 1000  /* max length of any input line */
   int getline(char *, int);
   char *alloc(int);

   /* readlines:  read input lines */
   int readlines(char *lineptr[], int maxlines)
   {
       int len, nlines;
       char *p, line[MAXLEN];

       nlines = 0;
       while ((len = getline(line, MAXLEN)) > 0)
           if (nlines >= maxlines || p = alloc(len) == NULL)
               return -1;
           else {
               line[len-1] = '\0';  /* delete newline */
               strcpy(p, line);
               lineptr[nlines++] = p;
           }
       return nlines;
   }

   /* writelines:  write output lines */
   void writelines(char *lineptr[], int nlines)
   {
       int i;

       for (i = 0; i < nlines; i++)
           printf("%s\n", lineptr[i]);
   }

```

First of all, I removed the qsort function, because I was not interested in it.
Now, on to the question:
**char *lineptr[maxlines]** will give us an array of *maxlines* elements, with each element being a pointer to a char, right? Also, I read that **char s[];** and **char *s;** are the exact same thing. But in the readlines function, we have: _int readlines(char *lineptr[], int maxlines)_, isn't that like saying ****lineptr**? 
Also, in arrays when do we use lineptr[100] and when do we use lineptr[]?



These are my ridiculous questions. I would really appreciate it, if someone wasted some minutes of their time to answer them, since these last days I'm really troubled about my intelligence.


Help a poor soul!

---

### Post by LaRoza on 2007-11-25
This won't work. x is a pointer to an int.

[php]
int *x
x = "now is the time"
printf("%d", x)
[/php]

Are you writing this code yourself or did you get it from somewhere?

We must call strcopy from main() like this: strcopy(&a[0], &b[0]) (or strcopy(a,b)), right? Also, we don't use pointers at all inside that function, shouldn't that only copy local copies of s and t, and not a and b? (This question is the real mind**** for me. I actually spent 20 minutes just thinking of how to ask it, so that I can get answers related to what I'm interested)

Strings in C are character arrays that end in '\0'. The name of the array is a pointer to the first value in the array. So:

[php]
char * name = "LaRoza";

char  name2[7];
name = "LaRoza";

char name3[7] = ['L','a','R','o','z','a','\0']

[/php]

C will add the null terminator ('\0') for you, so you can just use strings, like in name and name2.

When passing strings, you pass the name of the string (array), the end of the string (array) is '\0' which is used by C's string handling functions to get the length.

---

### Post by Anonii on 2007-11-25
> **LaRoza said:**
> This won't work. x is a pointer to an int.

[php]
int *x
x = "now is the time"
printf("%d", x)
[/php]

Are you writing this code yourself or did you get it from somewhere?

Yes, it will. At least in my gcc (It will also spit two warnings out, tho)

[quote=mygcc]
**aasdc@gentoo:~$ ./a.out**
134513776
**aasdc@gentoo:~$ cat test.c**
#include <stdio.h>

void main()
{
int *x;
x = "now is the time";
printf("%d\n", x);
}
[/quote]

---

### Post by LaRoza on 2007-11-25
> 
**char *lineptr[maxlines]** will give us an array of *maxlines* elements, with each element being a pointer to a char, right?


char * name[maxlines] is an array of pointers, or arrays or strings.

---

### Post by LaRoza on 2007-11-25
> **Anonii said:**
> Yes, it will. At least in my gcc (It will also spit two warnings out, tho)

You are using a pointer to an int, cramming a string (array) into, and printing out a digit. You are gettting the pointers value, the memory address. You are also overwriting memory, a buffer overflow.

---

### Post by Anonii on 2007-11-25
Thanks for trying to answer my questions, but I seriously think that I got nothing out of your 3 replies. 
No, really! I'm not trying to be a meany, but in your attempt to answer fast and correctly, you really messed up your posts.
Why? Because, you started with a post telling me about strings which had absolutely nothing to do with my question, you continued with a one-liner answering a rhetoric question of mine, and finished with a post that I didn't understand.

---

### Post by volanin on 2007-11-25
Well, let's see here...
Understanding pointers when they refer to strings is one of the most
confusing things in C, but once you get that down, things become easy easy!

> **Anonii]Greetings[/QUOTE]

Greetings!


> ```

int *x said:**
> 

Trick example this one!
You are indeed right when you say **x** carries a memory address.
It has been defined of the type POINTER TO INT. Every pointer in C
has 4 bytes (32bits) ou 8 bytes (64bits) depending on your platform.

Indeed, all the declarations below are the same:
[i]void *x;
char *x;
int *x;[/i]

They all are a POINTER... with 4 or 8 bytes.
The type (void, char, int) is there only to help the compiler.
Their content will always be an address in memory, pointing to "something".
Be aware that your variable name is **x** and not ***x**.

Going on with your code:
What you have there is a POINTER that is now pointing to the location in
memory where **"now is the time"** is stored. That's what **x**
contains: the address and NOTHING more.

You are NOT copying the string inside x, just its address.
There is no *variable = string* in C... that's what **strcpy** is for.

When you call that **printf "%d"**, you are printing the contents of **x**,
that is... yes... an ADDRESS IN MEMORY. So the output to that command
will be some random 32bit or 64bit number.


[QUOTE]```

void strcopy(char *s, char *t)
{
  ...
}
```

We must call strcopy from main() like this: strcopy(&a[0], &b[0]) (or strcopy(a,b)), right?
Yes, both are one and the same.

[QUOTE]Also, we don't use pointers at all inside that function, shouldn't that only copy local copies of s and t, and not a and b?

Let see...
You are passing the contents of **a** and **b** as parameters.
What are their contents? An ADDRESS to a location in memory, remember?
Coincidentaly, this location in memory contains data that represents a string.

So you are creating copies of these ADDRESS values, and not the string
itself. And the function uses these addresses in s[i] and t[i] to
make use of the string data.


> ```

   ...
   char *lineptr[MAXLINES];  /* pointers to text lines */
   ...
   int readlines(char *lineptr[], int nlines);
   void writelines(char *lineptr[], int nlines);
   ...
   }

```

**char *lineptr[maxlines]** will give us an array of *maxlines* elements, with each element being a pointer to a char, right?

Indeed.
You will get 5000 POINTERS to something in memory.
The char type is a tip to the compiler saying: "It is a char in there".


> Also, I read that **char s[];** and **char *s;** are the exact same thing. But in the readlines function, we have: _int readlines(char *lineptr[], int maxlines)_, isn't that like saying ****lineptr**?

Totally correct.
You can use ****lineptr**, or ***lineptr[]**, or even **lineptr[][]**.
Your choice is just for the sake of code readability.


> Help a poor soul!

:)

---

### Post by LaRoza on 2007-11-25
> **Anonii said:**
> Why? Because, you started with a post telling me about strings which had absolutely nothing to do with my question, you continued with a one-liner answering a rhetoric question of mine, and finished with a post that I didn't understand.

I don't think you should be reading K&R if you don't understand...

Strings had everything to do with your post, mainly because you had posted a function for handlng strings:

[php]
void strcopy(char *s, char *t)
{
    int i;

    i=0;
    while ((s[i] = t[i]) != '/0')
        i++;
}
[/php]

This function requires knowledge of arrays, pointers and strings and how they are related.

---

### Post by Anonii on 2007-11-25
Volanin, you are a God amongst men! Your reply was great and you were clear on almost everything.
What I did not understand was this quote of yours:
> Let see...
You are passing the contents of a and b as parameters.
What are their contents? An ADDRESS to a location in memory, remember?
Coincidentaly, this location in memory contains data that represents a string.

So you are creating local copies of these ADDRESS values, and not the
string itself. And the function uses these addresses in s[i] and t[i] to
make use of the string data.

Can you give me a "more verbose output" of that? Or well, like Joe Miller would say, "now, explain it to me like I'm a four-year-old.".


(Also, why did they use a pointer to a pointer in that last code? How does that help? I also noticed that in argc, and *argv[], and could not understand the purpose that it served.)

---

### Post by LaRoza on 2007-11-25
> **Anonii said:**
> Volanin, you are a God amongst men! Your reply was great and you were clear on almost everything.
What I did not understand was this quote of yours:

Can you give me a "more verbose output" of that? Or well, like Joe Miller would say, "now, explain it to me like I'm a four-year-old.".

Let see...
>You are passing the contents of a and b as parameters.
You are passing a and b to the function

>What are their contents? An ADDRESS to a location in memory, remember?
They are the memory locations, not the value they point to

>Coincidentaly, this location in memory contains data that represents a string.
The memory location is the first character in the string

>So you are creating local copies of these ADDRESS values, and not the
string itself. And the function uses these addresses in s[i] and t[i] to
make use of the string data.
Because you are using the address to manipulate the string, the string itself is not copied and anychange to the pointers values, also changes the string's value. If you alter a variable with by using its memory address in a function, you alter the original variable. Passing by value doesn't do this, which is what C normally does.

As a side note, four year old usually don't do this sort of stuff, so it is difficult to pretend like we are, I hoped it helped, and sorry for the above confusion :-)

---

### Post by volanin on 2007-11-25
> **Anonii said:**
> Can you give me a "more verbose output" of that? Or well, like Joe Miller would say, "now, explain it to me like I'm a four-year-old.".

Ok!
You said:
*Also, we don't use pointers at all inside that function, shouldn't that only copy local copies of s and t, and not a and b?*

Well, what you say is not entirely true.
What you pass to that function are the contents of **a** and **b**.
As you can see, they contain ADDRESSES, and not the string.

So, now **s** will be equal to **a** and **t** will be equal to **b**.
So **s** and **t** will point to the same things as **a** and **b**.
Coincidentally, it's the string!

Through the ADDRESS, your function will be able to access the string that is
located "somewhere"! This address is used when you say **s[i]=t[i]**.

Clearer now?
:)

---

### Post by tyoc on 2007-11-25
> Indeed.
You will get 5000 POINTERS to something in memory.
The char type is a tip to the compiler saying: "It is a char in there".


     Quote:
                                                 Also, I read that **char s[];** and **char *s;** are the exact same thing. But in the readlines function, we have: _int readlines(char *lineptr[], int maxlines)_, isn't that like saying ****lineptr**?                                 
Totally correct.
You can use ****lineptr**, or ***lineptr[]**, or even **lineptr[][]**.
Your choice is just for the sake of code readability.
char *s1 and char s2[] are only equal when s1 points to s2 like s1 = s2.

The real difference is that an array is a constant pointer not a variable pointer like *s ;).

Thus being a constant pointer it need to point actually to something in initialization, because YOU CANT assign a new address to a constant pointer (aka array).

for example:

```

#include <stdio.h>
#define MAXS 3
int main(){
    // char m00[];
    char m0[0];
    char m1[] = "Hola mundo";
    char m2[] = "no estoy";
    char *x = 0;
    int aValue = 10;
    int *pInt = 0;


    char **c;
    char *table[MAXS] = {"uno", "dos", "tres"};
    int i;

    printf("%d\n", sizeof(c));
    printf("%d\n", sizeof(table));

    c = table;
    for(i = 0; i < MAXS; i++){
        printf("%s\n", c[i]);
    }
    

    x = m1;
    printf("1:%s\n", x);
    x = m2;
    printf("2:%s\n", x);
    // me = x;
    // m1 = m1;
    printf("3:%s\n", m0);
    printf("m0=%x, m1=%x, m2=%x\n x=%x, *x=%x or %c\n", m0, m1, m2, x, *x, (char)*x);
    printf("A 'variable' is a constant pointer without declare it like a pointer\n");
    printf("aVal address: %x value: %d\n", &aValue, aValue);
    printf("aVal address: %x value: %d\n", &aValue, *(&aValue));
    pInt = &aValue;
    printf("pInt pointing: %x value: %d\n", pInt, *(pInt));
    printf("Pointer address: %x\n", &pInt);
    return 0;
}

```See m00 it must be initialized in declaration, because it is a constant pointer (ie, you cant reasignate address).

You are already using pointers... variables are also pointers to a certain type, but you dont use * for access the value.

An array of 0 len is a indicator of a block address, see that it have the same address of the next variable.


touht in some way they are semantically related, that dont mean that the look at memory is equal...
If you see the size of table is 12 (wich you can divide between the sizeof(char *) and you will get 3), but the size of the pointer is only 4... (Im in 32-bits).

You actually need some data to point a pointer, an array already point (constantly or at definition) to an address that normally has something inside.

Uncomment the comments for see the errors...

---

### Post by volanin on 2007-11-25
> Thus being a constant pointer it need to point actually to something in initialization, because YOU CANT assign a new address to a constant pointer (aka array).

Ok, I stand corrected!

A pointer defined as **array[]** has a static value, that corresponds to an address, and it cannot be modified.
**array = newvalue;** generates a compile-time error.

A pointer defined as ***array** can have it's value, that corresponds to an address, changed anytime.
**array = newvalue;** is ok.


> An array of 0 len is a indicator of a block address, see that it have the same address of the next variable.

I have never heard of that...
So I tested, of course!

```
#include <stdio.h>

int main( void )
{
  char var0[0];
  char var1[] = "Hello";
  char var2[] = "World";

  printf( "%d, %d, %d\n", var0, var1, var2 );
  return 0;
}
```

It returns:
**-1081423948, -1081423954, -1081423960**

Compiled with gcc version 4.1.3 *(gcc -o program program.c)*
But I also tested your code, and the values came out the same.
What is going on?
:)

---

### Post by LaRoza on 2007-11-25
> **volanin said:**
> 

It returns:
**-1081423948, -1081423954, -1081423960**

I ran it (but didn't compile it). They are the pointer address. See them all in a row?

You gave the name of an array, a pointer to the first member. Each array was stored in sequential memory addresses, and the difference between them is the length of the string (array). %d is for numbers, use %s for strings.

---

### Post by volanin on 2007-11-25
> **LaRoza said:**
> I ran it (but didn't compile it). They are the pointer address. See them all in a row?

Yes yes, I know that!
The point is, the two first values should have been the same.
As tyoc said: *"An array of 0 len is a indicator of a block address, see that it have the same address of the next variable."*

And it really does happen in his program.
He defines:

```
    char m0[0];
    char m1[] = "Hola mundo";
    char m2[] = "no estoy";
```

And the values in the output of his program are indeed the same:
**m0=bf82070c, m1=bf82070c, m2=bf820717**
:confused:

---

### Post by LaRoza on 2007-11-25
I get the same results, the first value is different.

---

### Post by Anonii on 2007-11-25
First of all, I want to thank you **LaRoza**, **volanin** and **tyoc** for trying to help me out.
I have one more question. 

1) We will use a pointer in a function because we want to change the value of that variable outside of that function, too. In the main() function then, why do we use char ***argv[]**, and not** argv[]**? We want to be able to change the parameters we gave when we executed the program?

---

### Post by CptPicard on 2007-11-25
You could just as well write **char **argv**, like I tend to do. It's an *array of pointers to char*, that is, an array of strings... there are, after all, possibly multiple parameters, and the count is given by **argc**. So something like argv[0] is the first pointer to string, that is, the pointer to the beginning of the first runtime parameter. Same for argv[1] and so on, until argv[argc-1].

---

### Post by LaRoza on 2007-11-25
> **Anonii said:**
> 
1) We will use a pointer in a function because we want to change the value of that variable outside of that function, too. In the main() function then, why do we use char ***argv[]**, and not** argv[]**? We want to be able to change the parameters we gave when we executed the program?

It isn't obvious, but these values are placed on the stack by the system when the program is run.

As stated before, it is * argv[] or ** argv, because it is an array of strings. Other languages, like Java, use "String argv[]" in the same place because Java has a string data type.

---

### Post by tyoc on 2007-11-25
>  But I also tested your code, and the values came out the same.
What is going on?mmm If Im not wrong I have printed all the pointers with %x, that is for print them in hex(adecimal), the thing is that the representation in "decimal" of those numebrs is negative, if you use %x for print pointers, you will get more "normal" results...

Here is the result I get for my code

```
$ ./a.out 
4
12
uno
dos
tres
1:Hola mundo
2:no estoy
3:Hola mundo
m0=bfec561c, m1=bfec561c, m2=bfec5627
 x=bfec5627, *x=6e or n
A 'variable' is a constant pointer without declare it like a pointer
aVal address: bfec560c value: 10
aVal address: bfec560c value: 10
pInt pointing: bfec560c value: 10
Pointer address: bfec5608
```4 and 12 are the sizes of s and x (IIRC)
uno, dos, tres are the prints of x[i] IIRC

m0=bfec561c, m1=bfec561c, m2=bfec5627 are the addresses, you see m0 and m1 have point to the same address... thuse semantically you can take that as a start of something... in fact any address is a start of something and thus depend in how you handle it (integers, chars??, unsigned, floating, structures??, functions [http://www.newty.de/fpt/index.html](http://www.newty.de/fpt/index.html) ??)... is only a "semantic" thing...

> aVal address: bfec560c value: 10
aVal address: bfec560c value: 10
pInt pointing: bfec560c value: 10Aval is a normal int variable
the second like is the same, showing that you can use *& (in fact they "eliminate" each other) thus showing that at end a variable is also a pointer to certain type (but equal that arrays you cant change the address that it is pointing to, or the type of the pointed address, only the content), the third way is the same showing it with a pointer to an int.

And finally the pointer address (not the address to wich it points)... it is needed when inside a function you want to modify to wich place the pointer is pointing and not the contents of the pointed address (see is different change the values at the pointed address, that change the value of the pointed address) (dont know if my English is the correct, but hope you ge ht e idea).

-------------------

The "thing" is that the compiler has a table whit variables in them some like

The compiler declare a name for an address, calculate the address and use it in the program. thus if the anterior variable has a size of zero, then the next variable will be at the same place ;)

[B]m0 bf82070c
m1 bf82070c
m2 bf820717
[/B]

also you can have **void *** pointer that mean something like I will point to somewhere and don't matter the type of the address I point to... later perhaps I will take care of the type assigning it to a specific pointer with semantics of specific type (forthe compiler) like a pointer to user definied struct, or a pointer to ints, unsigned ints and so on.

---

### Post by volanin on 2007-11-26
> Im not wrong I have printed all the pointers with %x, that is for print them in hex(adecimal), the thing is that the representation in "decimal" of those numebrs is negative, if you use %x for print pointers, you will get more "normal" results...

Indeed you are right, but that's NOT the problem.


> The compiler declare a name for an address, calculate the address and use it in the program. thus if the anterior variable has a size of zero, then the next variable will be at the same place

The problem is that this affirmation is NOT RIGHT.
The zero-sized variable WILL NOT be at the same place as the next.

In GCC 4.1, I verified that this will happen only if the next variable is 8 bytes or more in size.
For example:

```
#include <stdio.h>

int main( void )
{
   char m0[0];
   **char m1[] = "Hello";  // This has LESS than 8 bytes.**
   printf( "%x, %x", m0, m1 );
   return 0;
}
```

In this example, m0 and m1 will NOT HAVE the same value, and this can be checked
by the printf function... but if you do a simple change:

```
#include <stdio.h>

int main( void )
{
   char m0[0];
   **char m1[] = "HelloWorld";  // This has MORE than 8 bytes.**
   printf( "%x, %x", m0, m1 );
   return 0;
}
```

In this case, m0 and m1 WILL HAVE the same value.
As they do in your example program.


BUT...
Let's check ICC (Intel C Compiler).

In BOTH examples, m0 and m1 WILL BE DIFFERENT, and NOT have the same value.
So I believe that this is a GCC bug, or a lack of specification...

... but assuming that zero-sized arrays will have the same position in the compiler's
table as the next variable is NOT correct.
You can check for yourself!
:)

---

### Post by tyoc on 2007-11-26
hehe, I _guess_ that is some behavior of align, that is the only I can guess.

But I vote for the behaviour of the "block mark" XD... hehe, it sound more logic (for me).

> but assuming that zero-sized arrays will have the same position in the compiler's
 table as the next variable is NOT correct.

---

### Post by aks44 on 2007-11-26
> **tyoc said:**
> hehe, I _guess_ that is some behavior of align, that is the only I can guess.

But I vote for the behaviour of the "block mark" XD... hehe, it sound more logic (for me).

If it sometimes works, sometimes not... then it means that *_it only works by chance_*, IOW it is *_undefined behaviour_*.


Now, check that (I just did it...):

```
#include <stdio.h> 

int main()
{
  char foo_addr[0];
  int foo = 3;
  char bar_addr[0];
  char bar[] = "0123456";
  
  printf("foo_addr = %x\n",(unsigned)foo_addr);
  printf("foo      = %x\n",(unsigned)&foo);
  printf("bar_addr = %x\n",(unsigned)bar_addr);
  printf("bar      = %x\n",(unsigned)bar);
  return 0;
}
```


> **tyoc said:**
> An array of 0 len is a indicator of a block address, see that it have the same address of the next variable.
So foo_addr is supposed to hold the address of foo, right? Well, see the results:

```
$ ./test
foo_addr = bfdbb4b8
foo      = bfdbb4b4
bar_addr = bfdbb4b8
bar      = bfdbb4b8
```


Pretty funny, huh? ;)

---

### Post by volanin on 2007-11-26
Searching around the net I came across this ([http://www.ddj.com/cpp/184401956](http://www.ddj.com/cpp/184401956)):

**[i]"Zero-Length Arrays.** Standard C requires all arrays to contain at least one element, but in GNU C, you can declare zero-length arrays.
This can be very useful in applications where the size of the array needs to be dynamic. Consider Listing 3, in which the zero-length
array becomes an array of len bytes when returned from getPayload."[/i]

```
**Listing 3:**

typedef struct {
  int len;
  char data[0];
} payload_t;

payload_t *getPayload( int len )
{
  payload_t *payload = (payload_t *)0;

  payload = (payload_t *)malloc( sizeof(payload_t) + len );
  if (payload) payload->len = len;

  return payload;
}
```

So, in practice, this is a struct defined to hold a **non-defined** amount of data.
This function will allocate an amount of memory determined at runtime by the value
of the parameter passed to it + size of the struture, that in this case is the same
as sizeof(int).

The first byte of the memory allocated will always be an **int** that holds the
total length of the data, and will be accessible through the **payload.len** variable.
And the rest of the data loaded into this allocated space will be accessible through the
**payload.data** variable.

Another example:

```
struct BufferHeader;
{
  long fileLength;
  char fileData[0];
};


int main( void )
{
  struct BufferHeader *header;


  header = malloc( GetFileSize(SOMEFILE) + sizeof(struct BufferHeader));
  if( header == NULL )
    PrintErrorAndExit( );

  header.fileLength = GetFileSize( SOMEFILE );
  ReadFileContentsToMemoryBuffer( SOMEFILE, header.fileData );
  
  // Do something with the file contents...


  free( header );
  return 0;
}
```

---

### Post by slavik on 2007-11-26
simple stuff ...

char *a;

what is variable 'a'? it is a char * (pointer to a character)

what is variable '*a'? it is a char (the actual dereferenced character)

does that clear anything up? :)

---

### Post by aks44 on 2007-11-26
> **slavik said:**
> char *a;

what is variable 'a'? it is a char * (pointer to a character)

what is variable '*a'? it is a char (the actual dereferenced character)

I have to admit I never quite understood the C way of saying **char *a;**, it seems illogical to me.

Maybe it's because I'm used to the C++ way (which puts the star next to the type: **char* a**), but to me it has been easier to understand that **a** is a **char*** rather than the fact that ***a** is a **char**. Even though at the end both notations are equal, I still find the C++ way more clear since it emphasizes on *_the type of_* the variable **a**, rather than on *_the type pointed-to_* by **a**. YMMV I guess.

---

### Post by tyoc on 2007-11-26
volanin, thus my memory was right in a "mark for a block of memory", but it should be inside a struct I guess?? and not like a local variable... or a global var, I suppose.

And only argeen a little more, thus the "address" that it point, is not the next, but the anterior...

---------------------------------------
>  $ ./test
 foo_addr = bfdbb4b8
 foo      = bfdbb4b4
 bar_addr = bfdbb4b8
 bar      = bfdbb4b8 yea, that is pretty funny, more watching that a variable is bweten them.

---

### Post by volanin on 2007-11-26
> **tyoc said:**
> volanin, thus my memory was right in a "mark for a block of memory", but it should be inside a struct I guess?

Yeah, you were right in the "mark for a block of memory" indeed!
Man, I truly didn't know all this stuff!
:)

---

### Post by tyoc on 2007-11-26
as a side note, and off topic for sure.. I really will want some like

```
checkpointerpath(header->some->anythinhg->yea->ImHere)
```

Instead of do the nesting of if blocks checking for not null... dont ask why I want that, I only needed, and want my code look more compact... hehehe.

---

### Post by LaRoza on 2007-11-26
> **aks44 said:**
> I have to admit I never quite understood the C way of saying **char *a;**, it seems illogical to me.

Maybe it's because I'm used to the C++ way (which puts the star next to the type: **char* a**), but to me it has been easier to understand that **a** is a **char*** rather than the fact that ***a** is a **char**. Even though at the end both notations are equal, I still find the C++ way more clear since it emphasizes on *_the type of_* the variable **a**, rather than on *_the type pointed-to_* by **a**. YMMV I guess.

It doesn't matter where the * is.

```

char * a
char* a
char *a 

```
These are all the same. I do it the first way (in the middle)

---

### Post by CptPicard on 2007-11-26
Aks, you just made my mind click in a funny way :) I've always written **char *a** without ever thinking much of it in the sense that the weight is on declaring the type of *dereferenced* stuff -- it's just always been "a is a char-pointer" to me. Of course it's obvious from a linguistic point of view, but never really "hit" me before :)

---

### Post by samjh on 2007-11-27
> **CptPicard said:**
> Aks, you just made my mind click in a funny way :) I've always written **char *a** without ever thinking much of it in the sense that the weight is on declaring the type of *dereferenced* stuff -- it's just always been "a is a char-pointer" to me. Of course it's obvious from a linguistic point of view, but never really "hit" me before :)

I always use the **char *a** form, both in C and C++.

The way I read it is: **a* holds a char.  That way, I don't end up with the illusion of *a* being a char, because only **a* is a char, *a* is a pointer. :)  My way of considering variables is that they hold or represent a type, rather than being a type.  It makes thinking about classes and objects easier too, because an object represents or holds a class, rather than being a class.  So if I ever come across a variable name or object name that changes reference to different types or classes, my brain doesn't come to a screeching halt trying to get over the change.

If I use Aks44's way of reading it, I get confused.

Odd how different minds comprehend little things like this in different ways. :)

---

### Post by smartbei on 2007-11-27
Interesting discussion :D.

I find myself conforming to whatever code base I am currently using, and when I write new code I usually use **char *a**, since I will occasionally have things like **char *a, *b, *c** and in that case it doesn't look as good (to me) to have **char* a, * b, * c**. It looks more confusing - a bunch of '*' and floating around in the latter option with it being none-too-clear which variable the '*' belongs to.

@tyoc: Your question doesn't make sense, unless you do something convulted like overriding the '->' operator to check for null in a class and inheriting from that class. Then you could have something like:
```

if (header->some->anythinhg->yea->ImHere == NULL)
     //Abort

```
While being sure that it also checks the validity of 'header', 'some', 'anythinhg', 'yea', and 'ImHere'.

This is actually an interesting idea, though I am not sure if it is practical (specifically, if 'header' = NULL, will the overloaded '->' be called?)...Will try it out sometime. Assuming the overloaded '->' is not called, you would just have to make sure that header is an actual instance, and then have the overloaded '->' return an instance of the base class supporting the new '->'. It could ignore the rest of the tree, and have an overloaded '==' returning NULL so that the 'if' would work.

---

### Post by tyoc on 2007-11-27
> @tyoc: Your question doesn't make sense, unless you do something convulted like overriding the '->' operator to check for null in a class and inheriting from that class. Then you could have something like:
if (header->some->anythinhg->yea->ImHere == NULL)//Abort

While being sure that it also checks the validity of 'header', 'some', 'anythinhg', 'yea', and 'ImHere'.

Au, but I want it for C :)... and sure I want to skip "magically" (help of compiler) all those checks, with something like "check pointer path", instead to handcode all those chained if things ;).

---

### Post by aks44 on 2007-11-27
> **smartbei said:**
> when I write new code I usually use **char *a**, since I will occasionally have things like **char *a, *b, *c** and in that case it doesn't look as good (to me) to have **char* a, * b, * c**.

Heh, good point. I for one (almost) never declare multiple variables on a single line, just because I (almost) always initialize them and find it confusing to have several initializations on the same line:
```
int a = 2, b = 3, c = 4; // ugly and confusing
```


And since I **always** initialize pointers, I never have to declare things like **char* a, * b, * c**. ;)


> **samjh said:**
> If I use Aks44's way of reading it, I get confused.

Odd how different minds comprehend little things like this in different ways. :)
Blame my ASM background for that... :p
In my POV, the usual C++ way (stars next to the type) is "closer to the metal" and due to my background it was very straightforward for me to get it.

Not that it really matters anyway, but it's indeed funny (IMHO) to discuss about such things.


//------------------------------------------------------------


@tyoc: C can't handle that syntax. Maybe it would be possible using variadic macros (if C has them)?

But why not something like:
```
if (  !header
    ||!header->some
    ||!header->some->anythinhg
    ||!header->some->anythinhg->yea
    ||!header->some->anythinhg->yea->ImHere)
  // abort
```

Granted, this is not as compact as you want, but it can still be made an ugly, compact one-liner. Add a little comment to make it readable and you're good to go... :)

---

### Post by volanin on 2007-11-27
> **aks44 said:**
> C can't handle that syntax. Maybe it would be possible using variadic macros (if C has them)?

C has variadic macros.
But the macros can't be recursive.
So, it cannot be implemented anyway.

---

### Post by aks44 on 2007-11-27
> **volanin said:**
> But the macros can't be recursive.
I was rather thinking about something along the lines of BOOST_PP_FOR. Not sure if it is easy to (randomly) access individual items from the variadic arguments list though (I don't use much the preprocessor, and have usually no use for variadic macros).

But I have the strange feeling it could be done... I'll probably look into that (later) just for the sake of it. :p

---

