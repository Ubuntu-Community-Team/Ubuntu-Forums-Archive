---
title: "An interesting experiment (for me)."
date: 2006-11-20
forum: Programming Talk
---

### Post by slavik on 2006-11-20
This was the first program that I wrote in college using C. The program prints numbers 1 to 100, 5 numbers on each line.

Challenge: write a program in a language of your choice and try to make it as optimal as possible ...

```

#include <stdio.h>

void main(){
  int i;
  for (i=1;i<101;i++) {
    printf("%d ",i);
    if(i%5==0) printf("\n");
  }
}

```

Perl people must also do it in 1 line.

---

### Post by adwait on 2006-11-20
How about this (in c++):

```

#include<stdio.h>

int main()
{

        for(int i=-5;i<=94;i+=5,printf("%d %d %d %d %d\n",i+1,i+2,i+3,i+4,i+5));
}

```

---

### Post by DaveBorealis on 2006-11-20
```

#!/usr/bin/python
for i in range(1,100,5): print str(i), str(i+1), str(i+2), str(i+3), str(i+4)
```

How about someone more experienced in python shorten this even more?

Dave

---

### Post by Dot Communist on 2006-11-20
How do i run these o_O

---

### Post by hod139 on 2006-11-20
Here's another C++ example that will be hard to beat:
```

#include<iostream>

int main()
{
    std::cout << "1 2 3 4 5 \n";
    std::cout << "6 7 8 9 10\n";
    std::cout << "11 12 13 14 15\n";
    std::cout << "16 17 18 19 20\n";
    std::cout << "21 22 23 24 25\n";
    std::cout << "26 27 28 29 30\n";
    std::cout << "31 32 33 34 35\n";
    std::cout << "36 37 38 39 40\n";
    std::cout << "41 42 43 44 45\n";
    std::cout << "46 47 48 49 50\n";
    std::cout << "51 52 53 54 55\n";
    std::cout << "56 57 58 59 60\n";
    std::cout << "61 62 63 64 65\n";
    std::cout << "66 67 68 69 70\n";
    std::cout << "71 72 73 74 75\n";
    std::cout << "76 77 78 79 80\n";
    std::cout << "81 82 83 84 85\n";
    std::cout << "86 87 88 89 90\n";
    std::cout << "91 92 93 94 95\n";
    std::cout << "96 97 98 99 100\n";

    return 0;
}

```I'm guessing you really wanted a loop with an increment though?  This example removes a lot of the adds the previous post has. 
```

#include<iostream>

int main()
{
    register int i = 0;
        while(i < 100){
           std::cout << ++i << " ";
           std::cout << ++i << " ";
           std::cout << ++i << " ";
           std::cout << ++i << " ";
           std::cout << ++i << "\n";
    }
    return 0;
}

```

In all, I'm not sure you will notice any performance differences with such an easy program.

---

### Post by Dot Communist on 2006-11-20
> **Dot Communist said:**
> How do i run these o_O
???

---

### Post by hod139 on 2006-11-20
> 
How do i run these o_O

To run my c++ examples, copy my code into a text file, say foo.cpp, and type:
```

g++ foo.cpp

```

and then to run it, type
```

./a.out

```

Make sure you have the build-essential package installed/

---

### Post by Dot Communist on 2006-11-20
oh ty :]

---

### Post by DaveBorealis on 2006-11-20
And for a little perl:
```
#!/usr/bin/perl
while($i<100) { print ++$i." ".++$i." ".++$i." ".++$i." ".++$i."\n"; }

```

Dave

---

### Post by slavik on 2006-11-21
hod139, nice one!!!

One thing I was thinking, when I submitted my original code, the prof said that it could be made more efficient (by printing 5 numbers at once on the line).

Later on, I was told about 'funny loops' (not sure of the exact name), gcc if given the option tries to predict how many iterations it will go through, it will expand them all so that it doesn't actually do the increment (faster code, but also longer).

Coupled with the fact that it can also precalculate i+1 (i+2, etc.) (since we know i and the other is a constant), in the end, the compiler (or interpreter when compiling into pcode) can spit out the code that hod139 meant to be funny (which it was).

another perl type I was thinking of:
```

for $i(0..95) { print $_+1." ".$_+2." ".$_+3." ".$_+4." ".$_+5."\n"; }

```

Another thing I just remembered, when I took x86 assembly, I was told that for operations, encoding a number (versus a register/memory address) is more inefficient ... but I doubt it plays into much today.

As a side note (neat tricks, interesting):
changing 2 variables:
```

a^=b; //a = a xor b
b^=a; //b = b xor a
a^=b; //a = a xor b

```

```

sub ax, ax ;zero out ax
xor ax, ax ;zero out ax, this used to be faster on 80386 than the sub method and mov ax, 0 is just plain murder back in the day ...

```

---

### Post by amo-ej1 on 2006-11-21
```

edb@lapedb:~$ echo {1..100} | sed -e  's/\([0-9]* [0-9]* [0-9]* [0-9]* [0-9]* \)/\1\n/g

```

:)

---

### Post by pichalsi on 2006-11-21
> **amo-ej1 said:**
> ```

edb@lapedb:~$ echo {1..100} | sed -e  's/\([0-9]* [0-9]* [0-9]* [0-9]* [0-9]* \)/\1\n/g

```

:)

Winner :)

---

### Post by adwait on 2006-11-21
I am supposed to just run that as a command at the bash prompt right? doesn't work here..just gives a 
>
and waits for more input.

---

### Post by Ramses de Norre on 2006-11-21
```
class Fast
{
        public static void main(String[] args)
        {
                for(int i=1;i<=100;i++)
                {
                        if(i%5==1) System.out.println("");
                        System.out.print(i+"\t");
                }
                System.out.println("");
        }
}
```

---

