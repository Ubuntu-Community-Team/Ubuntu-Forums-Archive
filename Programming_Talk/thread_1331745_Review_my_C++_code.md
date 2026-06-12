---
title: "Review my C++ code?"
date: 2009-11-19
forum: Programming Talk
---

### Post by Muffinabus on 2009-11-19
Amateur programmer here, have been taking a C++ course this semester and I am kind of wondering where I stand in my writing and style skills.  Since it is an intro course, I haven't learned too much yet, so just keep that in mind.  But if you could please review my most recent homework assignment (I've already turned it in, I'm not looking for help on it, it works exactly as the assignment describes), mainly wishing to be critiqued on style and method.

A few questions though:

Does my code look readable?  I try to minimize whitespace as much as possible and don't insert any extra lines where they aren't needed, is this acceptable?

Some of my classmates use lots of functions.  For instance, there were a couple of them that would use five or even six functions in the same exact program, where I usually only use one.  Would that be good programming?  To me, it seemed unnecessary to complicate the code so much for such a simple task, so most of mine is written in main, and even my one function could be questioned about its necessity.

Also, the assignment specified that you use an enumerator to complete the task, that's as far as we have gotten in programming concepts so far - we just learned structured data types.

Assignment:
"The following table gives the factor by which the weight must be multiplied for each planet.  The program should consist of an error message if the user doesn't input a correct planet name.  The prompt and the error message should make it clear to the user how a planet name must be entered.  Be sure to use proper formatting and appropriate comments in your code.  The output should be labeled clearly and formatted neatly."

The planet values are in my program, so I won't rewrite them.

```
#include <iostream>
#include <string>
#include <cctype>
using namespace std;
//constants, enumerations, and functions
const double MER = 0.4155;
const double VEN = 0.8975;
const double EAR = 1.0;
const double MOO = 0.166;
const double MAR = 0.3507;
const double JUP = 2.5374;
const double SAT = 1.0677;
const double URA = 0.8947;
const double NEP = 1.1794;
const double PLU = 0.0899;
enum Planets {MERCURY, VENUS, EARTH, MOON, MARS, JUPITER, SATURN, URANUS, NEPTUNE, PLUTO, DEFAULT};
Planets findPlanet(string);
int main() {
  //local vars
  int weightInd = -1;
  double weight = 0;
  string planet;
  //ask for weight
  cout << "Enter your weight in pounds: " << endl;
  cin >> weight;
  //check to see if the in stream fails
  if (!cin) {
    cout << "CRITICAL ERROR: Weight needs to be a numerical value." << endl
      << "Exiting Program..." << endl;
    system("pause");
    return 1;
  }
  do {
    //list of planets
    cout << "Enter one of the following planets: " << endl << "Mercury" 
      << endl << "Venus" << endl << "Earth" << endl << "Moon" << endl 
      << "Mars" << endl << "Jupiter" << endl << "Saturn" << endl 
      << "Uranus" << endl << "Neptune" << endl << "Pluto" << endl;
    cin >> planet;
    cout << endl;
    //coerce the enum value into weightInd to act as a loop sentinel
    weightInd = findPlanet(planet);
    cout << "Your weight is ";
    //call the findPlanet function and figure out the weight
    switch (findPlanet(planet)) {
      case MERCURY : cout << weight*MER << ' ';
                     break;
      case VENUS   : cout << weight*VEN << ' ';
                     break;
      case EARTH   : cout << weight*EAR << ' ';
                     break;
      case MOON    : cout << weight*MOO << ' ';
                     break;
      case MARS    : cout << weight*MAR << ' ';
                     break;
      case JUPITER : cout << weight*JUP << ' ';
                     break;
      case SATURN  : cout << weight*SAT << ' ';
                     break;
      case URANUS  : cout << weight*URA << ' ';
                     break;
      case NEPTUNE : cout << weight*NEP << ' ';
                     break;
      case PLUTO   : cout << weight*PLU << ' ';
                     break;
      default      : cout << "\n\nERROR: Did not recognize planet name, try again." 
                       << endl << endl;
                     weightInd = -1;
                     break;
    }
  } while ((weightInd <= -1)||(weightInd >= 10));
  cout << "lbs" << endl;
  system("pause");
  return 0;
}
//findPlanet function of type enum Planets with string variable
Planets findPlanet(string planetName) {
  switch (toupper(planetName.at(0))) {
    case 'M' : if (planetName.length() >= 2) {
                 if (toupper(planetName.at(1)) == 'A')
                   return MARS;
                 else if (toupper(planetName.at(1)) == 'E')
                   return MERCURY;
                 else if (toupper(planetName.at(1)) == 'O')
                   return MOON;
                 else
                   return DEFAULT;
               }
               else
                 return DEFAULT;
               break;
    case 'V' : return VENUS;
               break;
    case 'E' : return EARTH;
               break;
    case 'J' : return JUPITER;
               break;
    case 'S' : return SATURN;
               break;
    case 'U' : return URANUS;
               break;
    case 'N' : return NEPTUNE;
               break;
    case 'P' : return PLUTO;
               break;
    default  : return DEFAULT;
  }
}
```

I appreciate any help or comments (:

Also, if you want to write the program the way *you* would do it, I could see that helping me as well to see how people with more knowledge and experience would complete the same task.

Thanks!

---

### Post by denago on 2009-11-19
I'd recommend reading the book [Code Complete](http://www.amazon.com/Code-Complete-Practical-Handbook-Construction/dp/0735619670/ref=sr_1_1?ie=UTF8&s=books&qid=1258666959&sr=8-1).

But for a more direct answer to your questions, here goes

> I try to minimize whitespace as much as possible and don't insert any extra lines where they aren't needed, is this acceptable?

You should definitely use more whitespace than you are.

> To me, it seemed unnecessary to complicate the code so much for such a simple task, so most of mine is written in main, and even my one function could be questioned about its necessity.
Don't look at functions as something that complicates code, look at them as something that simplifies code.  You definitely should break your program down in to more functions than you have.  Read up [here](http://www.stevemcconnell.com/cchqsub.htm) for a good idea of when you should be creating functions.  Especially this section:

> 
**Making a section of code readable**. Putting a section of code into a well-named routine is one of the best ways to document its function. Instead of reading a series of statements like 
```

if ( Node <> NULL )
   while ( Node.Next <> NULL ) do
      Node = Node.Next
   LeafName = Node.Name
else
   LeafName = ""

```

You can read a statement like 
```

LeafName = GetLeafName( Node )

```

The new routine is so short that all it needs for documentation is a good name. Using a function call instead of six lines of code makes the routine that originally contained the code less complex and documents it automatically. 



---

### Post by Shpongle on 2009-11-19
> **denago said:**
> 
Don't look at functions as something that complicates code, look at them as something that simplifies code.

+1 , this help you to brake problems down and simplifies them, also you can reuse functions and it saves time and coding, isolates problems and is part of the whole object oriented concept together with classes etc

---

### Post by dwhitney67 on 2009-11-19
Pluto has been demoted; it is no longer considered a planet.

The big key located at the lower-middle of your computer's keyboard is known as the 'space' key.  It's unfortunate, and at the same time ironic, that you elected not to use it in your coding exercise.

Your error handling for erroneous user input is very ungraceful.  Permit the user at least one more opportunity to input proper data before exiting the program.

When passing a string to a function, pass it by reference, not by value.  It saves overhead of 1) re-creating the string in memory, and 2) CPU cycles.

When you exit the while-loop in the main() function because the user entered an invalid planet/moon name, you proceed to print 'lbs', but nothing more.

The 'system(pause)' statement is applicable to Windoze, but not Linux.  Avoid its use, and instead use getchar() or something similar.

Avoid doing too much in a function; and that includes main().  Consider creating a function to gather input from the user, another (which you already have) to interpret the input, and lastly one to print the data.

Attempt to delve into OOP for your next C++ assignment; you could define a base-class called CelestialBody, and from there, create sub-classes called Galaxy, Star, Planet, Moon, and then from there... well hopefully you get it.  Basically categorized each celestial body to the type that matches it, thus offering that object its specialized attributes for the type of celestial body.

---

### Post by Muffinabus on 2009-11-19
Thanks for the comments already.  Does anyone have any links that may go over etiquette for whitespace use and other code formatting ideas?

And thanks for the tips on using functions, I will try to incorporate them more in my programs in the future, might even rewrite some of my current ones for practice.
> **dwhitney67 said:**
> Pluto has been demoted; it is no longer considered a planet.
I'm aware, I figured the point was too trivial to write the editors of the book about it.

> **dwhitney67 said:**
> The big key located at the lower-middle of your computer's keyboard is known as the 'space' key.  It's unfortunate, and at the same time ironic, that you elected not to use it in your coding exercise.
I'm not sure what you are referring to here, I actually have many spaces in my program.  Could you be more specific?

> **dwhitney67 said:**
> Your error handling for erroneous user input is very ungraceful.  Permit the user at least one more opportunity to input proper data before exiting the program.
I am not aware of any method that would fix the in stream after it has failed other than exiting the program entirely.  If someone could provide a better method, I would be glad to see it and learn from you.

> **dwhitney67 said:**
> When passing a string to a function, pass it by reference, not by value.  It saves overhead of 1) re-creating the string in memory, and 2) CPU cycles.
Probably a good point, I honestly missed the class from when we discussed reference values so I didn't grasp the concept fully.  So passing it by reference shows the function where the memory is located, correct?

> **dwhitney67 said:**
> When you exit the while-loop in the main() function because the user entered an invalid planet/moon name, you proceed to print 'lbs', but nothing more.
Admittedly, I wrote this program hurriedly and didn't spend much time on output formatting.

> **dwhitney67 said:**
> The 'system(pause)' statement is applicable to Windoze, but not Linux.  Avoid its use, and instead use getchar() or something similar.
I actually meant to remove my instances of system("pause").  I am aware it's used on Windows, it's just, I don't normally do my coding on my Linux install.

But anywho, like I said, amateur programmer.  I have never really done any OOP before, but yes, I would imagine it would be a good idea to start and practice.  Thanks for your post.

---

### Post by issih on 2009-11-19
I agree with the others about funtions, classes and whitespace...they are your friends.

As for your code I'll point out that in addition to what has been mentioned thus far you don't properly validate your input. I could enter "vestigial tail" and it would tell me my weight on venus, and I could be equally silly for the other planets.

Also your enum is entirely pointless.. Your findplanet method has a nice big switch that sorts out which planet you are on, and sets an enum value appropriately, which you then pass back to the main loop.

The main loop then switches on the value of that enum to set the weight.

You could just set the findplanets method to return a double and return the appropriate multiplier value based on which planet your input validation establishses the user wants, the second switch statement in main and the enum are doing nothing useful at all.

that being said, if the planets were a class rather than an enum, so the planet had a calculateWeight() function, then the design would be fine, as the code in main would be something like:

```

Planet & aPlanet = findPlanet(input);
aPlanet.calculateWeight(mass);

```

with no need for the secondary switch. In addition the Planets could be extended to offer lots of different functionalities e.g. a breath function that returns an "aaaah" on earth but "cough cough XXXXXXXXXXXXXXXXXXX" on all the others.

P.S. Pluto will always be a planet to me :(

---

### Post by Muffinabus on 2009-11-19
> **issih said:**
> I agree with the others about funtions, classes and whitespace...they are your friends.

As for your code I'll point out that in addition to what has been mentioned thus far you don't properly validate your input. I could enter "vestigial tail" and it would tell me my weight on venus, and I could be equally silly for the other planets.

Also your enum is entirely pointless.. Your findplanet method has a nice big switch that sorts out which planet you are on, and sets an enum value appropriately, which you then pass back to the main loop.

The main loop then switches on the value of that enum to set the weight.

You could just set the findplanets method to return a double and return the appropriate multiplier value based on which planet your input validation establishses the user wants, the second switch statement in main and the enum are doing nothing useful at all.

that being said, if the planets were a class rather than an enum, so the planet had a calculateWeight() function, then the design would be fine, as the code in main would be something like:

```

Planet & aPlanet = findPlanet(input);
aPlanet.calculateWeight(mass);

```

with no need for the secondary switch. In addition the Planets could be extended to offer lots of different functionalities e.g. a breath function that returns an "aaaah" on earth but "cough cough XXXXXXXXXXXXXXXXXXX" on all the others.

P.S. Pluto will always be a planet to me :(

Yes, I see what you mean, though the book specified that we use an enumerated type value to represent the planet, and the switch to find the planet name is taken nearly directly from an example in my book.  The books argument for having such a lenient check on the planet name was that it would use less resources to figure out the first letter first, deciding what the planet was at the soonest point possible, then using the second letter after assuming the first are the same, etc.  I felt that having two switch statements could possibly be redundant and it feels awkward (I also don't have much faith in my while loop statement check, I feel that could have been done better as well).

And about classes, I honestly have not learned what they are yet.  I have taken a Java class before, but that was nearly 6 years ago in high school, so I don't remember much.  Classes are covered in chapter 12, this assignment was for chapter 10 of my book, though perhaps I will read the chapter now so I can better grasp what you're saying.

---

### Post by issih on 2009-11-19
Ah, my apologies, I missed the requirement for an enum...

If I had to use an enum, I'd probably initialise an array of doubles with all the multiplier weights, ordered the same as the enum, then just use the enum returned from findplanet as the index in that array.

Thus avoiding the 2nd switch statement.

Generally having multiple arrays that only function by being in the same order is a bit kludgey, and a class  would usually be a better solution, but within the confines of the question, that's how I'd do it.

As for your input validation...the question stated the need to alert the user if an incorrect planet name was entered...hence my flagging it up.

---

### Post by Arndt on 2009-11-19
> **Muffinabus said:**
> Amateur programmer here, have been taking a C++ course this semester and I am kind of wondering where I stand in my writing and style skills.  Since it is an intro course, I haven't learned too much yet, so just keep that in mind.  But if you could please review my most recent homework assignment (I've already turned it in, I'm not looking for help on it, it works exactly as the assignment describes), mainly wishing to be critiqued on style and method.



1) I usually find "template header" comments such as

//constants, enumerations, and functions

more than useless. Any reader can see for himself what is below.

2) For someone new to the program, it helps to document what the constants represent. The gravitation, I gather.

3) Pluto is no longer a planet, but the moon is even less one. It's sort of alright now, but what if you extend the program some day to both planets and their moons? If you decide that yes, it makes the program easiest to understand this way, that's fine, but it merits a comment about how "planet" is defined in this particular program code.

4) You do weightInd = findPlanet(planet), but then you switch on weightInd = findPlanet(planet) and not on the variable weightInd.
What does the name "weightInd" stand for, by the way? Index? Why not spell out the whole word?

5) There is code duplication in the function findPlanet: toupper(planetName.at(1)) is done three times. The optimizer will find this, so that's not the problem, but ease of maintaining the code.

6) You mix int and Planet so you can use the sentinel value -1, but it's cleaner if you use Planet all the time, and add another enum entry, such as NOPLANET. You already have a non-planet, after all; DEFAULT.

7) Comparing weightInd with 10 is not elegant - compare it to the known last enum, or the last planet + 1, or something like that. But I think that test isn't needed at all - if it's not a planet, weightInd will be -1.

---

### Post by dwhitney67 on 2009-11-19
> **Muffinabus said:**
> 
I'm not sure what you are referring to here, I actually have many spaces in my program.  Could you be more specific?

I was actually referring to the vertical white-space; I should have indicated that more new lines are needed; not horizontal white-space.  Sorry about the confusion.

> 
I am not aware of any method that would fix the in stream after it has failed other than exiting the program entirely.  If someone could provide a better method, I would be glad to see it and learn from you.

Using a combination of clear() and ignore(), you can clear the stream error(s) and contents.  For example:
```

#include <iostream>

using namespace std;

template <typename T>
T getInput(const char* prompt)
{
   using namespace std;

   T input;

   while (true) {
      cout << prompt;
      cin  >> input;

      if (cin.peek() == '\n' && !cin.fail()) break;

      cout << "Invalid input!  Try again...\n" << endl;
      cin.clear();
      cin.ignore(1024, '\n');
   }

   return input;
}

int main()
{
   int num = getInput<int>("Enter a number: ");
   cout << "You entered: " << num << endl;
}

```

P.S.  You can read [here]("http://www.cplusplus.com/reference/iostream/istream/") for more information on clear() and ignore().

---

### Post by lisati on 2009-11-19
I agree with the other comments about functions, comments and whitespace: done well, they can help simplify the initial coding and subsequent debugging by organizing the code into managable chunks.
They can also help clarify the program's behaviour for others who might be called in to assist or if you have a break from your project and come back to it a few months later.

---

### Post by Muffinabus on 2009-11-19
> **dwhitney67 said:**
> I was actually referring to the vertical white-space; I should have indicated that more new lines are needed; not horizontal white-space.  Sorry about the confusion.


Using a combination of clear() and ignore(), you can clear the stream error(s) and contents.  For example:
```

#include <iostream>

using namespace std;

template <typename T>
T getInput(const char* prompt)
{
   using namespace std;

   T input;

   while (true) {
      cout << prompt;
      cin  >> input;

      if (cin.peek() == '\n' && !cin.fail()) break;

      cout << "Invalid input!  Try again...\n" << endl;
      cin.clear();
      cin.ignore(1024, '\n');
   }

   return input;
}

int main()
{
   int num = getInput<int>("Enter a number: ");
   cout << "You entered: " << num << endl;
}

```

P.S.  You can read [here]("http://www.cplusplus.com/reference/iostream/istream/") for more information on clear() and ignore().

Ah, yes.  Thanks for the information.  I feel slightly misinformed, the C++ book we are using mentioned how there is no way for the cin stream to recover if it is given bad data, so I never really investigated further.

I'm probably going to attempt rewriting this sample program with some of the new advice I've got, I'll see how this goes.

---

### Post by Muffinabus on 2009-11-20
My second attempt:

```
#include <iostream>
#include <cctype>
#include <string>
using namespace std;

enum Planets {MERCURY, VENUS, EARTH, MOON, MARS, JUPITER, SATURN, URANUS, NEPTUNE, PLUTO, DEFAULT};

void getInput();
void findPlanet();
void output();

const double MER = 0.4155;
const double VEN = 0.8975;
const double EAR = 1.0;
const double MOO = 0.166;
const double MAR = 0.3507;
const double JUP = 2.5374;
const double SAT = 1.0677;
const double URA = 0.8947;
const double NEP = 1.1794;
const double PLU = 0.0899;

double weight = 0;
double planetWeight = 0;
int count = 0;
string planet;
string planetOutput;
Planets planetName;

int main() {
  getInput();
  do {
    findPlanet();
    output();
  } while (planetName == DEFAULT);
  //system ("pause");
  return 0;
}

void getInput() {
  while (true) {
    cout << "Enter your weight: ";
    cin >> weight;
    cout << endl;
    if (cin.peek() == '\n' && !cin.fail()) break;
    cout << "Invalid input!  Try again...\n" << endl;
    cin.clear();
    cin.ignore(1024, '\n');
  }

  cout << "Enter one of the following planets: " << endl << "Mercury" 
    << endl << "Venus" << endl << "Earth" << endl << "Moon" << endl 
    << "Mars" << endl << "Jupiter" << endl << "Saturn" << endl 
    << "Uranus" << endl << "Neptune" << endl << "Pluto" << endl;
  cin >> planet;
  cout << endl;
}

void findPlanet() {
  switch (toupper(planet.at(0))) {
    case 'M' : if (planet.length() >= 2) {
                 if (toupper(planet.at(1)) == 'A')
                   planetName = MARS;
                 else if (toupper(planet.at(1)) == 'E')
                   planetName = MERCURY;
                 else if (toupper(planet.at(1)) == 'O')
                   planetName = MOON;
                 else
                   planetName = DEFAULT;
               }
               else
                 planetName = DEFAULT;
               break;
    case 'V' : planetName = VENUS;
               break;
    case 'E' : planetName = EARTH;
               break;
    case 'J' : planetName = JUPITER;
               break;
    case 'S' : planetName = SATURN;
               break;
    case 'U' : planetName = URANUS;
               break;
    case 'N' : planetName = NEPTUNE;
               break;
    case 'P' : planetName = PLUTO;
               break;
    default  : planetName = DEFAULT;
  }

  switch (planetName) {
    case MERCURY : planetWeight = weight*MER;
                   planetOutput = "Mercury";
                   break;
    case VENUS   : planetWeight = weight*VEN;
                   planetOutput = "Venus";
                   break;
    case EARTH   : planetWeight = weight*EAR;
                   planetOutput = "Earth";
                   break;
    case MOON    : planetWeight = weight*MOO;
                   planetOutput = "Moon";
                   break;
    case MARS    : planetWeight = weight*MAR;
                   planetOutput = "Mars";
                   break;
    case JUPITER : planetWeight = weight*JUP;
                   planetOutput = "Jupiter";
                   break;
    case SATURN  : planetWeight = weight*SAT;
                   planetOutput = "Saturn";
                   break;
    case URANUS  : planetWeight = weight*URA;
                   planetOutput = "Uranus";
                   break;
    case NEPTUNE : planetWeight = weight*NEP;
                   planetOutput = "Neptune";
                   break;
    case PLUTO   : planetWeight = weight*PLU;
                   planetOutput = "Pluto";
                   break;
    default      : cout << "\n\nERROR: Did not recognize planet name, try again." 
                     << endl << endl;
                   break;
  }
}

void output() {
  cout << "Your weight is " << planetWeight << " pounds on the planet " 
    << planetOutput << '.' << endl;
}
```

I do agree that in this case, the enumerator is entirely pointless and I still don't like having to use two switch statements.

I was able to refine my output using a more clear method, got rid of the redundant sentinel value, and made more use of functions and vertical whitespace.

Things I am still unsure about:

Arndt mentioned that using toupper(planetName.at(1)) three times should be avoided.  In this specific case, how could it be?  would setting a char value equal to toupper(planetName.at(1)) then evaluating the char be better?

Is my whitespace more appropriate now?

Should I have used value returning functions instead of void functions?

Many thanks to you all for taking the time to assist me though, I appreciate it.

And thanks dwhitney, the new method for error checking works wonderfully and should help a lot.

---

### Post by dwhitney67 on 2009-11-20
> **Muffinabus said:**
> 
Arndt mentioned that using toupper(planetName.at(1)) three times should be avoided.  In this specific case, how could it be?  would setting a char value equal to toupper(planetName.at(1)) then evaluating the char be better?


The first thing to do after obtaining the user's input for the planet/moon name is to normalized it... perhaps put it all in lowercase or all in uppercase.  All this involves is iterating through each of the characters of the string to toggle it to the appropriate character.

Next, develop a function that accepts this string so that you can compare it against a constant string, and if there is a match, return the weight factor.  If you do not find a match, then return zero or some negative factor.

As for your second attempt, dispense with the global variables; they are undesirable and contradict with good-programming practices.

As for the getInput(), define it as I posted earlier; then use it to prompt the user for their weight, and the celestial body name.  I don't think you need to present them a choice of all of the planets/moon; surely they know these.  Anyhow, something like:
```

double weight = getInput<double>("Enter your weight: ");

while (true)
{
   string name = getInput<string>("Enter name of Solar System planet or moon, or 'quit' when done: ");

   tolower(name);   // you will need to define this yourself

   if (name == "quit") break;

   double weightFactor = getWeightFactor(name);
   ...

```

---

### Post by issih on 2009-11-20
I agree about the global variables...their use should be avoided wherever possible.

Given that the op stated that they haven't really covered classes yet, I think we can assume that templates are a bit of a mystery at this point...dwhitney67 is advising you to use the original code posted as a template (which basically is a bit of code that adapts to be appropriate for different types, a double and a string in this case)

your usage of dwhitney67's concept for avoiding the cin stream failing if the wrong pattern is entered is fine, and it is valid to not bother with it for the planetname as that is merely grabbing the entered string, whatever it is.

Whilst I agree entirely that using a method like "getWeightFactor(name)" is a better solution, it somewhat breaks the requirement to use an eval in this case.

Finally, you do need to output the possible inputs, as the question requires it.

Generally all the advice given was good, just not within the rather spurious confines of the question you are answering.


Finally I think your 2nd stab at the code has a fairly serious error.

If you input a planet name that doesn't resolve to any of your matches, lets say you enter "queen", then your code goes into an infinite loop.

This is because your getInput() function is not within the loop in main, so the bad input merely gets repeatedly parsed by findPlanet, but always returns DEFAULT, and carries on looping.

Hope that helps

---

### Post by denago on 2009-11-20
Why does your findPlanet function calculate weight?  A function should do one thing only.

---

### Post by Muffinabus on 2009-11-20
> **issih said:**
> I agree about the global variables...their use should be avoided wherever possible.

Given that the op stated that they haven't really covered classes yet, I think we can assume that templates are a bit of a mystery at this point...dwhitney67 is advising you to use the original code posted as a template (which basically is a bit of code that adapts to be appropriate for different types, a double and a string in this case)

your usage of dwhitney67's concept for avoiding the cin stream failing if the wrong pattern is entered is fine, and it is valid to not bother with it for the planetname as that is merely grabbing the entered string, whatever it is.

Whilst I agree entirely that using a method like "getWeightFactor(name)" is a better solution, it somewhat breaks the requirement to use an eval in this case.

Finally, you do need to output the possible inputs, as the question requires it.

Generally all the advice given was good, just not within the rather spurious confines of the question you are answering.


Finally I think your 2nd stab at the code has a fairly serious error.

If you input a planet name that doesn't resolve to any of your matches, lets say you enter "queen", then your code goes into an infinite loop.

This is because your getInput() function is not within the loop in main, so the bad input merely gets repeatedly parsed by findPlanet, but always returns DEFAULT, and carries on looping.

Hope that helps

You are correct in assuming that I have literally no idea what a template is, so I did just take from the code he gave what I understood and implemented it in mine.

I will do away with my global variables then, I had a feeling I was doing something wrong there, it seemed too easy.  Then I must have missed that infinite loop, I didn't check to see if it had the same error checking as my original as I rewrote the whole thing and was a bit quick to repost it back here for more critiquing.  I will take a look at it.

Thanks.

---

### Post by Muffinabus on 2009-11-20
Here we go again!

Third attempt:

```
#include <iostream>
#include <cctype>
#include <string>
using namespace std;

enum Planets {MERCURY, VENUS, EARTH, MOON, MARS, JUPITER, SATURN, URANUS, NEPTUNE, PLUTO, DEFAULT};

double getWeight(double);
string getPlanet(string);
string normalizePlanet(string&);
string denormalizePlanet(string&);
Planets findPlanet(string&);
double findWeight(Planets&, double&, double);
void output(double&, string&);

const double MER = 0.4155;
const double VEN = 0.8975;
const double EAR = 1.0;
const double MOO = 0.166;
const double MAR = 0.3507;
const double JUP = 2.5374;
const double SAT = 1.0677;
const double URA = 0.8947;
const double NEP = 1.1794;
const double PLU = 0.0899;

int main() {
  double weight = 0;
  double planetWeight = 0;
  string planet;
  Planets planetName;
  weight = getWeight(weight);
  do {
    planet = getPlanet(planet);
    planetName = findPlanet(planet);
    planetWeight = findWeight(planetName, weight, planetWeight);
  } while (planetName == DEFAULT);
  output(planetWeight, planet);
  system ("pause");
  return 0;
}

double getWeight(double weight) {
  while (true) {
    cout << "Enter your weight: ";
    cin >> weight;
    cout << endl;
    if (cin.peek() == '\n' && !cin.fail()) break;
    cout << "Invalid input!  Try again...\n" << endl;
    cin.clear();
    cin.ignore(1024, '\n');
  }
  return weight;
}

string getPlanet(string planet) {
  cout << "Enter one of the following planets: " << endl << "Mercury" 
    << endl << "Venus" << endl << "Earth" << endl << "Moon" << endl 
    << "Mars" << endl << "Jupiter" << endl << "Saturn" << endl 
    << "Uranus" << endl << "Neptune" << endl << "Pluto" << endl;
  cin >> planet;
  cout << endl;
  planet = normalizePlanet(planet);
  return planet;
}

string normalizePlanet(string& planet) {
  int length = planet.length();
  string newPlanet;
  int x = 0;
  while (length > 0) {
    newPlanet += toupper(planet.at(x));
    x++;
    length--;
    }
  return newPlanet;
}

string denormalizePlanet(string& planet) {
  int length = planet.length();
  string planetOut;
  int x = 0;
  while (length > 0) {
    if (x == 0)
      planetOut += toupper(planet.at(0));
    else
      planetOut += tolower(planet.at(x));
    x++;
    length--;
    }
  return planetOut;
}

Planets findPlanet(string& planet) {
  Planets planetName;
  if (planet == "MARS")
    planetName = MARS;
  else if (planet == "MERCURY")
    planetName = MERCURY;
  else if (planet == "MOON")
    planetName = MOON;
  else if (planet == "VENUS")
    planetName = VENUS;
  else if (planet == "EARTH")
    planetName = EARTH;
  else if (planet == "JUPITER")
    planetName = JUPITER;
  else if (planet == "SATURN")
    planetName = SATURN;
  else if (planet == "URANUS")
    planetName = URANUS;
  else if (planet == "NEPTUNE")
    planetName = NEPTUNE;
  else if (planet == "PLUTO")
    planetName = PLUTO;
  else
    planetName = DEFAULT;
  return planetName;
}

double findWeight(Planets& planetName, double& weight, double planetWeight) {
  switch (planetName) {
    case MERCURY : planetWeight = weight*MER;
                   break;
    case VENUS   : planetWeight = weight*VEN;
                   break;
    case EARTH   : planetWeight = weight*EAR;
                   break;
    case MOON    : planetWeight = weight*MOO;
                   break;
    case MARS    : planetWeight = weight*MAR;
                   break;
    case JUPITER : planetWeight = weight*JUP;
                   break;
    case SATURN  : planetWeight = weight*SAT;
                   break;
    case URANUS  : planetWeight = weight*URA;
                   break;
    case NEPTUNE : planetWeight = weight*NEP;
                   break;
    case PLUTO   : planetWeight = weight*PLU;
                   break;
    default      : cout << "\n\nERROR: Did not recognize planet name, try again." 
                     << endl << endl;
                   break;
  }
  return planetWeight;
}

void output(double& planetWeight, string& planet) {
  string planetOutput = denormalizePlanet(planet);
  if (planet == "MOON")
    cout << "Your weight is " << planetWeight << " pounds on the Moon." << endl;
  else
    cout << "Your weight is " << planetWeight << " pounds on the planet " 
      << planetOutput << '.' << endl;
}
```

Fixed my infinite loop, got rid of all the global variables that weren't constants, changed the void functions to value returning functions, created some sort of string normalization and denormalization functions for reading and output, made more functions so that each one only has one main task, and got rid of the enumerator switch to change it to nested if statements so that I could check for the whole string.

I am still not sure I know how to properly use reference values when using functions, so please, correct me if I misused them.  And the enumerator is still ever so pointless... meh.

Hopefully this will be the last time I will have to revise it (: ?

---

### Post by dwhitney67 on 2009-11-20
What is the purpose of the third parameter in this function?
```

double findWeight(Planets& planetName, double& weight, double planetWeight)

```



Hint:  None.

---

### Post by lisati on 2009-11-20
> **dwhitney67 said:**
> What is the purpose of the third parameter in this function?
```

double findWeight(Planets& planetName, double& weight, double planetWeight)

```



Hint:  None.

I agree: in the program's current incarnation, it does seem redundant. I see possibilities for its use in future expansion of the program, but that's not 100% relevant right now.

edit: my main concern at this point is one of style, to choose something like either:
```
result = function_call(parameter 1, parameter 2, ....)
```
or:
```
function_call(parameter 1, paramter 2, ...., result)
```
and stick with one style for a paticular call.

---

### Post by Muffinabus on 2009-11-20
> **dwhitney67 said:**
> What is the purpose of the third parameter in this function?
```

double findWeight(Planets& planetName, double& weight, double planetWeight)

```



Hint:  None.

Code legibility (: ?

At least if that's the one thing you chose to pick out on my current iteration, the rest must be decent, right?

> **lisati said:**
> I agree: in the program's current incarnation, it does seem redundant. I see possibilities for its use in future expansion of the program, but that's not 100% relevant right now.

edit: my main concern at this point is one of style, to choose something like either:
```
result = function_call(parameter 1, parameter 2, ....)
```
or:
```
function_call(parameter 1, paramter 2, ...., result)
```
and stick with one style for a paticular call.

I did do that though, didn't I?  The only one that was not consistent was when I called the output function, which was a void function and wouldn't make any sense to have a value returned by it.

Or are you saying I should do it differently than how I have it?

---

### Post by issih on 2009-11-20
Just a quick lesson on references for you, as you seem slightly unsure about them..

A reference is literally a link to something else of the same type. Any action executed on a reference is actually performed on the thing that the reference is linked to.

so:

```

int x = 1;
int & y = x;
y+=10;
cout<<"x after reference addition = "<<x<<endl;

```

will return:

    x after reference addition = 11

because adding 10 to the reference y is really adding it to x.

Now, function calls in C++ generally implement pass-by-value. What this means is that a function will copy the value of any passed in parameter into a local variable (which exists only within the function) and consequently the function can not have any effect on the value of the variable that was passed into it, it can only affect its own copy.

so:

```

void addFive(int y){
    y+=5;
    cout<<"y in function = "<<y<<endl;
}

int main(){
    int x = 1;
    cout<<"x before function = "<<x<<endl;
    addFive(x);
    cout<<"x after function = "<<x<<endl;
}

```

Will return:

    x before function = 1
    y in function = 6
    x after function = 1

because the value in x was copied into the new variable y, and that variable had 10 added to it, x was never altered.

If you declare the function parameter as a reference then you pass that parameter as a reference, and the code inside the function is directly manipulating the passed in variable, not a local copy.

so:

```

void addFive(int & y){
    y+=5;
    cout<<"y in function = "<<y<<endl;
}

int main(){
    int x = 1;
    cout<<"x before function = "<<x<<endl;
    addFive(x);
    cout<<"x after function = "<<x<<endl;
}

```

will return:

x before function = 1
y in function = 6
x after function = 6

because the function is manipulating the passed in variable x via its reference y.

Return values work the same way, by default they copy the value of the variable inside the function into a new variable which is local to the calling code.

You can set the return type to be a reference in the same way as the parameters, but this must be done with care, as any variable returned in this way must NOT be a local variable within the function being returned. This is because the memory holding the variables defined in that function is discarded as the function exits, and the returned reference suddenly points to nothing....this is not allowed and the behaviour is undefined if you do this.

If you are returning a reference then ensure it is to an object with continuing scope, either a global variable, something passed in to the function as a reference, or something created via custom memory management (pointers heap allocation etc - you'll come onto that :)).

The advice to use references where possible stems from the fact that you can create complex objects in c++, and then pass them about as parameters and return values. The computational cost of copying these objects when passing by value can be significant, so it is wise to get to grips with passing by reference asap.

For the code you are making right now though, I would personally say that passing by reference is not necessary, as none of your parameters are large enough that the cost of copying them will produce any significant performance hit...

Hope that helps

---

### Post by Muffinabus on 2009-11-20
> **issih said:**
> Just a quick lesson on references for you, as you seem slightly unsure about them..

A reference is literally a link to something else of the same type. Any action executed on a reference is actually performed on the thing that the reference is linked to.

so:

```

int x = 1;
int & y = x;
y+=10;
cout<<"x after reference addition = "<<x<<endl;

```

will return:

    x after reference addition = 11

because adding 10 to the reference y is really adding it to x.

Now, function calls in C++ generally implement pass-by-value. What this means is that a function will copy the value of any passed in parameter into a local variable (which exists only within the function) and consequently the function can not have any effect on the value of the variable that was passed into it, it can only affect its own copy.

so:

```

void addFive(int y){
    y+=5;
    cout<<"y in function = "<<y<<endl;
}

int main(){
    int x = 1;
    cout<<"x before function = "<<x<<endl;
    addFive(x);
    cout<<"x after function = "<<x<<endl;
}

```

Will return:

    x before function = 1
    y in function = 6
    x after function = 1

because the value in x was copied into the new variable y, and that variable had 10 added to it, x was never altered.

If you declare the function parameter as a reference then you pass that parameter as a reference, and the code inside the function is directly manipulating the passed in variable, not a local copy.

so:

```

void addFive(int & y){
    y+=5;
    cout<<"y in function = "<<y<<endl;
}

int main(){
    int x = 1;
    cout<<"x before function = "<<x<<endl;
    addFive(x);
    cout<<"x after function = "<<x<<endl;
}

```

will return:

x before function = 1
y in function = 6
x after function = 6

because the function is manipulating the passed in variable x via its reference y.

Return values work the same way, by default they copy the value of the variable inside the function into a new variable which is local to the calling code.

You can set the return type to be a reference in the same way as the parameters, but this must be done with care, as any variable returned in this way must NOT be a local variable within the function being returned. This is because the memory holding the variables defined in that function is discarded as the function exits, and the returned reference suddenly points to nothing....this is not allowed and the behaviour is undefined if you do this.

If you are returning a reference then ensure it is to an object with continuing scope, either a global variable, something passed in to the function as a reference, or something created via custom memory management (pointers heap allocation etc - you'll come onto that :)).

The advice to use references where possible stems from the fact that you can create complex objects in c++, and then pass them about as parameters and return values. The computational cost of copying these objects when passing by value can be significant, so it is wise to get to grips with passing by reference asap.

For the code you are making right now though, I would personally say that passing by reference is not necessary, as none of your parameters are large enough that the cost of copying them will produce any significant performance hit...

Hope that helps

Okay, that makes sense now (:

So, if you WERE to add reference values to my parameters as they currently are (IE: assuming they were large and could cause performance problems), which ones in my functions would you add references to?  I feel like I almost did it completely backwards, actually.

---

### Post by CptPicard on 2009-11-20
> **Muffinabus said:**
> which ones in my functions would you add references to?

As a rule, whenever it is an object and not a primitive type, pass by reference by default.

Btw please do not quote entire posts just to answer a few lines. Thanks :)

---

