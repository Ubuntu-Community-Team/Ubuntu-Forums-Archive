---
title: "iostream behaving strangely (beginner)"
date: 2011-01-16
forum: Programming Talk
---

### Post by MichaelBurns on 2011-01-16
I'm going through an online C++ tutorial (just as a refresher), and wow, right at the beginning I get hit with embarassing problems.  (It's been a few years since I've used C++, and I don't think that I was very good anyway.)  I really didn't think that I could get stumped by iostreams, but here it is.  The program doesn't take my input, and I don't understand why.  For example, I was supposed to modify their example code to ask for another string and numerical value (so the yesOrNo and numberOfTimes variables are my additions):
```

#include <string>
#include <iostream>

int main() {
  using namespace std ;
  string yourName "John Doe" ;
  string yesOrNo = "yes" ;
  int birthYear = 2011 ;
  int numberOfTimes = 0 ;

  cout << " What is your name? "  << flush ;
  getline(cin,yourName) ;

  cout << "What year were you born? " ;
  cin >> birthYear ;

  cout << "Your name is " << yourName << " and you are approximately " << (2011 - birthYear) << " years old. " << endl ;

  cout << "Isn't this a worthless program? " ;
  getline(cin,yesOrNo) ;

  cout << "How many times did you run this worthless program? " ;
  cin >> numberOfTimes ;

  cout << "This is " << yesOrNo << " a worthless program, and you ran it " << numberOfTimes << " times." << endl ;
  return 0 ;
}

```
The getline(cin,yesOrNo) and cin >> numberOfTimes
seem to be skipped (I don't have a chance to provide these inputs from the keyboard, and the program just skips all the way to the end, but still displays all of the couts).  Can someone explain to me why, or see an obvious problem with the code?

---

### Post by worksofcraft on 2011-01-16
I think the problem is that [getline]("http://www.cplusplus.com/reference/iostream/istream/getline/") is a method of cin and yo need to pass a pointer to an array of char where you can store the input, not a string.

Check the link and see if it makes more sense?

---

### Post by Paul820 on 2011-01-17
There isn't anything wrong with the code, it's just how cin treats the newline character. Here's what's happening. Your first input statement is asking for a name, you enter a name, the name gets stored in the string and then the newline '/n' character is discarded.

Next you ask for birthyear. You enter it, cin read the year and stores it in the int, but it then ignores the '/n' and leaves it in the buffer, it doesn't discard it like getline does.

So the next time you come to read more data, your next getline sees the '/n' character. It treats the newline as the only data there is so it discards it from the buffer leaving you with nothing in your string and the buffer empty for the next input.

Solution?

Read and discard the newline when you use cin on it's own for input.

You can either concatenate the input with a .get() or use cin.get() to read and discard it.

Either:
```
cout << "What year were you born? ";
( cin >> birthYear ).get();
```

Or:
```
cout << "What year were you born? ";
cin >> birthYear;
cin.get();
```

Hope this helps. ;)

---

### Post by dwhitney67 on 2011-01-17
Usage of get() may not be the very best choice to recommend.  For example, if one seeks input for an int, and the user enters "123abc" plus the newline, get() will only pop off the character 'a' and still leave the rest of the data in the stream.

Instead, use ignore().  This function takes two parameters:  the marker character you seek (a newline), and the number of characters to ignore from the stream until you find the marker.  For example:
```

cout << "Enter a number: ";
cin  >> number;
cin.ignore(1024, '\n');

```
If you are concerned that some hacker may enter more than 1024 characters in an effort to subvert your application, then you could consider specifying the maximum sized value using something like:
```

#include <limits>
...
cin.ignore(numeric_limits<streamsize>::max(), '\n');

```


P.S.  Of course, what's missing from the code above is the check to ensure that cin was able to obtain an int value in the first place.

Here's some code to ensure that input for a string, int, float, double, etc. is obtained successfully.
```

#include <string>
#include <iostream>
#include <limits>

template <typename T>
T getInput(const char* prompt)
{
   using namespace std;

   T    input;
   bool done = false;

   while (!done) {
      // prompt user and attempt to read input
      cout << prompt;
      cin  >> input;

      // check if valid input given; break from loop if so.
      if (cin.peek() == '\n' && cin.good())
      {
         done = true;
      }
      else
      {
         // user gave bad input; let them know about it.
         cout << "Invalid input!  Try again...\n" << endl;
         cin.clear();
      }

      do { cin.ignore(numeric_limits<streamsize>::max(), '\n'); } while (!cin);
   }

   return input;
}

int main(void)
{
   char        ch   = getInput<char>("Enter a char: ");
   std::string str1 = getInput<std::string>("Enter a string: ");
   int         num  = getInput<int>("Enter a number: ");
   std::string str2 = getInput<std::string>("Enter another string: ");

   std::cout << "Your char is        : " << ch   << std::endl;
   std::cout << "Your string is      : " << str1 << std::endl;
   std::cout << "Your number is      : " << num  << std::endl;
   std::cout << "Your other string is: " << str2 << std::endl;
}

```

---

### Post by MichaelBurns on 2011-01-19
> **worksofcraft said:**
> ... yo need to pass a pointer to an array of char where you can store the input, not a string.So a string is not the same as a pointer to a character array?

> **Paul820 said:**
> ... cin read the year and stores it in the int, but it then ignores the '/n' and leaves it in the buffer, it doesn't discard it like getline does.

So the next time you come to read more data, your next getline sees the '/n' character. It treats the newline as the only data there is so it discards it from the buffer leaving you with nothing in your string and the buffer empty for the next input.

... either concatenate the input with a .get() or use cin.get() ...Is there a (simple/buitlin) way to test the input stream to see if the first character is a newline?  This seems kind of strange, but I tested your theory and it seems correct:
```

#include <iostream>
#include <string>
int main() {
  using namespace std ;
  int birthyear = 2011 ;
  string somestuff = "whatever" ;
  while ( birthyear != 9999 ) {
    cout << "What year were you born? (9999 to quit) " ;
    cin >> birthyear ;
    cout << "You were born in " << birthyear << endl ;
  }
  cout << "Enter some stuff: " ;
  getline( cin , somestuff ) ;
  cout << "You entered: " << somestuff << endl ;
  cout << "Enter some more stuff: ";
  getline( cin , somestuff ) ;
  cout << "You entered: " << somestuff << endl ;
  return 0 ;
}

```
cin apparently doesn't care about the \n in the buffer, but the first getline does, and then the second getline behaves as intended.  However, just FYI to anyone reading this (and probably well-known to those who have already replied), the while loop goes into an infinite loop if I enter a string instead of a number.  I wonder why this happens.

@dwhitney:
Your suggestion seems complicated.  I'm not disputing your ability as a programmer.  Maybe you're a professional programmer, and maybe your suggestion is the best recommendation in the long run, and I do appreciate it and will certainly refer back to it in a few weeks (or months is probably a more realistic target) when I get to templates.  However, for now I really think that I need to figure out some simple little thing that I'm overlooking.  I hope that the tutorial doesn't expect me to know about templates yet.  I've heard of them, but never learned them.  If the tutorial is going to be that way about my learning experience, then I need to find a different tutorial.  I just don't think that it should be this complicated.

I took a course in C++ about 5 years ago, and I used cin and cout in every programming exercise.  I never remember running into this problem; it seems like it was much more foolproof than this.  Could it be that C++ has actually changed in the last 5 years?  Or maybe the compiler that I'm using is doing something screwy?  (or maybe the compiler that I used in that course 5 years ago was made for dummies)

---

### Post by worksofcraft on 2011-01-20
> **MichaelBurns said:**
> So a string is not the same as a pointer to a character array?


No in C++ a string is a container class generated by the standard template library that grows dynamically as you push characters to it. However for this to work you have to call a special "push_back" method for each character as you append it. Presumably that then does dynamic memory reallocation as needed.

The older C style strings were just arrays of char and you could write to them using an incrementing pointer but you cannot do that with an instance of class string.

---

### Post by MadCow108 on 2011-01-20
> **MichaelBurns said:**
> 
cin apparently doesn't care about the \n in the buffer, but the first getline does, and then the second getline behaves as intended.  However, just FYI to anyone reading this (and probably well-known to those who have already replied), the while loop goes into an infinite loop if I enter a string instead of a number.  I wonder why this happens.


when you enter a string the cin >> integer will fail. The stream stays in fail state until you reset it.
To do that you must clear the stream error bit **and** discard the string from the stream buffer or it will fail again on the next attempt to extract the string into a number.
the functions to use arecin.clear(); and cin.ignore(...) as shown in dwhitney's example.


the use of getline is correct, worksofcraft probably confused the two version available in c++. the global getline takes a string, and the istream local getline takes a char array (where you need manual memory managment ...).
the global version (taking a string) is preferable in most cases
[http://www.cplusplus.com/reference/string/getline/](http://www.cplusplus.com/reference/string/getline/)
[http://www.cplusplus.com/reference/iostream/istream/getline/](http://www.cplusplus.com/reference/iostream/istream/getline/)

---

### Post by dwhitney67 on 2011-01-20
> **MichaelBurns said:**
> 
@dwhitney:
Your suggestion seems complicated.  I'm not disputing your ability as a programmer.  Maybe you're a professional programmer, and maybe your suggestion is the best recommendation in the long run, and I do appreciate it and will certainly refer back to it in a few weeks (or months is probably a more realistic target) when I get to templates.  However, for now I really think that I need to figure out some simple little thing that I'm overlooking.  I hope that the tutorial doesn't expect me to know about templates yet.  I've heard of them, but never learned them.  If the tutorial is going to be that way about my learning experience, then I need to find a different tutorial.  I just don't think that it should be this complicated.

If you want to observe the behavior of the code I supplied, but without using it as a template (which is btw, what you use when dealing with the STL), then take away the "template" preface used for the function declaration, and for every instance where you see "T" being used, replace it with your favorite input type (e.g. std::string, int, float, etc).  And then, there's more...

Suffice to say, you would need something like:
```

std::string getStringInput(const char* prompt)
{
   ...
}

int getIntInput(const char* prompt)
{
   ...
}

...

```
or something like:
```

void getInput(const char* prompt, std::string& input)
{
   ...
}

void getInput(const char* prompt, int& input)
{
}

...

```

Happy coding.

> **MichaelBurns said:**
> 
Is there a (simple/buitlin) way to test the input stream to see if the first character is a newline?

"Simple" is a relative term, depending on the level of the programmer.  From the example I provided earlier, I utilized cin's peek() function to determine the next character in the stream.  In other words, if I ask the operator to enter an int value, there should be some number N followed by the newline (e.g. "123\n").  Once cin pulls the number out, two facts should remain... the next character should be a newline, and the cin stream should remain in good standing.  If either of these is false, then I know there was an input error.

---

