---
title: "[C++] (Referencing?) variables  declared/defined in one function in another function"
date: 2011-08-31
forum: Programming Talk
---

### Post by MechWarrior001 on 2011-08-31
Hey, long time no see. I've recently started taking a C++ class and our assignment is to create a basic number guessing game for our first lab. So far I think I've got it down, but there's one thing I'm confused how to do. I'm using functions to organize my code, and place definitions for various variables. But I'm not sure how to make one variable defined in one function available in another function. For example:

```

// Initialize the Random Number Generator. Does this thing even work?
int RandomNumber(short int randomNumber)
{
  //short int randomNumber;

  /* initialize random seed: */
  srand ( time(NULL) );

  /* generate secret number: */
  randomNumber = rand() % 10 + 1;
}

```

I've defined the integer variable *randomNumber* here, and I would like to reference, or call, or use it (Whatever the correct term is for it, haven't memorized them yet) here:

```

int CPUPlayer()
{
    const short int cpuGuess = randomNumber;
}

```

How would I "forward" the definition of *randomNumber *from RandomNumber() to CPUPlayer()?

---

### Post by gnometorule on 2011-08-31
(1) Your functions don't return their values promised (int). They shouldn't even compile, or at least compile with warnings.

(2) To not do your hw for you, and so you also learn something, in C/C++ you can, among others, use variables created in one function in another by using any of the following that you should find in your text book or by googling or on the ubuntu web pages someplace:

(a) Declare the variable on the heap (using new (C++) or malloc (C) style functions. don't forget to clean up after).

(b) Make the variable global or static (static, for what you intend to do, is probably not what you want; and global might also not be).

(c) Hand it on: if you want to hand on a variable to a function, hand on a pointer to it, or hand it on by reference, among the other function arguments. Make sure what you hand on and off is 'in scope.'

Gl!

---

### Post by Longinus00 on 2011-08-31
There's lots of ways to do what you're asking (ask your professor/TA about variable scope to explain why what you're doing doesn't work) but why not just generate the random number when you need it? Do you need to use the same value in multiple places?

---

### Post by Senesence on 2011-08-31
> **gnometorule said:**
> (a) Declare the variable on the heap (using new (C++) or malloc (C) style functions. don't forget to clean up after).

...

(c) Hand it on: if you want to hand on a variable to a function, hand on a pointer to it, or hand it on by reference, among the other function arguments. Make sure what you hand on and off is 'in scope.'

Just to make it clear: you'll need to have an address to any piece of memory that you allocate on the heap, if you actually plan to use it in the future (and you will, because you'll have to at least free it if nothing else).

So, in that sense, allocating on the heap is not really a valid "method" to "forward data" from one function to the other - passing to, and returning from functions, via pointer, value, or reference; that's a valid method. Declaring a global variable is an alternative, but I think it's ill advised in this, and most other cases.

---

### Post by Bachstelze on 2011-08-31
> **gnometorule said:**
> (1) Your functions don't return their values promised (int). They shouldn't even compile, or at least compile with warnings.


The returned value has type short int, which can be losslessly converted to int. This compiles perfectly fine without warning. Neither C nor C++ is that strongly typed.

*EDIT:* And in the reverse case, where the conversion is not lossless, it compiles without warnings as well.

---

### Post by MechWarrior001 on 2011-08-31
> **gnometorule said:**
> 
(1) Your functions don't return their values promised (int). They shouldn't even compile, or at least compile with warnings.


The snippets I've shown you are only pieces of the program, not the whole thing. Then again I'm pretty new to C++ so I'm probably gonna get a few warnings.

> **gnometorule said:**
> 
(2) To not do your hw for you...


Don't worry, I'm not asking you to. I was just curious how to do this specific task. As a whole, the class has not learned about Functions yet. However, previously I had done some self-studying and therefore I already know, to a limited extent, how to use functions, so I decided to use them to help keep my code organized. But as you can see, this presents the problem of passing on variables and their values of one function to another, which is what I'm asking how to do.

> **gnometorule said:**
> 
(a) Declare the variable on the heap (using new (C++) or malloc (C) style functions. don't forget to clean up after).

(b) Make the variable global or static (static, for what you intend to  do, is probably not what you want; and global might also not be).


The class, as a whole, just recently started and we are still in Chapter 1.2. I think those methods are a bit beyond the scope of my abilities at the moment.

> **gnometorule said:**
> 
(c) Hand it on: if you want to hand on a variable to a function, hand on a pointer to it, or hand it on by reference, among the other function arguments. Make sure what you hand on and off is 'in scope.'


I'm not sure how to do that. What topic (in the book) do you think it would be located under?

> **Longinus00 said:**
> There's lots of ways to do what you're asking (ask your professor/TA about variable scope to explain why what you're doing doesn't work) but why not just generate the random number when you need it? Do you need to use the same value in multiple places?

Currently I do not think I will need to use the same value in multiple places, but the primary reason I'm using, or would like to use a separate function for the RNG is for organization and to make it easier for me to find it and modify it as needed.

---

### Post by gnometorule on 2011-08-31
@BS:

I actually had never tried compiling it this way, and learned something here. However, in the above form, the function 'returns' merely garbage, at least on my system...

```

#include <stdio.h>

int CPUPlayer()
{
    const short int cpuGuess = 6;
}

int CPUPlayer2()
{
    const short int cpuGuess = 6;
    return cpuGuess;
}

int main(){
  int i;

  i = CPUPlayer();
  printf("%d\n", i);
  i = CPUPlayer2();
  printf("%d\n", i);

  return 0;
}
----------
-1075512108
6

```

I know you know that, BS but poster might not.

P.S.: I remember on occasion getting warnings that some return paths do not 'return' values. When does that happen - as the above compiles warning and error free, as you pointed out?

---

### Post by gnometorule on 2011-08-31
@Mechwarrior:

If you just want to get done with it, the easiest (not best way for sure) is to make all such variables global. Your program will look like this (in C):

#include <stdio.h>
(more includes)

int myglobalvar1;
double my globalvar2;
(more global vars)

(function declarations/definitions)

main

(more function definitions)

Variables are accessible after they have been declared for the rest of the program. So you can use all your myglobalvar's everywhere. This contradicts ideas such as encapsulation and modularity, and so isn't usually what you want to do. But it should work.

Edit: This assumes your entire program is in one file, as seems likely for an early learning exercise.

---

### Post by Bachstelze on 2011-08-31
> **gnometorule said:**
> @BS:

I actually had never tried compiling it this way, and learned something here. However, in the above form, the function 'returns' merely garbage, at least on my system...



Oh sorry, I had overlooked the fact that there is *no* return statement in the function, as opposed to returning the short int. It will compile with a warning if you use -Wall (and this is why you should always use it, because otherwise it will let you do some very stupid things).

---

### Post by gnometorule on 2011-08-31
@Mechwarrior:

I missed your second question: for C++, the key phrase to look up would be 'call by reference,' which also is probably the preferred way to do it.

---

### Post by MechWarrior001 on 2011-08-31
Ok, so this is what I have so far, I think I'm doing it correctly:

```

// These includes define several functions and commands and allow proper execution
#include <iostream>
#include <cstdlib>
#include <ctime>
#include <string>

using namespace std;

// Initialize the Random Number Generator. Does this thing even work?
int RandomNumber()
{

  // Allocate space for the randomized number.
  short int randomNumber;

  /* initialize random seed: */
  srand ( time(NULL) );

  /* generate secret number: */
  randomNumber = rand() % 10 + 1;
  return 0;
}

// Ask the player for His or Her name, then store it in memory.
char Playername()
{
    char playerName;
    cout << "Please enter your name:" << endl;
    cin >> playerName;
    cout << "You entered " << playerName << "." << endl;
    return 0;
}

// Give the CPU player a custom variable and fill it with the RNG output so we never have to use the randomNumber variable again.
int CPUPlayer(short int& randomNumber)
{
    short int cpuGuess = randomNumber;
}

// Give the Human player a custom variable.
int Playerguess()
{
    short int playerGuess;
}

int HMNvCPUComparison(short int& cpuGuess, short int& playerGuess)
{
    if (playerGuess == cpuGuess)
        {
            cout << "Congradulations. You win." << endl;
        }
    if (playerGuess != cpuGuess)
        {
            cout << "Sorry. Try again." << endl;
        }
    return 0;
}

int RevealNumber(short int& cpuGuess, short int& playerGuess)
{
    cout << "Your number was: " << playerGuess << endl;
    cout << "The computers number was: " << cpuGuess << endl;
    return 0;
}

int main(short int& playerGuess)
{
    Playername();
    cout << "The CPU has challenged you to guess the number it is holding in memory." << endl;
    cout << "What is your guess?" << endl;
    cin    >> playerGuess;
    HMNvCPUComparison();
    RevealNumber();
}

```I'm using MS Visual Studio 2010 Professional (Got it through their Dreamspark program) and the output is giving me the error that HMNvCPUComparison() and RevealNumber() "does not take 0 arguments." I'm a bit confused as to what it means, and I'm unsure how any of the previous code could have caused it to say that. Did I forget something?

---

### Post by Bachstelze on 2011-08-31
HMNvCPUComparison takes two arguments, but you are calling it with zero.

---

### Post by MechWarrior001 on 2011-08-31
Ok, so I fixed the no-arguments problem, but now I'm getting a unhandled exception, which I have absolutely no idea how to deal with. It happens after I input a number and the program proceeds to the HMNvCPUComparison() function; specifically, it breaks at the if (playerGuess == cpuGuess) statement. I'm starting to wonder if I'm just generally doing this wrong. Perhaps I'm using the wrong variable type?

---

### Post by Longinus00 on 2011-08-31
> **MechWarrior001 said:**
> Ok, so I fixed the no-arguments problem, but now I'm getting a unhandled exception, which I have absolutely no idea how to deal with. It happens after I input a number and the program proceeds to the HMNvCPUComparison() function; specifically, it breaks at the if (playerGuess == cpuGuess) statement. I'm starting to wonder if I'm just generally doing this wrong. Perhaps I'm using the wrong variable type?

Have you covered variable scope in your lectures/reading? If you have PLEASE review the material. If you haven't then let us know. Honestly I'm a little surprised your program compiles at all.

---

### Post by dwhitney67 on 2011-08-31
See my comments below within the code...

> **MechWarrior001 said:**
> Ok, so this is what I have so far, I think I'm doing it correctly:

```

// These includes define several functions and commands and allow proper execution
#include <iostream>
#include <cstdlib>
#include <ctime>
#include <string>

using namespace std;

// Initialize the Random Number Generator. Does this thing even work?
int RandomNumber()
{

  // Allocate space for the randomized number.
  short int randomNumber;

  /* initialize random seed: */
  srand ( time(NULL) );

  /* generate secret number: */
  randomNumber = rand() % 10 + 1;  [COLOR="Blue"]**// This computation is lost when the function returns**[/COLOR]
  return 0;   [COLOR="Blue"]**// why return 0?**[/COLOR]
}

// Ask the player for His or Her name, then store it in memory.
char Playername()
{
    char playerName;  [COLOR="Blue"]**// is your intent to store only ONE character for the name??**[/COLOR]
    cout << "Please enter your name:" << endl;
    cin >> playerName;
    cout << "You entered " << playerName << "." << endl;
    return 0;  [COLOR="Blue"]**// playerName is lost when function returns; why return 0?**[/COLOR]
}

// Give the CPU player a custom variable and fill it with the RNG output so we never have to use the randomNumber variable again.
int CPUPlayer(short int& randomNumber)
{
    short int cpuGuess = randomNumber;  [COLOR="Blue"]**// an assignment; for what??**[/COLOR]
}

// Give the Human player a custom variable.
int Playerguess()
{
    short int playerGuess;  [COLOR="Blue"]**// a declaration; for what??**[/COLOR]
}

int HMNvCPUComparison(short int& cpuGuess, short int& playerGuess)
{
    if (playerGuess == cpuGuess)
        {
            cout << "Congradulations. You win." << endl;
        }
    if (playerGuess != cpuGuess)  [COLOR="Blue"]**// use else, not another if**[/COLOR]
        {
            cout << "Sorry. Try again." << endl;
        }
    return 0;   [COLOR="Blue"]**// what's the point of always returning 0??**[/COLOR]
}

int RevealNumber(short int& cpuGuess, short int& playerGuess)
{
    cout << "Your number was: " << playerGuess << endl;
    cout << "The computers number was: " << cpuGuess << endl;
    return 0;  [COLOR="Blue"]**// what's the point of returning a value??**[/COLOR]
}

int main(short int& playerGuess)  [COLOR="Blue"]**// generates compiler warning**[/COLOR]
{
    Playername();
    cout << "The CPU has challenged you to guess the number it is holding in memory." << endl;
    cout << "What is your guess?" << endl;
    cin    >> playerGuess;
    HMNvCPUComparison();   [COLOR="Blue"]**// you are not passing any parameters!!**[/COLOR]
    RevealNumber();   [COLOR="Blue"]**// again, no parameters are passed**[/COLOR]
}

```

In conclusion, you are not doing things correctly.  Refer to Chapter 1 of your book with respect to how to declare the main() function.  Then proceed to read about how to declare and call functions.

The code you have above is indicative of someone who spent a fleeting moment perusing some book or tutorial, without paying careful attention to detail.  Real pathetic.

---

### Post by Arndt on 2011-08-31
> **MechWarrior001 said:**
> Hey, long time no see. I've recently started taking a C++ class and our assignment is to create a basic number guessing game for our first lab. So far I think I've got it down, but there's one thing I'm confused how to do. I'm using functions to organize my code, and place definitions for various variables. But I'm not sure how to make one variable defined in one function available in another function. For example:

```

// Initialize the Random Number Generator. Does this thing even work?
int RandomNumber(short int randomNumber)
{
  //short int randomNumber;

  /* initialize random seed: */
  srand ( time(NULL) );

  /* generate secret number: */
  randomNumber = rand() % 10 + 1;
}

```

I've defined the integer variable *randomNumber* here, and I would like to reference, or call, or use it (Whatever the correct term is for it, haven't memorized them yet) here:

```

int CPUPlayer()
{
    const short int cpuGuess = randomNumber;
}

```

How would I "forward" the definition of *randomNumber *from RandomNumber() to CPUPlayer()?

This is not an answer to your question, but you should not call srand for each number, you should call it only once in the whole program.

Besides, doing rand() % 10 does not give you as random numbers as you may think - there are better generators and better ways to use rand.

---

### Post by dwhitney67 on 2011-08-31
> **Arndt said:**
> 
Besides, doing rand() % 10 does not give you as random numbers as you may think - there are better generators and better ways to use rand.

If someone is working on a scientific programming application, I would agree with you.  However if they are working with a pet project, or even a school project, where a deck of 52-cards has to be shuffled, rand() works just fine as long as srand() is seeded with a sufficiently large number.

In the case of the OP, he needs to learn to "walk" first, then worry about better randomization techniques at a later time, _should_ the need ever arise.  So far in my 20+ year career of s/w development, it has not not.

---

### Post by Arndt on 2011-08-31
> **dwhitney67 said:**
> If someone is working on a scientific programming application, I would agree with you.  However if they are working with a pet project, or even a school project, where a deck of 52-cards has to be shuffled, rand() works just fine as long as srand() is seeded with a sufficiently large number.

In the case of the OP, he needs to learn to "walk" first, then worry about better randomization techniques at a later time, _should_ the need ever arise.  So far in my 20+ year career of s/w development, it has not not.

What you say is true, but there is a non-negligible risk that the teacher also doesn't know this.

Besides, if I remember the behaviour of rand correctly, doing rand() % 10 will give a sequence of odd, even, odd, even, odd, even, and so on. Would you want that behaviour? The requirements for randomness are really mild if that code is at all OK. I haven't dealt with the need for high-quality random numbers either, but I don't think I would consider such results acceptable for my occasional purposes.

---

### Post by dwhitney67 on 2011-08-31
> **Arndt said:**
> What you say is true, but there is a non-negligible risk that the teacher also doesn't know this.

Besides, if I remember the behaviour of rand correctly, doing rand() % 10 will give a sequence of odd, even, odd, even, odd, even, and so on. 
This is not true.

For example:
```

#include <ctime>
#include <cstdlib>
#include <iostream>

int main()
{
   srand(time(0));
   for (int i = 0; i < 10; ++i)
   {
      std::cout << rand() % 10 << " ";
   }
   std::cout << std::endl;
}

```
yields:
```

$ ./a.out
7 0 0 6 2 6 4 2 7 1 
$ ./a.out
8 7 1 6 5 2 6 8 8 9 
$ ./a.out
5 0 3 0 4 9 8 6 4 2

```
Because a small pool of numbers (ie ranging from 0 through 9) is being sought, obviously the chance of seeing a duplicate result are higher.  The results of drawing numbered balls from a bag (with replacement), will probably be no more random than what the code produced above.

---

### Post by Arndt on 2011-08-31
> **dwhitney67 said:**
> This is not true.

For example:
```

#include <ctime>
#include <cstdlib>
#include <iostream>

int main()
{
   srand(time(0));
   for (int i = 0; i < 10; ++i)
   {
      std::cout << rand() % 10 << " ";
   }
   std::cout << std::endl;
}

```
yields:
```

$ ./a.out
7 0 0 6 2 6 4 2 7 1 
$ ./a.out
8 7 1 6 5 2 6 8 8 9 
$ ./a.out
5 0 3 0 4 9 8 6 4 2

```
Because a small pool of numbers (ie ranging from 0 through 9) is being sought, obviously the chance of seeing a duplicate result are higher.  The results of drawing numbered balls from a bag (with replacement), will probably be no more random than what the code produced above.

Interesting. Thanks for providing a counterexample to my statement. It was definitely the case on some Unix platforms that the low bits changed cyclically with rand, this was long known, and I thought it was still the case, so I didn't think I had to check. Someone with enough experience is well served by knowing this, but a beginner should not be bothered with portability and historic issues on top of everything else new he has to learn.

---

### Post by MechWarrior001 on 2011-08-31
[QUOTE=Longinus00]
Have you covered variable scope in your lectures/reading? If you have PLEASE review the material. If you haven't then let us know.
[/QUOTE]

For course material, we are using *Absolute C++ 4th Edition* by *Walter Savitch*, and we are only on Chapter 1.2, and so to my current knowledge, no we have not covered variable scopes yet, unless I missed something.

[QUOTE=dwhitney67][COLOR=Blue][B][FONT=monospace]
//[/FONT]why return 0?[/B][/COLOR]
[/QUOTE]

Because the compiler told me I needed to have those functions return a value, and currently that is the only way I know how to do it. Whenever I remove the return commands, I get Error C4716 from the compiler, complaining that function-in-question needs to return a value.

[QUOTE=Arndt]
Besides, doing rand() % 10 does not give you as random numbers as you may think - there are better generators and better ways to use rand. 
[/QUOTE]

[QUOTE=dwhitney67]
If someone is working on a scientific programming application, I would agree with you. However if they are working with a pet project, or even a school project, where a deck of 52-cards has to be shuffled, rand() works just fine as long as srand() is seeded with a sufficiently large number.

In the case of the OP, he needs to learn to "walk" first, then worry about better randomization techniques at a later time, should the need ever arise. So far in my 20+ year career of s/w development, it has not not. 
[/QUOTE]

[QUOTE=Arndt]
What you say is true, but there is a non-negligible risk that the teacher also doesn't know this.

Besides, if I remember the behavior of rand correctly, doing rand() % 10 will give a sequence of odd, even, odd, even, odd, even, and so on. Would you want that behavior? The requirements for randomness are really mild if that code is at all OK. I haven't dealt with the need for high-quality random numbers either, but I don't think I would consider such results acceptable for my occasional purposes. 
[/QUOTE]

The teacher, or Professor if you will, literally had a example source file with the srand command in it and told us to use that for our number generation scheme. I'm just doing what he told me to use.

---

### Post by Longinus00 on 2011-08-31
Has your course covered functions but not variable scope?

The website for the book [1] shows it doesn't cover functions until chapter 3. If you haven't covered functions in the course yet then don't use them in your program.


1.
[http://www.pearsonhighered.com/educator/product/Absolute-C/9780136083818.page](http://www.pearsonhighered.com/educator/product/Absolute-C/9780136083818.page)

---

### Post by muteXe on 2011-08-31
Your compiler is telling you that your functions have to return something because YOU have told the compiler that your function will return something! If you don't want to return anything use void rather than int.

---

