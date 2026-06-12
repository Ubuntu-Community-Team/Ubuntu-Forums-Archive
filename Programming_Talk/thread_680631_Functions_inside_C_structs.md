---
title: "Functions inside C structs"
date: 2008-01-28
forum: Programming Talk
---

### Post by xlinuks on 2008-01-28
Hi,
I'm learning C, for short my question would be "(how) can I include/tighten functions into structs?".
While learning and looking for this info in other books I couldn't find a way to write "objects with functions" that could be accessed like "myVector.add( param )", instead of "vector_add( &vector, param )".
Here's a snippet:

```

#include <stdio.h>
#include "BytesVector.h"

void init( BytesVector *vector ) {
	vector->iCurrentIndex = 0;
	vector->iCount = 0;
}

//HERE CAN I AVOID PASSING EACH TIME THE POINTER?
void add( BytesVector *vector, char text[] ) {
	//do stuff
}

//HERE SAME ISSUE
void setCurrentIndex( BytesVector *vector, int *iIndex ) {
	vector->iCurrentIndex = *iIndex;
}

```

I know in C++ one can write like this:
```

void BytesVector::add( char text[] ) {
	//do stuff
}

```
but in C you can't, is that correct..(?)

---

### Post by LaRoza on 2008-01-28
In C, structs can't contain functions.

They can, however, hold function pointers.

---

### Post by CptPicard on 2008-01-28
Why not use C++ if this is what you're after? :)

---

### Post by LaRoza on 2008-01-28
> **CptPicard said:**
> Why not use C++ if this is what you're after? :)

"Learning C" and still getting used to it.

---

### Post by xlinuks on 2008-01-28
> **CptPicard said:**
> Why not use C++ if this is what you're after? :)
That's a good question, I created a "hello world" in C and C++. By default In C it was about 8KB, in C++ about 200KB, that scared me..
Since I'm coming from Java I would welcome the functionality of C++, but there's another issue: on Linux most applications (and even the kernel AFAIK) are written in C..
If I find a way to create programs as small as those created in C I would certainly switch to it ( I guess ).

Thanks both, I will try implementing "pointers inside structs"..

---

### Post by CptPicard on 2008-01-28
The C++ standard library does pull in a lot of stuff into your binary, but do remember that the more own code you write, the less, in percentage terms, that library code becomes. "Hello World" is the extreme example.

Also, the difference is completely meaningless on modern computers. You aren't coding for a pocket calculator.

Another way to view this: your 200k Hello World is certainly much smaller than anything you had with Java ;)

---

### Post by revanthedarth on 2008-01-28
Java is alot like C++, as you said. Most apps are written in C, but C++ programmers *can* use C too.

And, if you try that pointers inside structs approach, you'll waste 4 bytes for every member of that struct.

Anyway, i'll give an example for C and C++ way:

```

struct A
{
	int x;
};
void resetA(struct A *arg)
{
	arg->x = 0;
}

```

And, C++ way:
```

class A
{
private:
	int x;
public:
	reset()
	{
		x = 0;
	}
}

```

I find C++ way simpler and better. And, using features of C++ is no harm, you'll get used to C too.

---

### Post by xlinuks on 2008-01-28
> **CptPicard said:**
> The C++ standard library does pull in a lot of stuff into your binary, but do remember that the more own code you write, the less, in percentage terms, that library code becomes. "Hello World" is the extreme example.

Also, the difference is completely meaningless on modern computers. You aren't coding for a pocket calculator.

Another way to view this: your 200k Hello World is certainly much smaller than anything you had with Java ;)

Actually a Java "hello world" is 415 bytes, thus a lot smaller, if I make it an executable .jar file it will still be around 1KB. I almost created a file manager in Java and the executable with all the code in it was (and is) about 150KB (without such resources as icons), the executables in Java are so small mostly because they are mainly "text files with little binaries altogether compressed using the "zip" utility and named with a .jar extension". The actual pain # 1 in Java (for me) is the Java startup time (especially the cold startup). That's the main reason why I decided to learn and rewrite the file manager in a native language.

I completely agree with you about code size, however I'm planning to make it available for download from the internet so the less people will have to download the better ( I guess ).

---

### Post by LaRoza on 2008-01-28
> **xlinuks said:**
> Actually a Java "hello world" is 415 bytes, thus a lot smaller, if I make it an executable .jar file it will still be around 1KB. I almost created a file manager in Java and the executable with all the code in it was (and is) about 150KB (without such resources as icons), the executables in Java are so small mostly because they are mainly "text files with little binaries altogether compressed using the "zip" utility and named with a .jar extension". The actual pain # 1 in Java (for me) is the Java startup time (especially the cold startup). That's the main reason why I decided to learn and rewrite the file manager in a native language.

I completely agree with you about code size, however I'm planning to make it available for download from the internet so the less people will have to download the better ( I guess ).

Java also runs a VM....a lot more memory (not that it makes a difference)

---

### Post by xlinuks on 2008-01-28
Yes, Java runs a VM, that is # 2 pain for me, because:
1) It eats up (much) more memory than a C/C++ app (yes, I did a comparison)
2) The VM uses extra resources, especially while system iddle, thus its always eating more CPU than your app normally does.
3) I call it "the wave effect". The difference in speed while executing same block of code before and after the VM (the Hotspot VM in my case) internally compiles the code.

Thus I guess it actually makes a difference.. It might not make such a difference on the server side since the apps is only once started and runs for long days/months running basically same blocks of code..

---

### Post by CptPicard on 2008-01-28
Yes exactly... the C++ stdlib is statically compiled in so you can take your binary anywhere, but with your 450k Java HelloWorld you need to install a humongous JVM+library :)

---

### Post by LaRoza on 2008-01-28
> **CptPicard said:**
> Yes exactly... the C++ stdlib is statically compiled in so you can take your binary anywhere, but with your 450k Java HelloWorld you need to install a humongous JVM+library :)

On the other hand, you can only take that C++ compiled app to the same platform, the Java one can (usually) be used on many platforms.

---

### Post by xlinuks on 2008-01-28
450 bytes (not kilobytes).
Yes, requiring the user to have installed the latest Java Runtime version from Sun is another pain..
The libraries come preinstalled with the the Java Runtime (for short "JRE" or just "Java").

PS: the app I will create will be for Linux only (Windows has a file manager I'm satisfied with), so portability to windows is not on my todo list (although portability is always welcome).

---

### Post by eye208 on 2008-01-28
> **xlinuks said:**
> That's a good question, I created a "hello world" in C and C++. By default In C it was about 8KB, in C++ about 200KB, that scared me..
That's scary indeed!
```
$ cat hello.cpp
#include <iostream>

using namespace std;

int main()
{
        cout << "Hello World!" << endl;
        return 0;
}
$ g++ -s -ohello hello.cpp
$ du -b hello
4196    hello
$ ./hello
Hello World!
$
```
You probably made a mistake at the linking stage. Even if you don't strip the debug symbols, the result should be about the same size as the C version.

---

### Post by xlinuks on 2008-01-28
Wow! I don't remember what exactly I did, but your example really compiles into a small executable, thanks!

---

### Post by LaRoza on 2008-01-28
> **CptPicard said:**
> Yes exactly... the C++ stdlib is statically compiled in so you can take your binary anywhere, but with your 450k Java HelloWorld you need to install a humongous JVM+library :)

You have an evil number of posts....

---

### Post by Jessehk on 2008-01-28
In regards to the original post, you could do something like this with function pointers. I think it would be pointless though, because you'd still have to pass in a *this* argument and things get redundant.

```

#include <stdio.h>
#include <stdlib.h>

typedef struct ball {
    int radius;
    
    void (*throw)( struct ball * );
} ball;

void ball_throw( ball *b ) {
    printf( "You've thrown the ball with radius %d.\n", b->radius );
}

ball *new_ball( int radius ) {
    ball *b = malloc( sizeof *b );
    
    if ( b == NULL ) {
        fprintf( stderr, "Unable to allocate memory." );
        exit( EXIT_FAILURE );
    }
    
    b->radius = radius;
    b->throw = ball_throw;
    
    return b;
}

int main( void ) {
    ball *b = new_ball( 3 );
    b->throw( b );
    
    free( b );
    return 0;
}

```

The best solution in my opinion is to just write free functions that accept a *this* parameter.

---

### Post by LaRoza on 2008-01-28
> **Jessehk said:**
> In regards to the original post, you could do something like this with function pointers. I think it would be pointless though, because you'd still have to pass in a *this* argument and things get redundant.


Yes, in this case, using function pointers isn't the best thing. I just wanted to clarify what was allowed and not allowed in C structs.

---

### Post by pmasiar on 2008-01-28
You may be interested in checking [this post from "Hidden gems"](http://ubuntuforums.org/showpost.php?p=4219780&postcount=15) which explains how to implement "object-oriented class" design pattern in C.

---

### Post by Wybiral on 2008-01-28
> **Jessehk said:**
> In regards to the original post, you could do something like this with function pointers. I think it would be pointless though, because you'd still have to pass in a *this* argument and things get redundant.

Actually... You can always JIT compile the function calls as a partial function (with the pointer passed first). :) In fact, since I already have a bunch of JIT routines lying around, I whipped up an example. My "partial" function generates the machine code required to build the argument stack (with the pointer), copy the arguments being passed to the partial function, then call and return. The only catch is that it REQUIRES an intel ix86 machine (and maybe GCC, I haven't invested too much research into how other compilers handle function calls).

PS: This is for fun only, not for serious use. It does work, if you have an intel machine, but it would probably be a nightmare to port to any other system. It does make for some interesting looking C code, but it's basically syntactic sugar.

---

### Post by xlinuks on 2008-01-29
Thanks to everybody posting here, after I found out that C++ produces code of practically same size as C does - I went the C++ way, and so far I like it a lot!

---

### Post by myhieu on 2011-03-14
> **Jessehk said:**
> In regards to the original post, you could do something like this with function pointers. I think it would be pointless though, because you'd still have to pass in a *this* argument and things get redundant.

```

#include <stdio.h>
#include <stdlib.h>

typedef struct ball {
    int radius;
    
    void (*throw)( struct ball * );
} ball;

void ball_throw( ball *b ) {
    printf( "You've thrown the ball with radius %d.\n", b->radius );
}

ball *new_ball( int radius ) {
    ball *b = malloc( sizeof *b );
    
    if ( b == NULL ) {
        fprintf( stderr, "Unable to allocate memory." );
        exit( EXIT_FAILURE );
    }
    
    b->radius = radius;
    b->throw = ball_throw;
    
    return b;
}

int main( void ) {
    ball *b = new_ball( 3 );
    b->throw( b );
    
    free( b );
    return 0;
}

```

The best solution in my opinion is to just write free functions that accept a *this* parameter.

If in ball_throw function, I want to create new ball (then call new_ball(3)), It'll throw a error like "new_ball isn't declared before", any help for this?

---

### Post by Arndt on 2011-03-14
> **myhieu said:**
> If in ball_throw function, I want to create new ball (then call new_ball(3)), It'll throw a error like "new_ball isn't declared before", any help for this?

Maybe it's best to ask the question in a new thread, since the one you're using is three years old. On the other hand, you're asking about the precise code that's there, so I don't know what's best.

The reason for the compiler error (one usually doesn't say "it'll throw an error" about the compiler) is that functions need to be declared before they are used. In your code, new_ball and ball_throw use each other, which is fine, but it means that one of them has to be given an extra declaration before both of them. For example like this:

```
ball *new_ball( int radius );

void ball_throw( ball *b ) {
    printf( "You've thrown the ball with radius %d.\n", b->radius );
    ... call new_ball in some way ...
}

ball *new_ball( int radius ) {
...

```

---

### Post by myhieu on 2011-03-14
> **Arndt said:**
> Maybe it's best to ask the question in a new thread, since the one you're using is three years old. On the other hand, you're asking about the precise code that's there, so I don't know what's best.

The reason for the compiler error (one usually doesn't say "it'll throw an error" about the compiler) is that functions need to be declared before they are used. In your code, new_ball and ball_throw use each other, which is fine, but it means that one of them has to be given an extra declaration before both of them. For example like this:

```
ball *new_ball( int radius );

void ball_throw( ball *b ) {
    printf( "You've thrown the ball with radius %d.\n", b->radius );
    ... call new_ball in some way ...
}

ball *new_ball( int radius ) {
...

```


Thank you, it helps me a lot :D

---

