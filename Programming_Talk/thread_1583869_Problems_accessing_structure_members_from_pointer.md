---
title: "Problems accessing structure members from pointer"
date: 2010-09-28
forum: Programming Talk
---

### Post by erupter on 2010-09-28
Looks quite stupid doesn't it?
The title...
Anyway i'm having big problems.
I'm defining my struct like this
```
struct map_cell_vector {
  int px;
  int py;
  struct map_cell_vector *next;
};
```problems:
1) i can't use "typedef" inline with the struct definition, i have to use it on another line afterwards. why???

2) if I define a variable like
```
map_cell_vector *new = malloc (sizeof(map_cell_vector));
```or
```
map_cell_vector *new = (map_cell_vector *) malloc (sizeof(map_cell_vector));
```then
new->px = 0;

fails, the compiler says
```
error: request for member ‘px’ in something not a structure or union
```I can't begin to understand what i'm doing wrong.
I've looked at every example i could on the internet and I'm even using a library that declares structs and pointers i can then access correctly.
Help :(

---

### Post by slavik on 2010-09-28
try:
```

struct map_cell_vector *new = (struct map_cell_vector *)malloc(sizeof(struct map_cell_vector));

```

'struct map_cell_vector' is the type

---

### Post by erupter on 2010-09-28
> **slavik said:**
> try:
```

struct map_cell_vector *new = (struct map_cell_vector *)malloc(sizeof(struct map_cell_vector));

```'struct map_cell_vector' is the type

That's right but why?
My actual declaration is this:
```
struct map_cell_vector {
  int px;
  int py;
  struct map_cell_vector *next;
};

typedef map_cell_vector;
```

it should not be necessary.
And why can't i use
```

typedef struct map_cell_vector {
  int px;
  int py;
  struct map_cell_vector *next;
};

```

?????????

---

### Post by saulgoode on 2010-09-28
> **erupter said:**
> That's right but why?
My actual declaration is this:
```
struct map_cell_vector {
  int px;
  int py;
  struct map_cell_vector *next;
};

typedef map_cell_vector;
```

it should not be necessary.
And why can't i use
```

typedef struct map_cell_vector {
  int px;
  int py;
  struct map_cell_vector *next;
};

```

?????????
C maintains separate namespaces for different entities. One could have a function, variable, struct, and type all named "x" and C would consider each of them distinct from the others. Without analyzing the details of your code too deeply, the problem undoubtedly lies with the type "map_cell_vector" being treated as distinct from the struct "map_cell_vector".

---

### Post by schauerlich on 2010-09-28
> **erupter said:**
> 
And why can't i use
```

typedef struct map_cell_vector {
  int px;
  int py;
  struct map_cell_vector *next;
};

```

?????????

[http://en.wikipedia.org/wiki/Typedef](http://en.wikipedia.org/wiki/Typedef)

A typedef looks like this:

```
typedef old type new_type
```

Where 'old type' is some type expression, and new_type is an identifier for the old one. In this case, "struct map_cell_vector { /*...*/}" is the old type, and after the close bracket you need to put an identifier for the type. Something like:

```
typedef struct foo {
    int bar;
} foo;
```

---

### Post by erupter on 2010-09-28
> **schauerlich said:**
> Something like:

```
typedef struct foo {
    int bar;
} foo;
```

I have been going crazy for hours with this.
Foo I am indeed :P

---

### Post by erupter on 2010-10-01
I follow up on this as I have another problem which seems somewhat related.

I declared
```
int **array;

array= malloc (number1 * sizeof(int));
for (i=0;i<number1;i++)
  for (j=0; j<number2; j++)
    array[i][j]=i+j;

```and it works.

Now i have
```

typedef struct XY_Coord {
  float px;
  float py;
} XY_Coord;

XY_Coord *hit_coordinates_original, *hit_coordinates_discrete, *robot_map_cell, *source_coordinates_original, *source_coordinates_discrete;

hit_coordinates_original = (XY_Coord *) malloc (sonar->pose_count * sizeof(XY_Coord));
hit_coordinates_discrete = (XY_Coord *) malloc (sonar->pose_count * sizeof(XY_Coord));


```which doesn't compile.
To me it seems identical to the above.
But the compiler at the first assignment says
```

incompatible types when assigning to type &#8216;XY_Coord&#8217; from type &#8216;struct XY_Coord *&#8217;
```I'm surely doing something wrong, but i can't pinpoint it.
I need an array of pointers to type XY_Coord.
Even if i do
```


hit_coordinates_original = (XY_Coord *) malloc (sonar->pose_count * sizeof(XY_Coord *));
hit_coordinates_discrete = (XY_Coord *) malloc (sonar->pose_count * sizeof(XY_Coord *));

  for (i=0;i<sonar->pose_count; i++) {
    hit_coordinates_original[i]= (XY_Coord *) malloc(sizeof(XY_Coord));
    hit_coordinates_discrete[i]= (XY_Coord *) malloc(sizeof(XY_Coord));
  }

```it doesn't compile.

If i declare arrays like
```

XY_Coord *ptr= (XY_Coord *) malloc (sizeof (XY_Coord)); 
```it works.
If i declare an array
```

XY_Coord *temp = (XY_Coord *) malloc (sonar->pose_count * sizeof (XY_Coord));
```it works.
Since i have the first declaration in an H file to make it global, it seems something goes wrong. But i don't understand what.


Ok i got it different.
Using this notation
```

  hit_coordinates_original = (XY_Coord *) malloc (sonar->pose_count * sizeof (XY_Coord*));
  hit_coordinates_discrete = (XY_Coord *) malloc (sonar->pose_count * sizeof (XY_Coord*));
```

or this
```

  hit_coordinates_original = (XY_Coord *) malloc (sonar->pose_count * sizeof (XY_Coord));
  hit_coordinates_discrete = (XY_Coord *) malloc (sonar->pose_count * sizeof (XY_Coord));

```

compiles, but makes an array of structs, not an array of pointers to struct.
So all my following code using hit_blabla->px doesn't work because the compiler wants hit_blabla.px.
I'm going crazy :(

---

### Post by erupter on 2010-10-01
After 2hrs of struggling i made it.
Correct declaration and definitions are
```

XY_Coord **hit_coordinates_original, **hit_coordinates_discrete;

hit_coordinates_original = (XY_Coord**) malloc (sonar->pose_count * sizeof (XY_Coord*));
  hit_coordinates_discrete = (XY_Coord**) malloc (sonar->pose_count * sizeof (XY_Coord*));

  
  
  for (i=0;i<sonar->pose_count; i++) {
    hit_coordinates_original[i]=  malloc(sizeof(XY_Coord));
    hit_coordinates_discrete[i]=  malloc(sizeof(XY_Coord));

  }


```

Why is it a pointer to pointer?
It seems to me it should be an array of pointers to structure.
Since arrays are part of C, why does it appear like a bi-dimensional array?

---

### Post by worksofcraft on 2010-10-01
```

int **array;

array= malloc (number1 * sizeof(int));
[B]// I think you need:
// array= malloc (number1 * number2 * sizeof(int));[/B]
for (i=0;i<number1;i++)
  for (j=0; j<number2; j++)
    array[i][j]=i+j;

```
I'll be back in a mo I see if I can work out what's going on there...

...edit... so basically what you really want to do is expressed in this C++ code:
```

// g++ erupter.cc
struct XY_Coord {
  float px;
  float py;
};

int main() {
	int pose_count = 10;
	XY_Coord *hit_coordinates_original, *hit_coordinates_discrete;
	hit_coordinates_original = new XY_Coord[pose_count];
	hit_coordinates_discrete = new XY_Coord[pose_count];
}

```

and that compiles fine, so all we have to do is convert it into the ancient obsolete C language now?
```

#include <stdlib.h>

// gcc -Wall erupter.c
typedef struct {
  float px;
  float py;
} XY_Coord ;

int main() {
	int pose_count = 10;
	XY_Coord *hit_coordinates_original;

	hit_coordinates_original = (XY_Coord *) malloc(pose_count * sizeof(XY_Coord));
	return 0;
}

```
there.. I just cut it down to one instance because it's the same for the others. Does that help?

---

### Post by nvteighen on 2010-10-01
> **erupter said:**
> 
Why is it a pointer to pointer?
It seems to me it should be an array of pointers to structure.
Since arrays are part of C, why does it appear like a bi-dimensional array?

Because an "array" in C is a somewhat nebulose entity if you don't know what Assembly magic is happening.

Ok, you'll hear some people say that "arrays are pointers and viceversa", which is a very pedagogical but not-quite-true way to explain the fact that you can pass an array to a function or return an array from a function (like malloc can do) by declaring it as a pointer.

What happens is the following: an array is a pointer to its first element; you get to the subsequent elements by pointer arithmetic, so that a[2] is actually *(a + 2), i.e. dereferencing whatever there is at address a + 2.

But, this is not that simple: there's a difference between declaring something as an char[3] and declaring something as an char *, even when you don't use malloc(). Please, take a look at this program:

```

#include <stdio.h>

int main(void)
{
    char array[10] = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9};
    char *pointer = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9};

    (void)printf("sizeof(array): %d\nsizeof(pointer): %d\n", sizeof(array), 
                 sizeof(pointer));

    return 0;
}

```

The output will tell you that the sizeof(pointer) is, effectively, whatever size pointers have in your platform. Why? Well, it's difficult to explain without recurring to Assembly, so I won't do it. But basically, it's about how you give the information to the compiler: in array's declaration, you're making sure that that's an 10 char's long array, while pointer could end up pointing to an segment of char's no matter how long. 

But, keep in mind this is a feature. For example, look at a function like **char *fgets(char *, unsigned int, FILE *)**. Concentrate on the (char *) parameter and the (char *) return value... ok, yes, you can declare a function's signature to be void my_func(char[256]), accepting only 256 char **arrays** as a parameter, but that's completely unflexible... A function like fgets has to be flexible in order to work with buffers of any length (and that's why it takes the second parameter to state that length). Using char * is a way to declare "arrays of undefined length", but if their length is undefined, then you can't expect sizeof() work on it.

Btw, there's a **very** misleading syntax available in C (and C++) that allows you to declare pointer as **char pointer[]**. That doesn't declare an array, but one of those pointers "as undefinitely long array". Be careful with that.

So, a double pointer can be seen as a 2D matrix for the same reason as a simple pointer can be seen as an array. But always, taking this in account.

---

### Post by trent.josephsen on 2010-10-01
> **worksofcraft said:**
> and that compiles fine, so all we have to do is convert it into the ancient obsolete C language now?
Sheesh, give it a rest already.

---

### Post by worksofcraft on 2010-10-01
> **trent.josephsen said:**
> Sheesh, give it a rest already.

Was there some error in my conversion back to C, or did I fail to understand what the OP wanted? Perhaps you care to explain?

---

### Post by Bachstelze on 2010-10-01
> **worksofcraft said:**
> Was there some error in my conversion back to C, or did I fail to understand what the OP wanted? Perhaps you care to explain?

He's probably annoyed, just like the rest of us, by the fact that you're constantly bashing C as "obsolete".  You're entitled to your opinion, but feeling the need to add such adjectives whenever you talk about C is just childish and, indeed, annoying.

---

### Post by worksofcraft on 2010-10-01
> **Bachstelze said:**
> He's probably annoyed, just like the rest of us, by the fact that you're constantly bashing C as "obsolete".  You're entitled to your opinion, but feeling the need to add such adjectives whenever you talk about C is just childish and, indeed, annoying.

I take the time to look at the problem that the OP posted and I take the time to work out what he/she is trying to achieve and I come back and edit my post as I make progress, to explain what I'm doing.

As far as I can see the problem that the op has is with the syntax of the C language.

This forum is for discussion of all programming topics and explaining about weaknesses and difficulties with different computer languages is appropriate. OTOH, getting annoyed at someone's choice of words and using adjectives like "childish" without contributing anything to subject are less so IMO.

---

### Post by nvteighen on 2010-10-02
> **worksofcraft said:**
> 
This forum is for discussion of all programming topics and explaining about weaknesses and difficulties with different computer languages is appropriate. OTOH, getting annoyed at someone's choice of words and using adjectives like "childish" without contributing anything to subject are less so IMO.

Yeah, but stating that C is "obsolete" when it is widely used in programming is also childish. I do agree with your complaints about C, but please, realize that C isn't obsolete at all... BCPL, COBOL, FORTRAN77, Simula, etc. may be, but not C.

---

### Post by erupter on 2010-10-02
> **nvteighen said:**
> Yeah, but stating that C is "obsolete" when it  is widely used in programming is also childish. I do agree with your  complaints about C, but please, realize that C isn't obsolete at all...  BCPL, COBOL, FORTRAN77, Simula, etc. may be, but not C.

C is somewhat obsolete in my opinion too.
But sometimes you just can't do anything else.
Microcontrollers have compilers for assembler, basic and c.
What do you choose?
Also i do not know C++ and find it very difficult to read, while visual c# and visual basic are a lot more comfortable, but are not available under linux (unless talking about the .NET port, but that's beyond the point).
Anyway i'm stuck with c and at the moment i can't do nothing about it.

> **worksofcraft said:**
> 
```

#include <stdlib.h>

// gcc -Wall erupter.c
typedef struct {
  float px;
  float py;
} XY_Coord ;

int main() {
    int pose_count = 10;
    XY_Coord *hit_coordinates_original;

    hit_coordinates_original = (XY_Coord *) malloc(pose_count * sizeof(XY_Coord));
    return 0;
}

```there.. I just cut it down to one instance because it's the same for the others. Does that help?

I already found the option you stated, but that way you are actually declaring an array of structs (as i said in some other post of mine before yours).
So had my program to pass hundreds of values it would have to pass the entire hundreds of structures. Clearli defeating the principle of deferencing.
So i needed pointers.
And in order to have pointers i had to result to the solution posted:
```

XY_Coord **hit_coordinates_original;
etc
```I tried to understand your explanation but it requires quite a bit of thinking on my side.
I haven't grasped it all apart from the fact that in order to be so powerful at the time C had to come up with some kind of "magic". And this magic are pointer which currently i fail to understand completely in all aspects.
Well i think i'll just study more and do more mistakes :P

---

### Post by slavik on 2010-10-02
> **nvteighen said:**
> Yeah, but stating that C is "obsolete" when it is widely used in programming is also childish. I do agree with your complaints about C, but please, realize that C isn't obsolete at all... BCPL, COBOL, FORTRAN77, Simula, etc. may be, but not C.
I disagree with FORTRAN being obsolete. :P

FORTRAN is still heavily used for scientific (distributed) purposes.

---

### Post by dwhitney67 on 2010-10-02
```

XY_Coord* ptr = NULL;

```
The pointer above point to one location in memory.  Currently, as shown above, it is pointing to NULL.  If you assign it the returned value from malloc() (assuming the call was successful), then it would point to a valid location in memory.  This location may be followed by additional "reserved" sequence of memory locations that was requested by the malloc() call.

This is how it is represented in a diagram, where each block is a location in memory (note the 'ptr' may be declared on the stack or on the heap, depending on how/where it is declared, but this is unimportant for now).
```

+--------+
|  ptr   |
+--------+
       \
        \     +---------+      +---------+
         ---> |  obj 0  |  ... | obj N-1 |
              +---------+      +---------+

```
So, with the following code, ptr will point to the first of 3 equally sized objects on the heap:
```

const int N = 3;

XY_Coord* ptr = malloc(N * sizeof(XY_Coord));

```

Now, for the following:
```

XY_Coord** ptr = NULL;

```
Here, ptr is a pointer to another pointer; it is commonly used to represent a two-dimensional array.

It would look something like this if used to implement a two-dimensional array:
```

+--------+
|  ptr   |
+--------+
       \
        \     +---------+ 
         ---> |  loc 0  |
         |    +---------+
         |            \
         |             \     +---------+      +---------+
         |              ---> |  obj 0  |  ... | obj N-1 |
         |                   +---------+      +---------+
         .
         .
         .
         .    +---------+ 
         ---> | loc Y-1 |
              +---------+
                      \
                       \     +---------+      +---------+
                        ---> |  obj 0  |  ... | obj N-1 |
                             +---------+      +---------+

```
With dimensions of Y and N, one can define a two-dimensional array:
```

const int Y = 5;
const int N = 3;

XY_Coord** ptr = malloc(Y * sizeof(XY_Coord*));  // here we allocate the pointers for each row of XY_Coord object(s).

for (int y = 0; y < Y; ++y)
{
   ptr[y] = malloc(N * sizeof(XY_Coord));   // here we allocate the columns for each row.
}

```

Now to confuse you a bit... sometimes it is necessary to pass a pointer to a function by "reference", which in C this implies something like:
```

void allocSpace(XY_Coord** p, const int n)
{
   *p = malloc(n * sizeof(XY_Coord));
}

...

const int N = 3;
XY_Coord* ptr = NULL;  // note the single pointer here!

allocSpace(&ptr, N);   // pass the address of the pointer

...

```
In the code above, the *address* of the ptr variable is being passed to a function.  The receiving function will need to dereference the pointer when it assigns a value (ie an address) to that pointer.

In reference to the previous example where the "pointer(s) to pointer(s)" concept was discussed, the variable p within allocSpace() is treated as if it were a two-dimensional array, with Y = 1.  So, technically, the following is also correct:
```

void allocSpace(XY_Coord** p, const int n)
{
   p[0] = malloc(n * sizeof(XY_Coord));
}

```
Anyhow, I hope that all of this helps.  Wiki probably has better graphics, and undoubtedly better explanations.

---

### Post by worksofcraft on 2010-10-02
> **nvteighen said:**
> Yeah, but stating that C is "obsolete" when it is widely used in programming is also childish. I do agree with your complaints about C, but please, realize that C isn't obsolete at all... BCPL, COBOL, FORTRAN77, Simula, etc. may be, but not C.

From the point of carrying on a diverging development of the C language standard that fosters inconsistency with using a C++ compiler to compile C code, said activity is not only obsolete but down right pigheaded, pointless and counter productive.

A typical example we can see here with the unnecessary confusion between typedef and struct name. :-({|=

---

### Post by worksofcraft on 2010-10-02
Yes anyway back to the topic.

> **erupter said:**
> ...
So had my program to pass hundreds of values it would have to pass the entire hundreds of structures. Clearli defeating the principle of deferencing.
So i needed pointers.

dwhitney67 gave a very good explanation, but just in case you are still wondering:

Yes, it would make an array of many coordinate pairs, however when you call a function passing an array as a parameter it does **NOT** copy that whole array.

In C, arrays do not get passed around *by value*. An array name is simply synonymous with the **address of the first element** of said array: i.e. just a pointer. On 32 bit system is 4 byte entity and on a 64 bit system it is 8 bytes that get passed to the function.

Thus passing an array of hundreds of values is just as efficient as passing an array of one value. It is in many cases more efficient than passing a single coordinate pair by value.

C syntax lets you index off that pointer just as if you were indexing into an array because all it has to do to find the entry you want is to add an offset to the array start address to give the address of the entry you want.

---

### Post by erupter on 2010-10-03
> **worksofcraft said:**
> A typical example we can see here with the unnecessary confusion between typedef and struct name. :-({|=

Can you elaborate a bit on this?
This is the only way i know of doing it: creating a custom type.

---

### Post by nvteighen on 2010-10-03
> **slavik said:**
> I disagree with FORTRAN being obsolete. :P

FORTRAN is still heavily used for scientific (distributed) purposes.

But FORTRAN77? But it's ok, I didn't know that a FORTRAN of any kind was still in use.

> **worksofcraft said:**
> From the point of carrying on a diverging development of the C language standard that fosters inconsistency with using a C++ compiler to compile C code, said activity is not only obsolete but down right pigheaded, pointless and counter productive.


No, because C++ and C are different languages and C++ is **not** defined formally as a superset of C. The C++ Standard replicates a lot from the C Standard because of that. On the contrary, Objective-C is formally declared as a superset of C, therefore it's specs (there's no ISO Standard... yet...) assume the C Standard... and it's compatible with C99 too.

---

### Post by worksofcraft on 2010-10-03
> **erupter said:**
> Can you elaborate a bit on this?
This is the only way i know of doing it: creating a custom type.

in message 7 of this thread you write:
```

typedef struct **XY_Coord** {
  float px;
  float py;
} **XY_Coord**;

```

notice you give the same name **XY_Coord** twice... effectively there are two different concepts in C here and people also often have problems trying to get it to store a pointer to another one of these structs inside said struct.

If you were to use the C++ compiler you could write:
```

struct XY_Coord {
  float px;
  float py;
};

```
XY_Coord then becomes synonymous with a type of that name and there would be no problem writing...
```

struct XY_Coord {
  float px;
  float py;
  XY_Coord *next; // to make a linked list
};

```

So well basically I find the C syntax obscure and unproductive... one of the many reasons I avoid the C compiler even when writing simple procedural C code.

---

### Post by slavik on 2010-10-03
> **worksofcraft said:**
> in message 7 of this thread you write:
```

typedef struct **XY_Coord** {
  float px;
  float py;
} **XY_Coord**;

```

notice you give the same name **XY_Coord** twice... effectively there are two different concepts in C here and people also often have problems trying to get it to store a pointer to another one of these structs inside said struct.

If you were to use the C++ compiler you could write:
```

struct XY_Coord {
  float px;
  float py;
};

```
XY_Coord then becomes synonymous with a type of that name and there would be no problem writing...
```

struct XY_Coord {
  float px;
  float py;
  XY_Coord *next; // to make a linked list
};

```

So well basically I find the C syntax obscure and unproductive... one of the many reasons I avoid the C compiler even when writing simple procedural C code.
the reason C++ acts in that way is that it automatically typedefs the label to the type ... this is the same as being able to refer to 'class Blah' simply by 'Blah'.

C structures and C++ structures are not the same.

C structures cannot have functions (you can have void pointers to functions).

In C++ structures, all functions/members are public by default (to have backwards compatibility with), while in a class, everything is private by default.

You can use the C convention of prepending an underscore to the label which means it should not be used by other code.

```

typedef struct _MyStruct {
  int item;
  struct _MyStruct *next;
} MyStruct;

```

What you also refer to is something that PL/I can do, the following would not be a problem for PL/I.
```

typedef struct _MyStruct {
  int item;
  MyStruct *next;
} MyStruct;

```

But in C, you have to remember that until 'MyStruct;' is parsed and lexed, the compiler has not idea what 'MyStruct' really means.

---

### Post by trent.josephsen on 2010-10-03
What I don't understand is why you would want to typedef a struct in the first place.  If you write
```
struct Item {
    int value;
};
```
then just use 'struct Item'.  Hiding the word 'struct' behind a typedef is detrimental to clarity.  (That's not to say there is never a good reason to typedef a struct, but "to avoid typing the word 'struct'" is not a good reason.)

---

### Post by dwhitney67 on 2010-10-03
worksofcraft

If I had to describe you in one word... it would be: [malcontent]("http://www.thefreedictionary.com/malcontent").

Rather than whine about what is, why not put thy foot forth to come up with a better solution.

---

### Post by worksofcraft on 2010-10-04
> **dwhitney67 said:**
> worksofcraft

If I had to describe you in one word... it would be: [malcontent]("http://www.thefreedictionary.com/malcontent").

Rather than whine about what is, why not put thy foot forth to come up with a better solution.

Rather than make adhominem and inappropriate personal assessments I suggest you use this forum for "programming talk". If you care to take notice the OP of this thread asked me for clarification and so I gave it.

---

### Post by dwhitney67 on 2010-10-04
> **worksofcraft said:**
> 
So well basically I find the C syntax obscure and unproductive... one of the many reasons I avoid the C compiler even when writing simple procedural C code.

The statement above has nothing to do with clarification; it is merely a personal judgment.

The fact that C++ offers certain capabilities over that of C is of no surprise.  It was developed later... much later.  The C language, however obsolete it may seem to you, is still widely used and practiced.

Rather than complain about it shortcomings, just accept it for what it is, and deal with it.

P.S.  My "name calling" was not so much in reference to your posts on this thread; it is a general statement based on your other posts.  You're new to the programming forum... or so it seems.  But every time you post something, it seems to have tinge of negativity.  Hence the adjective that I used to describe you is appropriate.  My apologies if you feel offended, but I tend to call things as I see it.  Maybe that's my shortcoming; I'm blunt and to-the-point type of person.

---

### Post by worksofcraft on 2010-10-04
> **dwhitney67 said:**
> The statement above has nothing to do with clarification; it is merely a personal judgment.

Why don't you read what the thread is about. You will see that it is about the syntax of structures in C and you can explain it what ever way you like but I think my explanation was just fine and if yo don't like it you don't have to read it :P

---

### Post by worseisworser on 2010-10-04
No one cares, worksofcraft; it's C, and *both* C and C++ are obsolete to begin with anyway.

Now behold; the exploding whale gut disaster that is C++0x: 
[http://www.msnbc.msn.com/id/4096586/](http://www.msnbc.msn.com/id/4096586/)

*(incf *flame-war* 9001)*

edit:
Perhaps you should "switch sides" and argue from that *other* tower of yours again now worksofcraft, because, you know, C++0x now here in 2010 finally has lambdas; something which several "obsolete" languages has had for decades. I.e., what does it mean to be obsolete?

---

### Post by cariboo on 2010-10-05
This thread doesn't seem to be going anywhere near a solution
It may be best to start all over again.

This thread is closed.

---

