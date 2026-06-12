---
title: "libgmp crashes if the number is big"
date: 2010-03-10
forum: Programming Talk
---

### Post by perham on 2010-03-10
well, the idea of using gmp is to be able to use big numbers. this has really disappointed me. here's the code:

```

#include <iostream>
#include <stdio.h>
#include <gmp.h>

using namespace std;


int first_factor(const mpz_t x, mpz_t res)
{
     mpz_t i,t1;
     mpz_init_set_str(i,"2",10);
     mpz_init(t1);


     while (mpz_cmp(t1,x)<=0)
          {


          if (mpz_divisible_p(x,i)) { mpz_set(res,i); return 1;}

          mpz_add_ui(i,i,1);
          mpz_mul(t1,i,i);

          }

     mpz_set(res,x);
     return -1;

};


int main()
{

    mpz_t x,t;
    char inp[40];

    cout << "\nEnter the number:\n";
    cin>> inp;

    mpz_init_set_str(x,inp,10);
    mpz_init(t);

    cout << "\n1";
    
    while (mpz_cmp_ui(x,1)) 
          {
          cout << "*";
          first_factor(x,t);

          mpz_divexact(x,x,t);
          mpz_out_str(NULL,10,t); 
          }
return 0;
}
```

the program works flawlessly when I enter a 10-15 digit number, but more than that, it often breaks with stack smashing error or something like that, or it just hangs. any idea why? should I report this as a bug to gmp team?

---

### Post by Lux Perpetua on 2010-03-10
It's almost definitely a bug in your code, but most people (including myself) are not going to read it if you're not going to indent it. Please edit your post to indent your code.

---

### Post by MadCow108 on 2010-03-10
I'd say it "hangs" because its working.
Factoring big numbers is an unsolved highly complex problem. It takes ages with today known methods (unless you have a quantum computer, on which the problem is solvable).
That the reason big factors are used for certain encryptions.

the stack smashing may be related to you overrunning your input buffer. I cannot say without more input on what your inputting.

---

### Post by perham on 2010-03-10
> **MadCow108 said:**
> I'd say it "hangs" because its working.
Factoring big numbers is an unsolved highly complex problem. It takes ages with today known methods (unless you have a quantum computer).
That the reason big factors are used for certain encryptions.


very true.


> 
the stack smashing may be related to you overrunning your input buffer. I cannot say without more input on what your inputting.

I changed the header from gpm.h to gmpxx.h, and ran g++ with -lgmpxx instead of -lgmp and suddenly it works as it should. it seems that g++ will not work correctly with gmp headers designed for C. so the issue is solved. I'm now searching for a way to display a progress bar for this procedure. seems that I should find a way to know what gmp is doing when processing the requests.

---

### Post by perham on 2010-03-10
> **Lux Perpetua said:**
> It's almost definitely a bug in your code, but most people (including myself) are not going to read it if you're not going to indent it. Please edit your post to indent your code.

it's a very simple code. just needs a look to understand.

---

