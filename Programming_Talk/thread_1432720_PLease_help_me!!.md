---
title: "PLease help me!!"
date: 2010-03-18
forum: Programming Talk
---

### Post by Meghkabbo on 2010-03-18
(As I am new to ubuntu as well as new to this forum i posted this thread in another place and someone told me to post it here to get better responses...please help me...)

I have a lot of curiosity for ubuntu and thats why I have been using  using Ubuntu beside windows to learn and explore and now I decided to  shift completely to Ubuntu from Windows but the fact is gcc or tcc could  not execute all kind of program like pointers correctly in my  ubuntu.(shows some error which is generally not shown in window's ide..)

Now my problem is I have written a program which is given below and it  is compiled successfully  but gives an odd output which were not given  in dev c++ in windows:[SIZE=3]


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

there should be 9 input by rules but it generate output automatically  when the 6 input is been given and creates the following output.

Is there anybody who can help me out.....I am also new in this forum...I  want to learn something with you.


Regards,
Irfan Ahmed
University of Liberal Arts Bangladesh
Computer Science and Engineering

---

### Post by Some Penguin on 2010-03-18
[http://ubuntuforums.org/showthread.php?t=1431737](http://ubuntuforums.org/showthread.php?t=1431737)
Duplicate thread.

---

### Post by Elfy on 2010-03-18
closed - please see duplicate

---

