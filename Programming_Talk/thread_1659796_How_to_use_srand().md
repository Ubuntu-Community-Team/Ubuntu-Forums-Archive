---
title: "How to use srand()"
date: 2011-01-04
forum: Programming Talk
---

### Post by Dorian Mayorquin on 2011-01-04
Hello everybody, i was taking a course in C++ but i don't know if i can use srand() and rand() not only for int numbers but for double numbers, to generate random double numbers, also when i put a letter instead of a number in the generator, i gives me a numeric result why? oh and finally when i put an int number the program gives a result and closes, but then when i open it again, and put the same number it gives me the same random results, so does the code has to be in order?

code:

#include <iostream>
#include <cstdlib>
#include <cmath>


using namespace std;

int main()

{
    unsigned int number;
    unsigned int n1,n2,n3;
    cout << "\t\t\t\tRandom Number Generator"<<endl;
    cout<< "------------------------------------------"<<endl;
    cout<<"Type a Number"<<endl;
    cin >> number;

    srand(number);


    n1 = rand();
    n2 = rand();
    n3 = rand();


    cout << "Random Numbers Are: \n " << n1 << "\n" << n2 << "\n" << n3 << "\n" << endl;

    system("pause");
    return 0;



}

or

#include <iostream>
#include <cstdlib>


using namespace std;

int main()

{
    unsigned int number;
    unsigned int n1,n2,n3;
    cout << "\t\t\t\tRandom Number Generator"<<endl;
    cout<< "------------------------------------------"<<endl;
    cout<<"Type a Number"<<endl;
    cin >> number;

    

    cout << "Random Numbers Are: \n " << n1 << "\n" << n2 << "\n" << n3 << "\n" << endl;

srand(number);


    n1 = rand();
    n2 = rand();
    n3 = rand();


    system("pause");
    return 0;



}




thanks everyone!!

---

### Post by Arndt on 2011-01-04
> **Dorian Mayorquin said:**
> Hello everybody, i was taking a course in C++ but i don't know if i can use srand() and rand() not only for int numbers but for double numbers, to generate random double numbers, also when i put a letter instead of a number in the generator, i gives me a numeric result why? oh and finally when i put an int number the program gives a result and closes, but then when i open it again, and put the same number it gives me the same random results, so does the code has to be in order?

code:

#include <iostream>
#include <cstdlib>
#include <cmath>


using namespace std;

int main()

{
    unsigned int number;
    unsigned int n1,n2,n3;
    cout << "\t\t\t\tRandom Number Generator"<<endl;
    cout<< "------------------------------------------"<<endl;
    cout<<"Type a Number"<<endl;
    cin >> number;

    srand(number);


    n1 = rand();
    n2 = rand();
    n3 = rand();


    cout << "Random Numbers Are: \n " << n1 << "\n" << n2 << "\n" << n3 << "\n" << endl;

    system("pause");
    return 0;



}

or

#include <iostream>
#include <cstdlib>


using namespace std;

int main()

{
    unsigned int number;
    unsigned int n1,n2,n3;
    cout << "\t\t\t\tRandom Number Generator"<<endl;
    cout<< "------------------------------------------"<<endl;
    cout<<"Type a Number"<<endl;
    cin >> number;

    

    cout << "Random Numbers Are: \n " << n1 << "\n" << n2 << "\n" << n3 << "\n" << endl;

srand(number);


    n1 = rand();
    n2 = rand();
    n3 = rand();


    system("pause");
    return 0;



}




thanks everyone!!

I quote from the man page for 'srand':

```
       #include <stdlib.h>

       int rand(void);

       int rand_r(unsigned int *seedp);

       void srand(unsigned int seed);

       The  rand()  function  returns  a  pseudo-random  integer  in the range
       [0, RAND_MAX].

      The srand() function sets its argument as the seed for a  new  sequence
       of  pseudo-random  integers  to be returned by rand().  These sequences
       are repeatable by calling srand() with the same seed value.

```

So, you are supposed to give an unsigned int to 'srand', and 'rand' will give you ints. What did you expect to happen when you give a letter? The letter, in a variable of type char, will just be treated as a number, for example, 'a' will be equivalent to 97.

To get a double, convert to double at some appropriate point, for example ((double) rand())/RAND_MAX.

The numbers are pseudo-random, i.e., the sequence is repeatable by using the same seed. If you want something which appears random, it may be random enough for your purposes to use the current time. There is open source code which gives you a much better seed, for example the one used for creating keys in openssh. And there are the device files /dev/random and /dev/urandom on Linux (look in "man 4 random"). Use these for the seed only, not for every number.

---

### Post by worksofcraft on 2011-01-04
srand and rand are intended to give what is known as a pseudo random sequence. i.e. the numbers it generates are always the same sequence and only look random.

The sequence it generates is guaranteed to be at least 2^32 long before it starts repeating itself. You should use srand to start that sequence at a different position if that is what you want (e.g. use the function time() to seed it).

Note however that in some situations people actually want the pseudo random sequence to be the same so that their tests will produce the same repeatable results even if the data looks random.

There is a number MAX_RAND defined that is the biggest number that rand will produce, so if you cast the unsigned integer result to double and divide by MAX_RAND then you get a result between 0 and 1.

p.s. oops no perhaps it's called RAND_MAX and not MAX_RAND... whatevah...

---

### Post by Arndt on 2011-01-04
> **worksofcraft said:**
> 
p.s. oops no perhaps it's called RAND_MAX and not MAX_RAND... whatevah...

The answer to that is in the post before yours.

---

### Post by worksofcraft on 2011-01-04
> **Arndt said:**
> The answer to that is in the post before yours.

Lol... so it is... I stopped reading when it started quoting the manual :D

---

### Post by Dorian Mayorquin on 2011-01-04
Thanks

---

### Post by onandcorei on 2011-01-05
In your examples, the program generates the same number  each time we run it because the generator is seeded with  the same default value each time. The following code will seed the  generator with the system time then output a single random number, which  should be different each time we run the program. 
```

#include <iostream>
#include <cstdlib>
#include <cmath>
#include <ctime>

using namespace std;

int main()

{
unsigned int n1,n2,n3;

srand((unsigned)time(0));

n1 = rand();
n2 = rand();
n3 = rand();


cout << "Random Numbers Are: \n " << n1 << "\n" << n2 << "\n" << n3 << "\n" << endl;

return 0;



}

```

---

