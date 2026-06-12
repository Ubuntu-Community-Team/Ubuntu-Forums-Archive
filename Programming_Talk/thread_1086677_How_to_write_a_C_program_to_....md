---
title: "How to write a C program to ..."
date: 2009-03-04
forum: Programming Talk
---

### Post by Bob John on 2009-03-04
Hello , buddies .

I am reading a C programming book these days . There is a practice I can't solve . It asks me to write a program to caculate the number of "space" in a paragraph . The "space" means the result of pressing space button on keyboard once . The paragraph is allowed to be any paragraph as you wish . So could you please help me to write this program ? My problem is simple : I don't know how to describe a "space" in the program . However , it is best that you can help me complete the entire program . 

Thank you very much .

---

### Post by Simian Man on 2009-03-04
In C, strings are just arrays of characters.  Characters are just 8-bit [ASCII values]("http://www.asciitable.com/").  The character that represents the space is decimal 32.  In your C program you can just use ' ' as a character literal, and the compiler will translate that into a 32 for you.

SO just loop through every character in the paragraph and check if it's equal to ' '.

---

### Post by Bob John on 2009-03-04
> **Simian Man said:**
> In C, strings are just arrays of characters.  Characters are just 8-bit [ASCII values]("http://www.asciitable.com/").  The character that represents the space is decimal 32.  In your C program you can just use ' ' as a character literal, and the compiler will translate that into a 32 for you.

SO just loop through every character in the paragraph and check if it's equal to ' '.

Thank you for your reply .

As you see , I am a newbie on C . So I changed my program as following according to your message . So in your opinion , will it work ?
```
#include <stdio.h>
main()
{
    long c,n;
    n=0;
    while((c=getchar())!=EOF)
        if(c=='')
        ++n;
    printf("%d\n",n);
}

```

---

### Post by sujoy on 2009-03-04
save that it a file with filename.c
and compile with

gcc filename.c -o output_filename

then you can run it as 

./output_filename


so try it and see if you are getting errors


EDIT: you can use "fgets" to take string inputs

---

### Post by abhilashm86 on 2009-03-04
> **Bob John said:**
> 
```
#include <stdio.h>
main()
{
    long c,n;
    n=0;
    while((c=getchar())!=EOF)
        if(c=='')
        ++n;
    printf("%d\n",n);
}

```

your code almost correct, just small correction, in line 7,
abhilash@abhi:~$ gcc cpgm1.c
cpgm1.c:7:15: error: empty character constant

so just modify like this,
> 
#include <stdio.h>
int main()
{
    long c,n;
    n=0;
    while((c=getchar())!=EOF)
        if(c==' ')
        ++n;
    printf("%d\n",n);
}


abhilash@abhi:~$ gcc cpgm1.c -o cpgm1
abhilash@abhi:~$ ./cpgm1
space in space can ever never be measured!!
7

this is required result right?better option is read from a file and check,try it

---

### Post by PandaGoat on 2009-03-04
I suggest the following:
[php]
#include <stdio.h>

int main()
{
  int c;
  unsigned int n = 0;

  while ((c=getchar()) != EOF)
    if (c == ' ')
      ++n;

  printf("%u\n", n);
} 

[/php]

First, I changed c to an integer.  getchar() will always return an integer on all systems.  The size of an int and long may differ: for example, [http://en.wikipedia.org/wiki/64-bit#64-bit_data_models](http://en.wikipedia.org/wiki/64-bit#64-bit_data_models).  You should always use the type that the function returns.

Also, I changed n to be an unsigned int.  I presume some paragraphs will have tons of spaces but never a negative amount of spaces.  A signed integer may have enough storage for pretty much all paragraphs but still.  Staying consistent is a virtue.

---

### Post by Bob John on 2009-03-04
> your code almost correct, just small correction, in line 7,
abhilash@abhi:~$ gcc cpgm1.c
cpgm1.c:7:15: error: empty character constant

so just modify like this,

Quote:
#include <stdio.h>
int main()
{
long c,n;
n=0;
while((c=getchar())!=EOF)
if(c==' ')
++n;
printf("%d\n",n);
}  

It seems that in line 7 , there is no differences between modified program and the original program . Is it a typing mistake ?

---

### Post by sujoy on 2009-03-04
> **Bob John said:**
> It seems that in line 7 , there is no differences between modified program and the original program . Is it a typing mistake ?

there ought to be a <space> between the quotes
```
if(c==' ')
```

---

### Post by Bob John on 2009-03-04
I correct the program as yours and the floor 7 's . But it doesn't work . When I finished typing the paragraph , I pressed "Enter" and nothing but a blank line shows up . And another "Enter" brings another blank line . So I have to use Ctrl+C to terminate it . So what's wrong with it ?

---

### Post by sujoy on 2009-03-04
your program waits till EOF, which is Ctrl+D
meaning you have to provide input strings and terminate it by pressing ctrl+d
enter is '\n' which is not equal to EOF ;)

---

### Post by Bob John on 2009-03-05
> **sujoy said:**
> your program waits till EOF, which is Ctrl+D
meaning you have to provide input strings and terminate it by pressing ctrl+d
enter is '\n' which is not equal to EOF ;)

Thank you very much , sujoy . You did help me a lot . Thank you . Thank you everyone replied . I do like to invite all of you to have this : :popcorn: :D

---

### Post by sujoy on 2009-03-05
Cheers :)
May the source be with you ;)

---

