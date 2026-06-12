---
title: "Predefined functions C++"
date: 2010-03-14
forum: Programming Talk
---

### Post by YourMomsASmurph on 2010-03-14
Every once in a while I become curious about exactly how a function works, or how someone managed to create a function that is predefined in the compiler, functions like 

rand()
atoi()
sqrt() <-- assuming this is some type of approximating series, but could be wrong.\

So if you could let me know where I could find the _source code_ ([SIZE=1]usage?). [/SIZE]it would be appreciated. :)[SIZE=1][SIZE=2] [/SIZE][/SIZE]

---

### Post by MadCow108 on 2010-03-14
rand uses a linear congruential random number generator
its very simple:
r_n+1 = a(r_n + b) mod c
where a,b and c are parameters (of course the optimal ones) and r_0 is the seed provided by srand()

atoi is just some string parsing

sqrt will use some numerical method to compute it:
[http://en.wikipedia.org/wiki/Methods_of_computing_square_roots](http://en.wikipedia.org/wiki/Methods_of_computing_square_roots)

the source for all this should be in glibc:
[http://www.gnu.org/software/libc/](http://www.gnu.org/software/libc/)

---

### Post by n0dix on 2010-03-14
Rand: [http://www.cplusplus.com/reference/clibrary/cstdlib/rand/]("http://www.cplusplus.com/reference/clibrary/cstdlib/rand/")
Atoi: [http://www.cplusplus.com/reference/clibrary/cstdlib/atoi/]("http://www.cplusplus.com/reference/clibrary/cstdlib/atoi/")
Sqrt: [http://www.cplusplus.com/reference/clibrary/cmath/sqrt/]("http://www.cplusplus.com/reference/clibrary/cmath/sqrt/")

---

### Post by heikaman on 2010-03-14
Those functions are defined in the standard c/c++ library, your compiler (assuming gcc) links your program with the standard libraries by default.

You can read about standard libraries in the man pages:
man atoi

---

### Post by Zugzwang on 2010-03-14
For the "sqrt()" function, you will probably have no luck with finding how it is implemented as nowadays, there exist processor commands for computing square roots from floating point number. Thus, one might assume that the "sqrt()" function simply utilises the processor command.

---

### Post by Lux Perpetua on 2010-03-14
> **Zugzwang said:**
> For the "sqrt()" function, you will probably have no luck with finding how it is implemented as nowadays, there exist processor commands for computing square roots from floating point number. Thus, one might assume that the "sqrt()" function simply utilises the processor command.IIRC, the IEEE specification does include a square-root operation, so any floating-point unit implementing the IEEE standard should have a square-root instruction. (The Intel architecture does, but I'm not sure about others.) The math.h function sqrt() should then simply be a wrapper for the hardware instruction.

To YourMomsASmurph: atoi() is something that a first-year CS student should be able to write without much trouble. I suggest trying to implement it yourself before looking at the source code.

---

### Post by YourMomsASmurph on 2010-03-15
@Lux -- > yea it wasn't really hard to do, took about 20 minutes. Though some things I think could be done better. // I'm also pretty sure most first year CS students could create a function that will estimate sqrt() {{taylor series mayb}}

Like:
1.MAX_SIZE being an acctual max size.  
2. return ((inumber-1)/10); --> really not sure why this is needed but my code cept coming out as 123451 if i input 12345
3. It is probably possible to stop when number[i] == "\0" (end point of c-string) but I have no idea how to do this. *tried the code number[i] == "\0" but it didnt work :(, some problem with "\0" being a pointer.* 


----------------------------- SECOND ATTEMPT ----------------------------------------

> **Lux Perpetua said:**
> Yes, it's not hard to approximate, but I think getting it correct in the IEEE sense (i. e., as accurate as possible given the limitations of the representation) would be pretty challenging. 

Correct me if I'm wrong but couldn't a taylor series theoritcally correctly estimate sqrt to an infinite number of decimal places (dependant on the number of terms in the series). Although this would require a number of calculations to be made within a loop :. it might not be optimal for anything makes consistent use of the sqrt computaion, and is required to do it fast.


> **Lux Perpetua said:**
> 
Your code doesn't work because it walks right off the end of the string. atoi stops reading at the first non-decimal-digit character, which is a convenient exit condition because it's automatically satisfied when you reach the null terminator at the end of the string. In any case, while the exact behavior when the string contains non-decimal-digit characters may be negotiable for a "str2int" function, failing to stop at a null character is unambiguously wrong.

Well, this is second attempt at it, and it works liek ATOI now, ending at the first non-decimal-digit character. 

Howver, I am curious of what the ascii value for the null character is, I could try printing out the "\0" integer value, but I have a feeling that that is wrong. 
(This would help stop searching directly at the null character instead of at the first non decimal character.

--> didn't want to keep this thread alive so edited instead of posting. :. I'm not exactly expecting a response.




[PHP]
/*
Attempt 2:
*/

#include <cstdlib>
#include <iostream>

using namespace std;

const int MAX_SIZE = 25;

unsigned int str2int(char number[]);

unsigned int str2int(char number[])
{
    int inumber(0);
    
    for (int i = 0; i <= MAX_SIZE; i++)
    {
        if (int(number[i]) >= 48 && int(number[i]) <= 57){
            inumber *= 10;
            inumber += (int(number[i])-48);
        }
        else 
            break;
   
    }
    return (inumber);

}


int main()
{
    char number[MAX_SIZE]; // this is more for testing than anything else.
    unsigned int strnum(0);
   
    cin >> number;
    cout << endl;
   
    strnum = str2int(number);
    cout << strnum <<endl;

    cout << endl <<endl;
    system("PAUSE");
    return 0;
}

[/PHP]

---

### Post by Lux Perpetua on 2010-03-15
> **YourMomsASmurph said:**
> @Lux -- > yea it wasn't really hard to do, took about 20 minutes. Though some things I think could be done better. // I'm also pretty sure most first year CS students could create a function that will estimate sqrt() {{taylor series mayb}}Yes, it's not hard to approximate, but I think getting it correct in the IEEE sense (i. e., as accurate as possible given the limitations of the representation) would be pretty challenging. 

Your code doesn't work because it walks right off the end of the string. atoi stops reading at the first non-decimal-digit character, which is a convenient exit condition because it's automatically satisfied when you reach the null terminator at the end of the string. In any case, while the exact behavior when the string contains non-decimal-digit characters may be negotiable for a "str2int" function, failing to stop at a null character is unambiguously wrong.

---

### Post by Simon17 on 2010-03-16
You might also want to check out this:
[http://en.wikipedia.org/wiki/Fast_inverse_square_root](http://en.wikipedia.org/wiki/Fast_inverse_square_root)

---

### Post by unknownPoster on 2010-03-16
> **Zugzwang said:**
> For the "sqrt()" function, you will probably have no luck with finding how it is implemented as nowadays, there exist processor commands for computing square roots from floating point number. Thus, one might assume that the "sqrt()" function simply utilises the processor command.

I know the SPARC instruction set has the following:

```

FSQRTs

FSQRTd

FSQRTq

```

---

