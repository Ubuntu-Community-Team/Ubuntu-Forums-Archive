---
title: "multinomial formula"
date: 2009-02-22
forum: Programming Talk
---

### Post by diamantis13 on 2009-02-22
Hi!,
I would like to compute the multinomial formula (see [http://en.wikipedia.org/wiki/Multinomial_theorem#Theorem]("http://en.wikipedia.org/wiki/Multinomial_theorem#Theorem")):
[IMG]http://upload.wikimedia.org/math/8/a/2/8a21d051dca679f6e83e8671310ebd0a.png[/IMG],
As input I have the variables x1,x2...xm and the variable n (Initially I am interested in the case where n = 2).
I cannot figure out how to do the summation over all k1,k2...km, although there must be some simple (or not so simple) way!
Any ideas???
Thanks!!!

P.S. I need to find a way of computing this as I am trying to simulate in C++ of an evolving population

---

### Post by monkeyking on 2009-02-22
look into integer partition
[http://en.wikipedia.org/wiki/Integer_partition](http://en.wikipedia.org/wiki/Integer_partition)

Do you need the exact or just close enough?
I remember some recursion formula from my math classes for multinomials, for smaller numbers that should be ok.

Or just to check that it actually works :)

---

### Post by croto on 2009-02-22
Hey, how about something like this?
```

#include<iostream>

using namespace std;

main(){

  int m,n;
  cout << "Values for m, n:";
  cin >> m >> n;

  int* k = new int[m];


  // loop!

  // initialize k[0]...k[m] to 0
  for(int i=0; i<m; i++) k[i]=0;
  while (true) {
    // do whatever you wanna do (in this case, just print indices)
    for(int i=0; i<m; i++) cout << k[i] << " "; cout << endl;

    // increment indices
    k[0]++;
    for(int i=0; i<m-1; i++) 
      if(k[i] >= n) {
	k[i] = 0;
	k[i+1]++;
      }
      else break;
    
    // if we're done, exit loop
    if(k[m-1] >= n) break;
  }

  // end loop
}

```

probably it's not the best (most efficient) way, but it works.

---

### Post by c174 on 2009-02-22
I don't really get the problem... If you need to evaluate ( x1 + x2 + ... )^k you could simply use

```
double value = pow( x1 + x2 + ... , k );
```

---

### Post by diamantis13 on 2009-02-22
> **c174 said:**
> I don't really get the problem... If you need to evaluate ( x1 + x2 + ... )^k you could simply use

```
double value = pow( x1 + x2 + ... , k );
```
I need to find the value of ( x1 + x2 + ... )^k as well as of each of the different (n!/(k1!*k2!...km!))(x1^k1*x2^k2...xm^km).

monkeyking, croto thanks for the suggestions, I will see what I can do as soon as I wake up!

---

### Post by diamantis13 on 2009-02-22
croto the code you gave is not exactly what I was looking for.
I did some more homework and I now have an outline of the algorithm I need, but still I do not know how to do some parts of it.

Input: a vector: (x1,x2,...xm) and an integer n
Algorithm:
[LIST=1]
[*]Find all the partitions of m (the ways in which integers add up to m)
e.g. for m=3:
partition 1: 3
partition 2: 1+2
partition 3: 1+1+1
[*]For each partition, add zeros until the length is m and find all permutations with repetition.
continuing the previous example:
partition 1:
3,0,0
0,3,0
0,0,3
partition 2:
1,2,0
1,0,2
0,1,2
2,1,0
2,0,1
0,2,1
partition 3:
1,1,1
[*]use the permutations to compute each n!/(k1!*k2!...km!)*x1^k1*x2^k2...xm^km and add up to find the sum
[/LIST]
Now I am trying to find an algorithm for getting **all the partitions of a vector** and **permutations with repetition**. Anyone done something similar???
This task is much more complicated than I thought when I started!

---

### Post by gmatt on 2009-02-22
> **diamantis13 said:**
> I need to find the value of ( x1 + x2 + ... +xm)^n as well as of each of the different (n!/(k1!*k2!...km!))(x1^k1*x2^k2...xm^km).

monkeyking, croto thanks for the suggestions, I will see what I can do as soon as I wake up!

If n is large then calculating the coefficients the naive way by evaluating all the factorials and dividing multiplying will be extremely slow and probably won't finish before the end of the universe.

Let me outline what I think would be a good way to go about implementing this. 

1) First figure out a way that will evaluate a coefficient for any value of n, k1 ...km efficiently, don't be afraid to use recursion or reusing any previous work you have done, there is a lot of symmetry in this problem to be exploited.

2) After you have done step one in a "smart" way you will find summing over all the indicies a trivial thing. In fact you can just use the pow function instead and probably finish this a lot quicker than summing. 

-----------

Ok so I would recommend making some observations about this problem before you even write your first line of code. 

Observations:

-each coeff can be written as n!/(k1!...km!); note that the values of ki and kj  for any 1<=i<j<=n can be interchanged in the ceoff without altering the result. Lets consider a vector k = (k1, .., km) amd consider the function c(k) = n!/(k1!...km!)  this means that for example c(2,1,3)=c(1,2,3)=c(3,2,1)=c(2,3,1)=c(1,3,2)=c(3,1,2). This means we can reuse a lot of the previous work.
-in the coeff function c defined above and a vector k as defined above we should look for the largest element of k. by the previous observation of the order of the elements in k is irrelevant, so if we can find the biggest element than we can eliminate the most terms in the calculation of n! (which is EXTREMELY costly).
-the sum of the elements of x must be = n (I think you realized this with your partition observation in the previous post). This is useful because then we are guaranteed that the largest element of k >= n/m. Of course the larger the element the better.
-the main problem is after dividing out the largest element of k from n! what do we do with the left over terms in the denominator ki? They are not going to necessarily cancel with any way with the left over terms in the numerator. This is the interesting part that needs to be figured out I will think on it, but I have homework to do now....

---

### Post by croto on 2009-02-22
A few changes and now I think it does what you need. However, it's very slow. If I think of something better I'll let you know.

```

#include<iostream>

using namespace std;

main(){

  int m;
  cout << "Value for m:";
  cin >> m;

  int* k = new int[m];

  // loop!

  // initialize k[0]...k[m] to 0
  for(int i=0; i<m; i++) k[i]=0;
  while (true) {
    // if it's a good set of parameters, do whatever you wanna do 
    // (in this case, just print indices), else proceed directly
    // to increment indices
    
    int idx, idxsum;
    for(idx=0, idxsum=0; (idx<m) && (idxsum<=m); idx++) idxsum += k[idx];

    if(idxsum==m) {
      // good set!
      for(int i=0; i<m; i++) cout << k[i] << " "; cout << endl;
    }

    // increment indices
    k[0]++;
    for(int i=0; i<m-1; i++) 
      if(k[i] > m) {
	k[i] = 0;
	k[i+1]++;
      }
      else break;
    
    // if we're done, exit loop
    if(k[m-1] > m) break;
  }

  // end loop
}

```

---

### Post by croto on 2009-02-22
A somewhat faster algorithm:
```

#include<iostream>

using namespace std;

void partition(int i, int m, int* k, int sum, void (*func)(int,int*)){
  if(i == m-1) { // last one
    k[i] = m-sum;
    func(m,k);
    return;
  }

  // not the last one
  for(int idx=0;idx<=m-sum;idx++) {
    k[i] = idx;
    partition(i+1, m, k, sum+idx, func);
  }
}



void printks(int m, int* k){
  for(int i=0;i<m;i++) cout << k[i] << " ";  cout<<endl;
}


main(){
  int m;
  cout << "Enter value for m: ";
  cin >> m;
  int* k = new int[m];
  partition(0, m, k, 0, printks);

}

```

---

