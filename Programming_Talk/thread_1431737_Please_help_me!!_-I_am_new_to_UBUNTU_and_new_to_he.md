---
title: "Please help me!! -I am new to UBUNTU and new to here.."
date: 2010-03-17
forum: Programming Talk
---

### Post by Meghkabbo on 2010-03-17
I have a lot of curiosity for ubuntu and thats why I have been using using Ubuntu beside windows to learn and explore and now I decided to shift completely to Ubuntu from Windows but the fact is gcc or tcc could not execute all kind of program like pointers correctly in my ubuntu.(shows some error which is generally not shown in window's ide..)

Now my problem is I have written a program which is given below and it is compiled successfully  but gives an odd output which were not given in dev c++ in windows:[SIZE=3]


#include<stdio.h>


main( )
{
    struct book
    {
         char name ;
         float price ;
         int pages ;
    };
    struct book b1, b2, b3 ;
    printf ( "\nEnter names, prices & no. of pages of 3 books\n" ) ;
    scanf ( "%c %f %d", &b1.name, &b1.price, &b1.pages ) ;
    scanf ( "%c %f %d", &b2.name, &b2.price, &b2.pages ) ;
    scanf ( "%c %f %d", &b3.name, &b3.price, &b3.pages ) ;
    printf ( "\nAnd this is what you entered" ) ;
    printf ( "\n%c %2f %d", b1.name, b1.price, b1.pages ) ;
    printf ( "\n%c %2f %d", b2.name, b2.price, b2.pages ) ;
    printf ( "\n%c %2f %d", b3.name, b3.price, b3.pages ) ;
}

*"*[SIZE=2]and the out put(with command):
irfan@irfan-laptop:~$ cd Desktop/
irfan@irfan-laptop:~/Desktop$ cd Rough/
irfan@irfan-laptop:~/Desktop/Rough$ gcc struct1.c
irfan@irfan-laptop:~/Desktop/Rough$ cc -o struct1 struct1.c
irfan@irfan-laptop:~/Desktop/Rough$ ./struct1

Enter names, prices & no. of pages of 3 books
f 34 67
e 56 78

And this is what you entered
f 34.000000 67

 -1.788583 9749317
e 56.000000 78irfan@irfan-[/SIZE][/SIZE]      "

there should be 9 input by rules but it generate output automatically when the 6 input is been given and creates the following output.

Is there anybody who can help me out.....I am also new in this forum...I want to learn something with you.


Regards,
Irfan Ahmed
University of Liberal Arts Bangladesh
Computer Science and Engineering

---

### Post by phrostbyte on 2010-03-17
I am not sure how your code even compiles.

Please use the following method signatures:

int main()

As opposed to

main()

Also, please use only one input argument per scanf. The way you are using scanf is uncommon and may even be incorrect.

---

### Post by Meghkabbo on 2010-03-17
nop, still it is not working.............

---

### Post by VernonA on 2010-03-17
Part of the problem is that you are not initialising the book variables, so when you print out the values in b3 you are getting random bytes from the memory. You should look at the return value from the scan to see how many args were converted successfully, and only print the ones which were done OK. If you actually type in nine good values does the program work as expected? When you type in the empty line as input to that last scan, what were you hoping was going to happen? Did you expect the values would all be set to 0? C library functions just don't work like that!

---

### Post by derrick81787 on 2010-03-17
This should probably go in the "Programming Talk" section of the forums.  You'd probably get a better response there.

Maybe a mod can move this?

- Derrick

---

### Post by lisati on 2010-03-18
Another observation: that looks more like C than C++ to me.....

---

### Post by Some Penguin on 2010-03-18
Major:
Take a look at the output.  You presumably expect three lines in a row.  Ask yourself why there is a blank one.

Read the man page for scanf, very very carefully.  Consider what happens to the newline character.    Understand this and you shouldn't have a problem fixing the program.


Minor nits:
It is a bit unconventional to define a struct type inside a function.
Also, if you're using C++, you might want to look at the iostream stuff instead.

---

### Post by ApEkV2 on 2010-03-18
@ op, plz use code tags

EDIT: you should be using cout and cin

---

### Post by Meghkabbo on 2010-03-18
I got solution yaaaaaaaaaaaaaaaaaaaaaaaaa

---

### Post by roccivic on 2010-03-18
Then mark it as [SOLVED]

---

### Post by Meghkabbo on 2010-03-18
Solution: I didnt scan the input correctly and SOLUTION is in creating new line: here is the corrected form: #include<stdio.h>


int main( )
{
    struct book
    {
         char name ;
         float price ;
         int pages ;
    };
    struct book b1, b2, b3 ;
    printf ( "\nEnter names, prices & no. of pages of 3 books\n" ) ;
    scanf ( "%c\n", &b1.name) ;
    scanf ( "%f\n", &b1.price) ;
    scanf ( "%d\n", &b1.pages) ;
    scanf ( "%c\n", &b2.name) ;
    scanf ( "%f\n", &b2.price) ;
    scanf ( "%d\n",&b2.pages ) ;
    scanf ( "%c\n", &b3.name);
    scanf ( "%f\n",&b3.price);
    scanf ( "%d",&b3.pages );
    printf ( "\nAnd this is what you entered" ) ;
    printf ( "%c %2f %d\n", b1.name, b1.price, b1.pages ) ;
    printf ( "%c %2f %d\n", b2.name, b2.price, b2.pages ) ;
    printf ( "%c %2f %d", b3.name, b3.price, b3.pages ) ;
}



Marking as a solved.............Done.

---

### Post by schauerlich on 2010-03-18
As has already been stated, if this is C++, you should be using classes and iostream, not structs and stdio.h.

---

### Post by ApEkV2 on 2010-03-18
> **schauerlich said:**
> As has already been stated, if this is C++, you should be using classes and iostream, not structs and stdio.h.

...and code tags

---

### Post by soltanis on 2010-03-18
Enclose your code in [code] tags please. There's a button (the # sign) in the editor for it. It formats it with a monospace font and preserves indentation so that we're happier reading your code.

You are using some kind of weird mix of C/C++ there. While it may compile, I strongly urge you to pick one language and stick it it, because while they are related (and while you can use some C features in C++) C++ has for the most part replaced almost all of C's semantics with other constructs.

---

