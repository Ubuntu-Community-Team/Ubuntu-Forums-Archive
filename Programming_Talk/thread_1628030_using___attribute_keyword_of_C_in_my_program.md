---
title: "using __attribute keyword of C in my program"
date: 2010-11-22
forum: Programming Talk
---

### Post by jamesbon on 2010-11-22
I am trying to understand usage of keyword __attribute in C 
I have checked following two pages
[http://unixwiz.net/techtips/gnu-c-attributes.html](http://unixwiz.net/techtips/gnu-c-attributes.html)
and this page also 
[http://gcc.gnu.org/onlinedocs/gcc-4.0.0/gcc/Function-Attributes.html](http://gcc.gnu.org/onlinedocs/gcc-4.0.0/gcc/Function-Attributes.html)
but still I could not understand where do I declare them and how I can use __attribute in my program.

To test this I wrote a C program but I am not able to understand how will I use **attribute** keyword of C  in it
```
#include<stdio.h>
int myfunction (int ,int);
int main ()
{
 int a,b,c;
 printf("Enter 2 numbers \n");
 scanf("%d,%d",&a,&b);
 c = myfunction(a,b);
 printf("the result is %d ",c);
  return 0;
}

int myfunction (int a,int b)
{
 int c;
return c=a+b;
}

```

---

### Post by Arndt on 2010-11-22
> **jamesbon said:**
> I am trying to understand usage of keyword __attribute in C 
I have checked following two pages
[http://unixwiz.net/techtips/gnu-c-attributes.html](http://unixwiz.net/techtips/gnu-c-attributes.html)
and this page also 
[http://gcc.gnu.org/onlinedocs/gcc-4.0.0/gcc/Function-Attributes.html](http://gcc.gnu.org/onlinedocs/gcc-4.0.0/gcc/Function-Attributes.html)
but still I could not understand where do I declare them and how I can use __attribute in my program.

To test this I wrote a C program but I am not able to understand how will I use **attribute** keyword of C  in it
```
#include<stdio.h>
int myfunction (int ,int)
int main ()
{
 int a,b,c;
 printf("Enter 2 numbers \n");
 scanf("%d,%d",&a,&b);
 c = myfunction(a,b);
 printf("the result is %d ",c);
 exit 0;
}

int myfunction (int a,int b)
{
 int c;
return c=a+b;
}

```

I don't see how you can use __attribute in that program either, but what is it you want to achieve? The pages you link to explain quite well in which situations __attribute is useful, I think. Are you seeing __attribute in some program and don't know why it's there?

---

### Post by jamesbon on 2010-11-22
> **Arndt said:**
> I don't see how you can use __attribute in that program either, but what is it you want to achieve? The pages you link to explain quite well in which situations __attribute is useful, I think. Are you seeing __attribute in some program and don't know why it's there?
You might have understood from those links that does not mean that even I will understand.The reason I asked is I could not understand those links and how do I put myfunction and attribute together  just show me one way it can be done I will be able to understand those links.

---

### Post by randumnumber on 2010-11-22
It is used to give an attribute to something, as you can see by the example.
```

int old_fn () __attribute__ ((deprecated));
          int old_fn ();
          int (*fn_ptr)() = old_fn;

```

this gives the int old_fn the attribute deprecated and then it will give you errors anywhere this is located in the source files. This way you can go though and change to a new function or what have you.

---

### Post by Arndt on 2010-11-22
> **jamesbon said:**
> You might have understood from those links that does not mean that even I will understand.The reason I asked is I could not understand those links and how do I put myfunction and attribute together  just show me one way it can be done I will be able to understand those links.

I'd like to lead you along the way to understanding, but just quoting parts of those pages will not help, obviously. Did you copy the example programs from those pages, and compile them?

I see now that I look at the previous posts, that you edited your code after I commented your post. It has "exit 0" (which is not compilable) instead of "return 0". For functions not returning, it's possible to suppress warnings by using __attribute. Is that what you want?

---

### Post by wmcbrine on 2010-11-22
It should not be used at all. It's non-standard.

When you're much more experienced in C, you can learn about possible exceptions to this rule. But by then, you won't have to ask us to explain it. (I can tell you that personally, I've never needed it.)

---

### Post by jamesbon on 2010-11-23
> **randumnumber said:**
> It is used to give an attribute to something, as you can see by the example.
```

int old_fn () __attribute__ ((deprecated));
          int old_fn ();
          int (*fn_ptr)() = old_fn;

```this gives the int old_fn the attribute deprecated and then it  will give you errors anywhere this is located in the source files. This  way you can go though and change to a new function or what have  you.


Not yet clear.What I understand from your post is while using a keyword __attribute__ in a function definition the above is a way by which we can specify like
```
int n;
```
I did not understood anything more than this.

> **Arndt said:**
> I'd like to lead you along the way to understanding, but just quoting parts of those pages will not help, obviously. Did you copy the example programs from those pages, and compile them?

Those programs do not have a main defined.
I compiled and got a lot of errors and warnings.
> **Arndt said:**
> 
I see now that I look at the previous posts, that you edited your code after I commented your post. It has "exit 0" (which is not compilable) instead of "return 0". For functions not returning, it's possible to suppress warnings by using __attribute. Is that what you want?
Yes I had edited the post as I later felt that I should understand the use of __attribute__
in a correctly written program.Never mind if you can give an example of this also that will also help me I have a read a lot about __attribute__ but I have not at all understood it.
> **wmcbrine said:**
> It should not be used at all. It's non-standard.

When you're much more experienced in C, you can learn about possible  exceptions to this rule. But by then, you won't have to ask us to  explain it. (I can tell you that personally, I've never needed  it.)

Currently I am not bothered with standards I just want to understand how it works.

---

### Post by Arndt on 2010-11-23
> **jamesbon said:**
> 
Those programs do not have a main defined.
I compiled and got a lot of errors and warnings.


Yes, so "programs" was not the word I should have chosen, but "code". If you show the program you attempted to compile based on the examples there, and what error messages you got, then we can help you fix them.

---

### Post by jamesbon on 2010-11-23
> **Arndt said:**
> Yes, so "programs" was not the word I should have chosen, but "code". If you show the program you attempted to compile based on the examples there, and what error messages you got, then we can help you fix them.
This is the program on your link named test1.c
```
#include<stdio.h>
extern void exitnow();

int foo(int n)
{
        if ( n > 0 )
        {
                exitnow();
                /* control never reaches this point */
        }
        else
                return 0;
}

```I just copy pasted it
and when I compiled it as mentioned on that link
it gave me following warning
```
cc -Wall -c temp2.c 
temp2.c: In function &#8216;foo&#8217;:
temp2.c:13: warning: control reaches end of non-void function
```Where temp2.c is the name of program I have.


I am using gcc
```

 gcc -v
Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.4.3-4ubuntu5' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --program-suffix=-4.4 --enable-nls --enable-clocale=gnu --enable-libstdcxx-debug --enable-plugin --enable-objc-gc --disable-werror --with-arch-32=i486 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5)
```and uname -a
```
2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:52:42 UTC 2010 x86_64 GNU/Linux
```
Where as if I compile the program 
test2.c on the [link]("http://unixwiz.net/techtips/gnu-c-attributes.html")
```

extern void exitnow() __attribute__((noreturn));

int foo(int n)
{
        if ( n > 0 )
                exitnow();
        else
                return 0;
}

```
as mentioned 
```
 cc -c -Wall temp3.c
```
on my system I do not get any message and it seems it compile without any problem.

---

### Post by Arndt on 2010-11-23
> **jamesbon said:**
> This is the program on your link named test1.c
```
#include<stdio.h>
extern void exitnow();

int foo(int n)
{
        if ( n > 0 )
        {
                exitnow();
                /* control never reaches this point */
        }
        else
                return 0;
}

```I just copy pasted it
and when I compiled it as mentioned on that link
it gave me following warning
```
cc -Wall -c temp2.c 
temp2.c: In function ‘foo’:
temp2.c:13: warning: control reaches end of non-void function
```Where temp2.c is the name of program I have.


I am using gcc
```

 gcc -v
Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.4.3-4ubuntu5' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --program-suffix=-4.4 --enable-nls --enable-clocale=gnu --enable-libstdcxx-debug --enable-plugin --enable-objc-gc --disable-werror --with-arch-32=i486 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5)
```and uname -a
```
2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:52:42 UTC 2010 x86_64 GNU/Linux
```

I don't understand. Wasn't the example meant to show the usage of __attribute? The compiler behaves exactly as I would expect for your example.

---

### Post by jamesbon on 2010-11-23
You are right this is how it is given on that page but the code I wrote in my first post suppose say the function **myfunction** of my code I want to use 
> __attribute__(scanf) 
then what should I modify in that.

---

### Post by Arndt on 2010-11-23
> **jamesbon said:**
> You are right this is how it is given on that page but the code I wrote in my first post suppose say the function **myfunction** of my code I want to use 

then what should I modify in that.

I have problems understanding what you write. Please use some commas and periods to make your sentences easier to read.

In your first post, you use scanf, and there is nothing you need do to that function - it probably already is recognized specially by the compiler, whether by use of __attribute or builtin, I don't know.

But your code above has no similarity to your first post, that I can see.

---

### Post by Arndt on 2010-11-23
I didn't look too closely before at the pages you referred to. I see that your most recent code here comes from the section that begins

> In this example, two nearly-identical C source files refer to an "exitnow()" function that never returns, but without the __attribute__ tag, the compiler issues a warning. The compiler is correct here, because it has no way of knowing that control doesn't return. 

I find this text and the two following code blocks and their comments perfectly clear. What is there that you don't understand? Did you try the second code block, where __attribute__ is used?

---

### Post by jamesbon on 2010-11-23
I am referring to this program.```

#include<stdio.h>
int myfunction (int ,int);
int main ()
{
 int a,b,c;
 printf("Enter 2 numbers \n");
 scanf("%d,%d",&a,&b);
 c = myfunction(a,b);
 printf("the result is %d ",c);
  return 0;
}

int myfunction (int a,int b)
{
 int c;
return c=a+b;
}
```Here I want to use **__attribute__** with scanf as an argument of attribute.
So how can I do that?

---

### Post by Arndt on 2010-11-23
> **jamesbon said:**
> I am referring to this program.```

#include<stdio.h>
int myfunction (int ,int);
int main ()
{
 int a,b,c;
 printf("Enter 2 numbers \n");
 scanf("%d,%d",&a,&b);
 c = myfunction(a,b);
 printf("the result is %d ",c);
  return 0;
}

int myfunction (int a,int b)
{
 int c;
return c=a+b;
}
```Here I want to use **__attribute__** with scanf as an argument of attribute.
So how can I do that?

I wish you would pay more attention to the replies you get. I quote myself:

> In your first post, you use scanf, and there is nothing you need do to that function - it probably already is recognized specially by the compiler, whether by use of __attribute or builtin, I don't know.

Having said that, of course you can equip scanf with an __attribute__ format, even if it is useless, just for testing the syntax, for example. What have you tried so far? Take one of the examples and modify it until it does what you want.

---

