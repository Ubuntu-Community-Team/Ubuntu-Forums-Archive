---
title: "Need help for a little c++ script about Gauss conjecture"
date: 2013-02-05
forum: Programming Talk
---

### Post by iMac71 on 2013-02-05
I wrote, in several steps, this piece of code in C++ for testing the Gauss conjecture about prime numbers.
I've come to a point beyond which I don't know what I should do to better structurize and to optimize the code (assuming that it be already sufficiently structured and optimized, but I'm not sure about all this).
Could anyone give me some tip and/or trick about to better structurize the code and/or to optimize it? Please don't pay too much attention to variable names: I don't know English very well, thus some names might seem weird or mistyped.
[PHP]#include <iostream>
#include <cmath>
#define NOT_FOUND 4294967295
using namespace std;

unsigned long getStartingValue ()
{
    unsigned long startingValue;
    do
    {
        cout << "Enter a positive integer greater than 2: ";
        cin >> startingValue;
        cout << endl;
    } while (startingValue <= 2);
    return startingValue;
}

bool isPrime (unsigned long guessPrime)
{
    if (guessPrime % 2 == 0) return false;
    unsigned long intSqrt_guessPrime = ceil(sqrt(guessPrime));
    for (unsigned long i = 3; i <= intSqrt_guessPrime; i += 2)
        if (guessPrime % i == 0) return false;
    return true;
}

unsigned long primeSearch (unsigned long intNum)
{
    unsigned long intSqrt_intNum = ceil(sqrt(intNum));
    unsigned long leftGuess, rightGuess;
    for (unsigned long delta = 1; delta <= intSqrt_intNum; delta++)
    {
        leftGuess = intNum - delta;
        if (isPrime(leftGuess)) return leftGuess;
        rightGuess = intNum + delta;
        if (isPrime(rightGuess)) return rightGuess;
    }
    return NOT_FOUND;
}

int main ()
{
    cout << "* Gauss conjecture about prime numbers *" << endl;
    unsigned long intNum = getStartingValue();
    if (isPrime(intNum)) cout << intNum << " is prime. Gauss conjecture is verified." << endl;
    else
    {
        unsigned long guessPrime = primeSearch(intNum);
        if (guessPrime == NOT_FOUND) cout << "Gauss conjecture verification failed." << endl;
        else cout << guessPrime << " is prime. Gauss conjecture is verified." << endl;
    }
    return 0;        
}[/PHP]

---

