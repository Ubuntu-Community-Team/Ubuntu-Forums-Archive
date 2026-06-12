---
title: "Statement questions"
date: 2010-12-01
forum: Programming Talk
---

### Post by newport_j on 2010-12-01
I found a statement in some legacy code that I am using that is confusing. None of my hardcore programming colleagues seem to have a satisfactory answer either and I have asked.
 
The statement is:
 
 
 
typedef enum logical {false,true} LOGICAL;
 
 
 
Now this is c code and it compiles with a c compiler, but does not with a c++ compiler - clearly because it is redefing true and false which are reserved words in c++.
 
My question is what are the two Logicals for? I know that you need one, but why two?
 
It seems that this stement would suffice:
 
 
 
typedef enum {false,true} logical;
 
 
 
I have seen similar statements on various programming forums so I believe it would work. I have no solid proof that the immediate above statement works, except its presence on variuos forums. 
 
Question:
 
What is the difference between the leftmost and rightmost Logicals in the statement - now repeated:
 
 
 
typedef enum logical {false,true} LOGICAL;
 
 
 
As I said one of the logicals seems uneeded. 
 
It seems one is the name of the redefined variable set (and can be anything the programmer chooses) and the other is the type. Is it not dangerous to use the same word in both cases - albeit on is in caps and one is in small letters? 
 
Any help appreciated.
 
 
Respectfully,
 
Newport_j

---

### Post by Zugzwang on 2010-12-01
Basically, "typedef enum logical {false,true} LOGICAL;" is two lines in one, namely "enum logical {false,true};" and "typedef enum logical LOGICAL;"

See for example the example [here]("http://home.fhtw-berlin.de/~junghans/cref/EXAMPLES/enum1.c"). In order to use an enum in your code, your need to prefix all variable declarations by the keyword "enum" - using a typedef, you can avoid this. The example line you had both declares a name for the type where you have to use "enum" in front of every declarations as well as for a type where you don't have to do that.

---

### Post by talonmies on 2010-12-01
> **newport_j said:**
> 
Now this is c code and it compiles with a c compiler, but does not with a c++ compiler - clearly because it is redefing true and false which are reserved words in c++. 
You're welcome.
 
> My question is what are the two Logicals for? I know that you need one, but why two?

There is an "enum logical" which is declaring a named enumeration, and a "typedef enum logical Logical" which is declaring a type from that named enumeration (in C and C++ type names are effectively aliases). The two statements have been combined. The original author of the code could equally have written:

```

enum logical { false, true };
typedef enum logical LOGICAL;
```

which does the same thing, but using two lines of code instead of one. You could also directly declare a type from an unnamed enumeration.

---

### Post by newport_j on 2010-12-01
Okay, but which is which? I am assuming that the last logical is a name and the first is a typedef. The code that I referred to in the previous statement as found in another forum is:
 
 
 
typedef enum {false,true} bool;
 
 
 
Which has only a word, bool, following the right bracket and is a simlar stament to mine. Is bool a name or typedef?
 
Also, how do they get away with the statment:
 
 
 
typedef enum 
 
 
 
Should there not be some a third modifier here?
 
Basically this legacy code is being ported to a c++ compiler. I thus want to define myown true, false in the c code. I clearly cannot use c++'s reserved true, false.
 
By that I would have new values betrue, and befalse representing true and false respectiveley.
 
From there I would have to go into the c source and change every use of true and false to betrue and befalse. 
 
Then I would comment out the current statement, and put in this one:
 
 
 
typedef enum {befalse = 0, betrue =1} LOGICAL;
 
 
 
Would that do it?
 
 
 
Newport_j

---

### Post by talonmies on 2010-12-01
> **newport_j said:**
> 
Then I would comment out the current statement, and put in this one:
 
 
 
typedef enum {befalse = 0, betrue =1} LOGICAL;

That is a really poor idea. You would be much better doing something like this:

```

#ifdef __cplusplus
typedef bool LOGICAL;
#else
typedef enum logical { true, false } LOGICAL;
#endif

```which would define the type depending on which language you are compiling with and not require you to edit all the remaining source.

---

### Post by talonmies on 2010-12-01
> **newport_j said:**
> Okay, but which is which? I am assuming that the last logical is a name and the first is a typedef. j

As was already explained (twice), [FONT=Fixedsys]LOGICAL[/FONT] is a typename and [FONT=Fixedsys]enum logical[/FONT] is an enumeration.

---

### Post by Zugzwang on 2010-12-01
> **newport_j said:**
> Okay, but which is which? I am assuming that the last logical is a name and the first is a typedef. The code that I referred to in the previous statement as found in another forum is:
 

The last LOGICAL is the name of the new type whereas the first one is the name of the enumeration.

BTW: Why can't you simply do a
```

typdef bool LOGICAL;

```

wouldn't that solve your problem? Then, true and false can be used as usual.

---

### Post by dwhitney67 on 2010-12-01
> **Zugzwang said:**
> The last LOGICAL is the name of the new type whereas the first one is the name of the enumeration.

BTW: Why can't you simply do a
```

typdef bool LOGICAL;

```

wouldn't that solve your problem? Then, true and false can be used as usual.

I would assume, from this statement, "I found a statement in some legacy code...", that the bool type was not available in the past.  I used to program exclusively in C back in the old days (1987-1999), and I do not recall ever seeing a bool type until I started with C++.

Nowadays, of course, one can include stdbool.h.

---

### Post by newport_j on 2010-12-02
No, no. I googled my error and found that someone had put a problem similar to mine. Their c code was porting to a c++ compiler and they had to make some rewrites, which is what I had to do. The "found" code was c and it was going to be compiled on c++. It was suggexted by who I do not know to use bool. 
 
Newport_j

---

### Post by newport_j on 2010-12-02
What C++ header file defines bool?
 
Newport_j

---

### Post by newport_j on 2010-12-02
Could bool.h be the header file that defines bool. It can not be as simple as that. 
 
Newport_j

---

### Post by talonmies on 2010-12-02
> **newport_j said:**
> What C++ header file defines bool?

It isn't defined in a header, bool is fundamental type which is "built-in" into C++ in the same way that int, float double and char are.

---

### Post by TennTux on 2010-12-02
Perhaps another example will clarify one of the points being discussed here.

```
// We need an enum to keep track of seasons
enum season {spring, summer, fall, winter} ;

// Now lets use it
enum season current_season = winter ;

if (season == summer)
    printf("Enjoy it while you can.") ;
```

The problem here is that everytime we want to declare a variable of type "season" we need to use "enum season". However, we can change that with the following code.

```
 // We need an enum to keep track of seasons
enum season {spring, summer, fall, winter} ;

typedef enum season TIME_OF_YEAR ;

// Now lets use it
TIME_OF_YEAR current_season = winter ;

if (season == summer)
    printf("Enjoy it while you can.") ;
```
By using the typedef we no longer need the enum before season when we use TIME_OF_YEAR.

I believe this is the point that talonmies was making in the 3rd post.

As for the point about bool, true and false that dwhitney67 was making in post #8. In the old days there was no true, false and bool. It was not until C++ added them to the language [and every programmer ;) rejoyced] that C wanted to follow suit and created stdbool.h.

In the old days there was a header file (I don't remember which) that had the equivalent of the following two lines.
```
#define FALSE 0
#define TRUE (!FALSE)
```
So you could use a char or int to hold a Boolean value but there was no real type.

I hope this clarifys some of the discussion.

---

### Post by saulgoode on 2010-12-02
> **TennTux said:**
> ```
// We need an enum to keep track of seasons
enum season {spring, summer, fall, winter} ;

// Now lets use it
enum season current_season = winter ;

if (season == summer)
    printf("Enjoy it while you can.") ;
```
The test should be '***if (current_season == summer)***' (otherwise you would be comparing a variable's value to a tag).

---

