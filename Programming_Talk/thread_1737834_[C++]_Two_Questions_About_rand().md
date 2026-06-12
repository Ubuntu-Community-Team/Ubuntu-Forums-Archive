---
title: "[C++] Two Questions About rand()"
date: 2011-04-23
forum: Programming Talk
---

### Post by dodle on 2011-04-23
I have two questions about the random number generating function rand(). 

Firstly, and this is because I am not good at math:), if I want to generate a random number between 1 and 10, I would use 10 as the maximum and 1 as the mininum:
[php]int num = rand() % 10 + 1;[/php]

But if I want to generate a number between 0 and 10 I have to simply use 11:
[php]int num = rand() % 11;[/php]

And maybe the answer is more complicated than I think, but why can't I use '10 + 0' or simply '10'?
[php]int num = rand() % 10 + 0;[/php]

This is just a question for mathematics-curiosity's sake. Again, I am not that good at math. If the answer is simple I will pound my head with a 2-by-4 (or a 5.08-by-10.16).


Second question: According to what I have read, rand() is not supposed to be uniform, but from this test program it appears that each number is produced about equally:
[php]#include <iostream>
using namespace std;

#include <cstdlib>
#include <ctime>

int GetNumber(int min = 0, int max = 11)
{
    int num;
    
    num = rand() % max + min;
    
    return num;
}

int main()
{
    // Seed the random number
    srand(time(NULL));
    
    int num;
    
    int zer=0, one=0, two=0, thr=0, fou=0, fiv=0, six=0, sev=0, eig=0, nin=0, ten=0;
    
    for (int x = 0; x < RAND_MAX; x++)
    {
        num = GetNumber();
        if (num == 1) one++;
        else if (num == 2) two++;
        else if (num == 3) thr++;
        else if (num == 4) fou++;
        else if (num == 5) fiv++;
        else if (num == 6) six++;
        else if (num == 7) sev++;
        else if (num == 8) eig++;
        else if (num == 9) nin++;
        else if (num == 10) ten++;
        else zer++;
    }
    
    cout << "Zeros:\t" << zer << endl;
    cout << "Ones:\t" << one << endl;
    cout << "Twos:\t" << two << endl;
    cout << "Threes:\t" << thr << endl;
    cout << "Fours:\t" << fou << endl;
    cout << "Fives:\t" << fiv << endl;
    cout << "Sixes:\t" << six << endl;
    cout << "Sevens:\t" << sev << endl;
    cout << "Eights:\t" << eig << endl;
    cout << "Nines:\t" << nin << endl;
    cout << "Tens:\t" << ten << endl;
    
    return 0;
}[/php]

So what is going on? What am I missing?

---

### Post by NovaAesa on 2011-04-23
In simple terms, if you want a number in the range [a, b] then you have to do ```
rand() % (b - a + 1) + a
```
I.e. reduce the random value modulo the size of the range you want, then add odd the smallest member in the range. So in your case where you want to get numbers between 0 and 10, there are 11 numbers in this range - 0,1,2,3,4,5,6,7,8,9,10. And the lowest number is 0. So you need to go ```
rand() % 11 + 0
```

For you second question, rand() IS meant to be uniform. Where did you read that it wasn't? Be aware however that when you do something like rand() % 10, this value will generally NOT be perfectly uniform. rand() returns a uniformly distributed number between 0 and RAND_MAX, so when you take rand() modulo 10, lower values will be slightly more likely unless RAND_MAX is divisible by 10 (which it's generally not, it's implementation specific though).

For example, if RAND_MAX is defined to be 32767, then the probabilities of rand() % 3 are as follows:

P(0) = 10923 / 32768
P(1) = 10923 / 32768
P(2) = 10922 / 32768

As you can see, 0 and 1 are both more likely than 2. Usually the slight probability difference can be ignored, but it could be important depending on what you are doing.

---

### Post by dodle on 2011-04-24
> **NovaAesa said:**
> ...rand() IS meant to be uniform. Where did you read that it wasn't?  ...

I read it here: [http://www.cplusplus.com/reference/clibrary/cstdlib/rand/](http://www.cplusplus.com/reference/clibrary/cstdlib/rand/), but I thought it was talking specifically about the function rand(). What you explained has made it clear.

---

### Post by dodle on 2011-04-24
Okay, another question: Will this help the output to be more uniform? It's pretty simple. I've heard that creating truly uniform random numbers is quite complicated.

[php]int GetRandInt(int min, int max)
 {
     int x;
     bool return_x;
     
     x = rand() % (max - min + 1) + min;
     return_x = rand() % 2;
     
     if (return_x) return x;
     else GetRandInt(min, max);
 }[/php]

**------ EDIT ------ **

Did I just create a potential memory leak? Should I put a "return" statement instead of "else"?

[php]int GetRandInt(int min, int max)
 {
     int x;
     bool return_x;
     
     x = rand() % (max - min + 1) + min;
     return_x = rand() % 2;
     
     if (return_x) return x;
     return GetRandInt(min, max);
 }[/php]

---

### Post by cyberslayer on 2011-04-24
> **dodle said:**
> Did I just create a potential memory leak? Should I put a "return" statement instead of "else"?

[php]int GetRandInt(int min, int max)
 {
     int x;
     bool return_x;
     
     x = rand() % (max - min + 1) + min;
     return_x = rand() % 2;
     
     if (return_x) return x;
     return GetRandInt(min, max);
 }[/php]

The original version won't leak memory, but the return value is undefined.  Since you are not using dynamic memory allocation, there is no possibility for leaks.  The code you posted won't make rand() more uniform; it will just cause it to randomly reject the number generated by rand() half the time.  It's well known that rand() generates poor quality random numbers compared to better RNGs like MT19937 ([http://en.wikipedia.org/wiki/Mersenne_twister](http://en.wikipedia.org/wiki/Mersenne_twister)) so if you are worried about the quality of the random numbers you're using you should use a better RNG.  That said, rand() is still good enough for most practical applications.

---

### Post by NovaAesa on 2011-04-24
I don't think your code would really give truly uniform answers, remember that rand() will give a different result each time.

Try something more like this:
```

int f(int min, int max) {
    r = max - min + 1
    do {
        x = rand();
    } while (x >= (RAND_MAX + 1) / r * r);
    return x % r + min;
}

```

Note that I didn't test my code, it just shows the general idea.

---

### Post by Arndt on 2011-04-24
In theory, doing rand()%n to get uniformly distributed numbers in the range 0..n-1 is fine, but in practice, one has to be careful. There are several random number generators available, and rand is one of the oldest and worst of them. If you do rand()%2, you will get the series 0, 1, 0, 1, 0, 1, 0, etc. Not random at all.

Much better is to take (double)rand()/RAND_MAX to obtain a floating point number in the range 0..1 and then multiply it with something appropriate.

The two other generators I know about that are immediately available are random and drand48.

---

### Post by dwhitney67 on 2011-04-24
> **dodle said:**
> 
[php]
int main()
{
    ...
    
    int zer=0, one=0, two=0, thr=0, fou=0, fiv=0, six=0, sev=0, eig=0, nin=0, ten=0;
    
    for (int x = 0; x < RAND_MAX; x++)
    {
        num = GetNumber();
        if (num == 1) one++;
        else if (num == 2) two++;
        else if (num == 3) thr++;
        else if (num == 4) fou++;
        else if (num == 5) fiv++;
        else if (num == 6) six++;
        else if (num == 7) sev++;
        else if (num == 8) eig++;
        else if (num == 9) nin++;
        else if (num == 10) ten++;
        else zer++;
    }
    
    ...
    
    return 0;
}[/php]

The declarations above are "silly"; consider simplifying your code by using an array.

[php]
int main()
{
    ...
    const int MAX = 11;
    int num_count[MAX];
    
    for (int x = 0; x < RAND_MAX; x++)
    {
        ++num_count[ GetNumber(0, MAX) ];
    }
    
    for (int x = 0; x < MAX; ++x)
    {
        std::cout << "Number of " << x << "'s is: " << num_count[x] << std::endl;
    }
    
    return 0;
}
[/php]

P.S.  I know, I know... not relevant to the problem the OP was asking about.

---

### Post by cyberslayer on 2011-04-24
> **Arndt said:**
> In theory, doing rand()%n to get uniformly distributed numbers in the range 0..n-1 is fine, but in practice, one has to be careful. There are several random number generators available, and rand is one of the oldest and worst of them. If you do rand()%2, you will get the series 0, 1, 0, 1, 0, 1, 0, etc. Not random at all.

Much better is to take (double)rand()/RAND_MAX to obtain a floating point number in the range 0..1 and then multiply it with something appropriate.

The two other generators I know about that are immediately available are random and drand48.

Actually, using rand() % n introduces a slight bias towards smaller numbers.  This is a separate issue from rand() producing poor quality numbers to begin with and can be solved using something similar to the code posted by NovaAesa.  To see this, suppose that the maximum value returned by rand() is 14.  Then clearly, rand() % 10 will return 0 through 4 more often than 5 through 9.  Making the range of random numbers generated larger does not eliminate this problem; it only makes the bias smaller.

---

### Post by dodle on 2011-04-24
> **NovaAesa said:**
> ...
Try something more like this:
```

int f(int min, int max) {
    r = max - min + 1
    do {
        x = rand();
    } while (x >= (RAND_MAX + 1) / r * r);
    return x % r + min;
}

```

Note that I didn't test my code, it just shows the general idea.

Thanks for the suggestion. I've tested it and it seems to work:

[php] int GetRandInt(int min, int max)
 {
     int x;
     int r = max - min + 1;
     
     do{
         x = rand();
     } while (x >= (RAND_MAX + 1) / r * r);
     
     return x % r + min;
 }[/php]

Although, I don't understand everything that's happening. I'll study it and try to figure out exactly what it does.

> **dwhitney67 said:**
> P.S.  I know, I know... not relevant to the problem the OP was asking about.

Thanks for the suggestion anyway. I was wondering about a better way. You guys must get tired of newbie questions. I hope you find more questions to challenge your intellects in these forums ;).

---

