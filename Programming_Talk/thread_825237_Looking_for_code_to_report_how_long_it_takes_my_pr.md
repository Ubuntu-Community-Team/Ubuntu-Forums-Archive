---
title: "Looking for code to report how long it takes my program to execute"
date: 2008-06-10
forum: Programming Talk
---

### Post by CoffeeBreath on 2008-06-10
Hi
I have some simple .cpp programs that I'm revising for clarity and speed. is there any code that I can inject into them to see how long it takes the computer to run them?


[PHP]
#include <iostream>
#include <math.h>
using namespace std;

int main() {
int n;
int i;
int is_prime;

is_prime = true;

cout << "Enter a number and press Enter: ";
cin >> n;

i = 2;

while ( i <= sqrt(static_cast<double>(n))) {
    if (n % 1 == 0 )
        is_prime = false;
i++;
}

if (is_prime)
     cout << "Number is prime.";
else
     cout << "Number is not prime.";
     cout << endl;

return 0;


}

[/PHP]

---

### Post by kknd on 2008-06-10
The simple solution is to test your program with a large input and use time to run it.

Example.:

time ./MyProgram 99999

The other way is to use "time.h" and get the current system time.


P.S.: When you need a big sequence of prime numbers, its more efficient to use the Sieve of Eratosthenes.

---

### Post by Can+~ on 2008-06-10
The most simple approach is take two measures of time with the time library (C example):
[PHP]
time_t time_start = time(NULL);
[task]
time_t time_end = time(NULL);

time_end-time_start; // Time delta
difftime(time_end, time_start); // Or difftime.[/PHP]

[http://www.cplusplus.com/reference/clibrary/ctime/difftime.html](http://www.cplusplus.com/reference/clibrary/ctime/difftime.html)

---

### Post by iansane on 2008-06-10
Hi, I'm a newb interested in something similar for my cpp programs.

I found this article in Linux Magazine about using strace to get all kinds of runtime info.

Not sure if it tells you what you want. It seems complicated to me but if your interested the article is "strace: The friend you never knew you had."
it's an intro to using strace.

[http://www.linux-mag.com/id/5509](http://www.linux-mag.com/id/5509)

You'll have to register and log in to see it though but it's free to register.

---

### Post by CoffeeBreath on 2008-06-10
I haven't had time to explore all the advice given yet and I need to reframe my question. What commands is there that can let me test how long it takes my computer to complete the program from right after I put in the input to the time it takes to give me output?

I can see where difftime may work but, I can't figure out where to put it or if it would really work in this case.

---

### Post by KingTermite on 2008-06-10
Never tried it or used it myself, but gcc has a built in profiler which should tell you such things.

Google this web page with "gcc profiler" search term.
[http://www.network-theory.co.uk/docs/gccintro/gccintro_80.html](http://www.network-theory.co.uk/docs/gccintro/gccintro_80.html)

Hope it helps.

---

### Post by CoffeeBreath on 2008-06-10
Thanks for gprof. I tried it. But, i think my program was too simple for it.

---

