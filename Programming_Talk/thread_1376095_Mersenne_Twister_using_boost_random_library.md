---
title: "Mersenne Twister using boost random library"
date: 2010-01-08
forum: Programming Talk
---

### Post by pholding on 2010-01-08
I'm looking for some example code that shows how to use the Mersenne twister random number generator function. I've had a look through boost/random/mersenne_twister.hpp but I can't figure out how to run the seed function and then generate a random number between an upper and lower value.
 
Could someone please point me in the right direction. I've searched through the boost documentation and also and google but I can't find anything useful.

---

### Post by mizukiov on 2010-01-08
what are you trying to use it for?

---

### Post by pholding on 2010-01-08
I need the ability to generate random numbers for a C++ program that will perform various simulations. From the research I've done the Mersenne twister algorithm seems to offer a high degree of "randomness" whilst being able to generate the numbers quickly.
 
I'm already using other parts of the boost library in my program so it seemed to make sense to use the boost random library.

---

### Post by TheStatsMan on 2010-01-08
I use the Mersenne Twister from here. It isn't boost but it is well documented

[http://www.agner.org/random/](http://www.agner.org/random/)

---

### Post by mizukiov on 2010-01-08
nvm

---

### Post by pholding on 2010-01-08
Sorry I don't know what a pathos() loop is. Just googled it and I could find anything.
 
I really need to use the Mersenne Twister algorithm for the program I'm working on.

---

### Post by mizukiov on 2010-01-08
lol sorry. best forget that i said that :P

please edit it out of your post.

---

### Post by pholding on 2010-01-09
> **TheStatsMan said:**
> I use the Mersenne Twister from here. It isn't boost but it is well documented
 
[http://www.agner.org/random/](http://www.agner.org/random/)
 
 
Do you know if the libraries on [http://www.agner.org/random]("http://www.agner.org/random/") are thread safe?
 
Edit - Sorry just re-read the descriptions on the website and it says it is thread safe, so please ignore :)

---

### Post by dwhitney67 on 2010-01-09
> **pholding said:**
> 
Could someone please point me in the right direction. I've searched through the boost documentation and also and google but I can't find anything useful.

The boost documentation ranks as one of the worst I have come across.  The boost developers have their brains wrapped around code so much that I believe they have lost touch with how to communicate.

Here's a simple example of the Mersenne Twister generator:
```

#include <boost/random.hpp>
#include <boost/nondet_random.hpp>
#include <ctime>
#include <unistd.h>
#include <iostream>

using namespace boost;
using namespace std;

int main()
{
   mt19937 gen;
   boost::uniform_int<> range(0, 1000);
   boost::variate_generator<boost::mt19937&, boost::uniform_int<> > next(gen, range);


   while (true)
   {
      gen.seed(time(0));   // this is optional, but wise to do

      for (int i = 0; i < 10; ++i)
      {
         int randNumber = next();

         cout << randNumber << " ";
      }
      cout << endl;

      sleep(1);
   }
}

```
I'm probably no better at using boost than you are, so please if you have any further questions, keep them simple!

---

### Post by Barriehie on 2010-01-09
I too am needing an RNG and have ran across */dev/random* and */dev/urandom*.  Since the system entropy affects how fast */dev/random* can generate numbers I'm working on a program to build a 'sliding' pool of numbers.  Granted the generator will have to run for a bit, depending on the number of numbers you need, but once the file is in place it looks promising.

---

