---
title: "Loop in C"
date: 2013-10-04
forum: Programming Talk
---

### Post by Timmoore001 on 2013-10-04
I'm trying to get a Do Loop to work but get the error message:-

tim@tim-A880G:~$ g++ -o Bob19 Bob19.c
Bob19.c: In function &#8216;int main()&#8217;:
Bob19.c:26:27: error: expected &#8216;)&#8217; before &#8216;;&#8217; token
tim@tim-A880G:~$ 

part of the code is:-

#include <stdio.h>

int main()
{
 float num1, num2, result;
 char choice;

 
 do {

etc....

Total beginner so no idea why it complains

I invoke it with:-

g++ -o Bob19 Bob19.c


at the bash prompt.

Any thoughts very welcome !

A puzzled,

Tim

---

### Post by Vaphell on 2013-10-04
It looks like C and you should compile it with gcc not g++ which is for C++ 
you have a syntax error there, and as the error says in the 26th line you have some ')' missing

it would be nice to see the code near the 26th line, otherwise you won't get a better answer

---

### Post by Timmoore001 on 2013-10-04
Many many thanks.

I use G++ because GCC gave error messages even for Hello World but G++ worked.

I will try again to use GCC. (update :-  it worked using gcc so that is a bit plus !)

I got it to work with this code:-

#include <stdio.h>
 main()
{
 float num1, num2, result;
 char choice;
 
 do {   
      printf(" Number 1 ");
      scanf(" %f", &num1);
      printf(" Number 2 ");
      scanf(" %f", &num2);
         
      result=num1+num2;
      printf ("Answer \n \n", result) ;   
    scanf(" %c", &choice);
     if (choice == 'n') ;
     {
       choice = 'N';
     }
    } while (choice != 'N');
    printf("%.2f\n\n",result);  
    printf("Hello world - bob22 ! \n");
    return 0;
  
}
_____________

I had left the ' ) ' of the 'while'  line !

It is very very early days in my attempt to use 'C', so your help was especially appreciated.   I know the code is terrible but it compiled and ran OK and for me a massive step forward !

So thank you again !

Tim

---

### Post by ofnuts on 2013-10-04
> **Timmoore001 said:**
> Many many thanks.

I use G++ because GCC gave error messages even for Hello World but G++ worked.

I will try again to use GCC. (update :-  it worked using gcc so that is a bit plus !)


Some or the more "modern" elements of C syntax ("//"" comments, loop variable declaration in the lop condition, etc...) have been borrowed from C+, so G++, that assumes a C++ syntax, will consider them OK (but will also imply C++ semantics, that can be different), while GCC which uses a rather old standard by default will complain about much modernities. The real solution is to tell GCC to use a more recent standard (-std=c99 option).

---

