---
title: "[C++] rand() - Same Ten Digits Printed -- Random?"
date: 2010-05-10
forum: Programming Talk
---

### Post by dodle on 2010-05-10
I must be using the [color=red]rand[/color]() function wrong, because every time I run this program, even after recompiling, it prints out the same ten digits:
```
3675356291
```
[php]#include <iostream>
#include <cstdlib>
using namespace std;

class Random
{
  public:
    int getnumber(); // Retrieve a random number
};

int Random::getnumber()
{
  int random = rand() % 10;
  return random;
}

int main()
{
  Random num;
  
  for (int x = 0; x < 10; x += 1)
  {
    cout << num.getnumber(); // Print a random number
    cout.flush(); // Clear output buffer
    usleep(100000); // Wait 1/10 sec between numbers
  }
  cout << endl;
  
  return 0;
}
[/php]Why aren't the numbers randomly chosen each time the program is run?  The compiler seems to predefine the numbers.

---

### Post by Portmanteaufu on 2010-05-10
It turns out that there is no way for a computer to produce a *truly* random number. When asked, computers will use a pre-defined way to produce a number which seems pretty random. Since it uses the same way each time, the result will always be the same unless you give the random number generator a different starting place. We call this "seeding" the random number generator. I believe PHP has a function which will do this. "srand"? Something like that, I think.

Often times you'll want to seed it with the time of day, which is always changing and thus makes it seem like it's actually random.

---

### Post by psusi on 2010-05-10
You didn't use seed().

---

### Post by Queue29 on 2010-05-10
You need to call srand() first. Make sure you call it only once in your program. If you up it in a loop, or in a constructor, you're doing it wrong.

[http://www.cplusplus.com/reference/clibrary/cstdlib/srand/](http://www.cplusplus.com/reference/clibrary/cstdlib/srand/)

---

### Post by dodle on 2010-05-10
Thank you very much.  I had no idea about seeding.

Credit goes to [Grey Wolf](http://cplusplus.com/member/Grey_Wolf/) at cplusplus.com forums for this example:
[php]#include <iostream>
#include <cstdlib>
#include <ctime>
using namespace std;

class Random
{
  public:
    int getnumber(); // Retrieve a random number
private:
    static bool seeded;
};

bool Random::seeded = false;

int Random::getnumber()
{
    if(!seeded)
    {
        srand((unsigned int) time(NULL) );
        seeded = true;
    }
    int random = rand() % 10;
    return random;
}


int main()
{
  Random num;
  
  for (int x = 0; x < 10; x += 1)
  {
    cout << num.getnumber(); // Print a random number
    cout.flush(); // Clear output buffer
    usleep(100000); // Wait 1/10 sec between numbers
  }
  cout << endl;
  
  return 0;
}
[/php]

---

### Post by cyberslayer on 2010-05-10
> **Portmanteaufu said:**
> It turns out that there is no way for a computer to produce a *truly* random number.

Actually, truly random numbers can be obtained by reading from /dev/random.

---

### Post by Tony Flury on 2010-05-11
Generating a know sequence of Random numbers can be a distinct advantage :
[LIST]
[*]Generation of a repeatable but "random" set of test data
[*]Creation of a large set of Random Data from one small value
[/LIST]

The 2nd item is very useful in many games - for instance the creation of a random initial universe, which can be recreated very simply in a totally repeated way, and more importantly you only need to save your seed value - and not the entire universe.
I have a "Galaxy creator" in prototype - which can create (and re-create) many thousands of distninct galaxys (with random star distributions - and eventually star names, technology levels etc) - and all it works on is a single seed value - instead of storing all the data for the galaxy. Start up time might be a bit longer, but data storage is kept small.

---

### Post by Portmanteaufu on 2010-05-11
> **cyberslayer said:**
> Actually, truly random numbers can be obtained by reading from /dev/random.

/dev/random also uses a pre-defined way of producing "random" numbers. To be truly random, there would have to be absolutely no way of predicting what the next number it would spit out would be. If I were to learn the code, I would be able to guess the next number it would spit out every time.

It *is* convenient in that you are not obligated to provide a seed number each time you read from it, however. :)

---

### Post by MadCow108 on 2010-05-11
you'll have a very hard time predicting the numbers from /dev/random as that uses many very good sources including noise from connected devices.
you'd have to monitor the complete system **without** overhead and that is very hard too do.

so /dev/random is strong enough for encryption (unless you're using the infamous flawed debian implementation)
the only drawback is that its slow, so of not much use in statistical studies (but in these a good pseudo generator is almost always enough)

---

### Post by Portmanteaufu on 2010-05-11
> **MadCow108 said:**
> you'll have a very hard time predicting the numbers from /dev/random as that uses many very good sources including noise from connected devices.
you'd have to monitor the complete system **without** overhead and that is very hard too do.

so /dev/random is strong enough for encryption (unless you're using the infamous flawed debian implementation)
the only drawback is that its slow, so of not much use in statistical studies (but in these a good pseudo generator is almost always enough)

Entirely true! :D

I'm not saying that /dev/random is easily predictable. I'm saying that while computers follow a very, very complicated procedure to produce random numbers, they're still following a procedure. If they weren't, there'd be no such thing as seeding.

Most beginners will think that a random number generator is *truly* random. I wanted to make it clear that when a computer sets out to pick a random number, what it ends up providing only has the appearance of randomness.

---

### Post by psusi on 2010-05-11
Actually /dev/random will use hardware random generators if your motherboard has one to generate *truly* random numbers.  The hardware generators do things like measure background cosmic radiation.

---

### Post by Portmanteaufu on 2010-05-11
> **psusi said:**
> Actually /dev/random will use hardware random generators if your motherboard has one to generate *truly* random numbers.  The hardware generators do things like measure background cosmic radiation.

o_O Wow! That would be very impressive. I am assuming you're talking about hardware on computers used by, say, well-funded astrophysics labs? I have yet to see cosmic-radiation-interpreting modules offered on the Asus motherboards I tend to buy. :P

---

### Post by cyberslayer on 2010-05-11
> **Portmanteaufu said:**
> If I were to learn the code, I would be able to guess the next number it would spit out every time.

You would also have to develop a way of modeling the exact physical properties of the hardware for the system in question in order to predict the noise gathered from them by the kernel to generate the random number.  This would be extremely difficult to say the least so /dev/random is close enough to truly random for all practical purposes; it is not periodic like pseudo-random number generators and I doubt anyone would be able to predict the next number.  To have a 100% theoretically unpredictable number generator you would have to use quantum mechanics.

---

### Post by Portmanteaufu on 2010-05-11
> **cyberslayer said:**
> This would be extremely difficult to say the least so /dev/random is close enough to truly random for all practical purposes.

Yup! I can't imagine ever running into a scenario in which I needed something more random than /dev/random.

---

