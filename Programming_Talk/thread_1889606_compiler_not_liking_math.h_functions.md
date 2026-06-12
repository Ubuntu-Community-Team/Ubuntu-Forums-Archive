---
title: "compiler not liking math.h functions"
date: 2011-12-01
forum: Programming Talk
---

### Post by bikewrecker on 2011-12-01
hi everybody. I'm getting a compiler error that I dont understand and was wondering if you guys could help. At the top of my program I include stdio.h and math.h, and according to numerous websites including [http://www.gnu.org/s/hello/manual/libc/Exponents-and-Logarithms.html](http://www.gnu.org/s/hello/manual/libc/Exponents-and-Logarithms.html), powf and log1pf should be functions that work in math.h. Here's the function that uses these:
```

void function(float* B, float* i, float* m)
{
    float N, newBal, lastPayment, concurrently;
    int k, number, counter, TotalNumberOfPayments1;

    for(counter = 0; counter < num_of_credits; counter++){
        N = -log1pf(1-i[counter]*B[counter]/(m[counter]+X))/log1pf(1+i[counter]);
        for(k = 0; k < N; ++k){
            number = k;}
        newBal = powf(B[counter]*(1+i[counter]),number) - ((m[counter] + X)/ i[counter])*(powf(1+i[counter],number-1));
        lastPayment = newBal + (newBal*i[counter]);

        for(k = counter+1; k < num_of_credits; k++){
            concurrently = powf(B[k]*(i[k]+1),number) - (m[k]/i[k])*(powf(i[k]+1,number-1));
            B[k] = concurrently; }// concurrently is factoring in all the minimum payments being payed while the main payment is going on

        if (counter  !=  num_of_credits - 1){
            B[counter+1] = (B[counter+1]-(X-lastPayment)+X)*(i[counter+1]);
            number = number +1; }

        TotalNumberOfPayments1 += number;
    }
    
    if(TotalNumberOfPayments1 > TotalNumberOfPayments2) {
        TotalNumberOfPayments2 = TotalNumberOfPayments1;
        for(k = 0; k < num_of_credits; k++) 
        finalOrder[k] = order[k];}
}//function

```and here is the error message:

```

daniel@daniel-EP45-UD3L:~/Desktop$ cc -o myProgram.out myProgram.c
/tmp/cclWFzok.o: In function `function':
myProgram.c:(.text+0x2c5): undefined reference to `log1pf'
myProgram.c:(.text+0x2fa): undefined reference to `log1pf'
myProgram.c:(.text+0x36e): undefined reference to `powf'
myProgram.c:(.text+0x3e1): undefined reference to `powf'
myProgram.c:(.text+0x461): undefined reference to `powf'
myProgram.c:(.text+0x4c0): undefined reference to `powf'
collect2: ld returned 1 exit status

```Thanks for any help you can give me!

---

### Post by Arndt on 2011-12-01
> **bikewrecker said:**
> hi everybody. I'm getting a compiler error that I dont understand and was wondering if you guys could help. At the top of my program I include stdio.h and math.h, and according to numerous websites including [http://www.gnu.org/s/hello/manual/libc/Exponents-and-Logarithms.html](http://www.gnu.org/s/hello/manual/libc/Exponents-and-Logarithms.html), powf and log1pf should be functions that work in math.h. Here's the function that uses these:
```

void function(float* B, float* i, float* m)
{
    float N, newBal, lastPayment, concurrently;
    int k, number, counter, TotalNumberOfPayments1;

    for(counter = 0; counter < num_of_credits; counter++){
        N = -log1pf(1-i[counter]*B[counter]/(m[counter]+X))/log1pf(1+i[counter]);
        for(k = 0; k < N; ++k){
            number = k;}
        newBal = powf(B[counter]*(1+i[counter]),number) - ((m[counter] + X)/ i[counter])*(powf(1+i[counter],number-1));
        lastPayment = newBal + (newBal*i[counter]);

        for(k = counter+1; k < num_of_credits; k++){
            concurrently = powf(B[k]*(i[k]+1),number) - (m[k]/i[k])*(powf(i[k]+1,number-1));
            B[k] = concurrently; }// concurrently is factoring in all the minimum payments being payed while the main payment is going on

        if (counter  !=  num_of_credits - 1){
            B[counter+1] = (B[counter+1]-(X-lastPayment)+X)*(i[counter+1]);
            number = number +1; }

        TotalNumberOfPayments1 += number;
    }
    
    if(TotalNumberOfPayments1 > TotalNumberOfPayments2) {
        TotalNumberOfPayments2 = TotalNumberOfPayments1;
        for(k = 0; k < num_of_credits; k++) 
        finalOrder[k] = order[k];}
}//function

```and here is the error message:

```

daniel@daniel-EP45-UD3L:~/Desktop$ cc -o myProgram.out myProgram.c
/tmp/cclWFzok.o: In function `function':
myProgram.c:(.text+0x2c5): undefined reference to `log1pf'
myProgram.c:(.text+0x2fa): undefined reference to `log1pf'
myProgram.c:(.text+0x36e): undefined reference to `powf'
myProgram.c:(.text+0x3e1): undefined reference to `powf'
myProgram.c:(.text+0x461): undefined reference to `powf'
myProgram.c:(.text+0x4c0): undefined reference to `powf'
collect2: ld returned 1 exit status

```Thanks for any help you can give me!

```
$ man powf

...

SYNOPSIS
       #include <math.h>

       double pow(double x, double y);
       float powf(float x, float y);
      long double powl(long double x, long double y);

       Link with -lm.

```

So link with -lm.

---

### Post by bikewrecker on 2011-12-01
Ok, Sorry I'm really new to C. How do I link things? I tried googling it, but all the pages on linking were rather cryptic. 

Thanks for your help!

---

### Post by MadCow108 on 2011-12-01
add -lm to the end of the command line:
```
cc -o myProgram.out myProgram.c -lm
```

that flag -l*name* will look in the library search paths (gcc -print-search-dirs) and paths provided with the -L*path* flag for files named lib*name*.extension
in this case libm.so in /usr/lib/<architecture-triplet>

---

### Post by bikewrecker on 2011-12-01
Sweet! It's working now! Thank you guys so much for your help! You've saved me days of pulling my hair out and cursing at my screen. I really appreciate it!

---

