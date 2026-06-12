---
title: "rand() seeding (c++)"
date: 2010-02-26
forum: Programming Talk
---

### Post by YourMomsASmurph on 2010-02-26
[Additional Question at bottom]

So, im attemping to seed random numbers with time.. sounds simple enough, but it seems seeding rand with any value causes it to output constant numbers. (tested with constants as well)

Code and output are printed below.


CODE:

[PHP]
#include <iostream>
#include <cstdlib>
#include <ctime>

using namespace std;

int main () {
-----------------------------------
code that uses value and outputs it.
-----------------------------------
}

int getRandomNumber() 
{
    int rndm;
    srand((unsigned)time(NULL));
    rndm=100*(rand()/(double)RAND_MAX);
    return rndm;
}
[/PHP]5 Outputs of rndm

```

38 
38 
38 
38 
38 

```Second attempt.

```
39
39
39
39
39
```and it keeps doing this, increased every few seconds by 1 (assuming its increasing with time)

It remains constand if seeding with a constant number.


[Are there any better free c++ IDEs than Dev Cpp? --> Something like XCODE(MAC), or Anjunta(Linux)]



Solved -->>Thx Simon.

---

### Post by Simon17 on 2010-02-26
You only use srand() once in your program and use rand() each time you want a new random number. If you keep on calling srand(), your random seed gets reset and you'll get the same numbers from rand().



Dev-cpp is pretty outdated. Code::Blocks is pretty good.

---

