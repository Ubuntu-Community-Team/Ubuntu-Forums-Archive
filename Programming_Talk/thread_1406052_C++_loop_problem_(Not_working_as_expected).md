---
title: "C++ loop problem (Not working as expected)"
date: 2010-02-13
forum: Programming Talk
---

### Post by Enrui on 2010-02-13
I keep getting a slight issue, when I try to validate an input. 

```
unsigned char response =0; 

while ((response < 1) || (response > 3))
{
//If validation errs then enter new
cin >> response;
}


```In theory that should just carry on until the user inputs the right item. I've changed char to int and there's no difference. (Not that there should be)

I've tried numerous ways of writing the while parameters still nothing. 

Here's how I've tested it. 

enter a then enter y, then enter 1 = never ending loop
enter 5 then a then 0 = never ending loop...

I'm going to try an internal if... which didn't work same results. 

As soon as I enter a letter it repeats indefinitely, is there a way of validating to only natural numbers or a way to exclude everything else?

---

### Post by MadCow108 on 2010-02-13
works with int as type

the problem is when the type is char it will read ascii chars instead of numbers
so your if statement will have to compare against ascii chars bei adding single quotes around the numbers or subtracting '0' (the offset of numbers in ascii) from the input
this is not necessary if you use int type

---

### Post by Enrui on 2010-02-13
It doesn't work with either unsigned or signed int either, as soon as I enter a letter instead of a number it repeats indefinitely

---

### Post by MadCow108 on 2010-02-13
I'm sorry forgot about the wrong input

check if the stream is good before repeating and if not ignore the input and restart:
```

#include <limits>
if (cin.fail()) {
  cin.clear();
  cin.ignore(std::numeric_limits<streamsize>::max(), '\n');
}

```

---

### Post by dwhitney67 on 2010-02-13
I've used something like this in the past, to ensure I got valid data.

It might be overkill for what you require, but it will provide you with the clues how to handle I/O.

```

#include <iostream>

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
   unsigned int response = getInput<unsigned int>("Enter a number: ");

   // do something with 'response' ...
}

```

---

### Post by Enrui on 2010-02-13
How the.... :popcorn: < - gonna need this. 

Reading through main. 

getInput pulls the T get_input (I assume), which is a template? I understand that Enter a number is the prompt and if that's the case then const char* prompt, would be the prompt. Not a clue what the pointer is for and wouldn't it be better to be a string? 

I don't see what it's doing with unsigned int however, that seems to be the input but I can't see how. 

Yet that leads me either way into the template. 

while(true) ??? I assume this is testing if there is input of any kind not whether the input is correct since the only thing before it is T input (which by the way I have no idea about), no earlier declaration and seems to base from the original template. 

Then it outputs the prompt followed by cin. 

Not a clue how that if statement works as I don't know where cin.peek() comes from, is this a standard cin function. If it's absolutely equal to a new line and it fails then break. Would this mean that if someone returns a blank command then break? 

Of course, I'm not sure where cin.fail() comes from either, reading to do on that. 

DWhitney, would you like to add comments?


notes to look up. reference: cin query - what comes along with it.

according to the reference guide on cplusplus.com I can't find cin.fail() or any of those others. Could you post a link?

---

### Post by dwhitney67 on 2010-02-13
Code reposted with comments:
```

#include <iostream>

// Template function, that returns a value of type T,
// which for the most part, T can only be a basic data
// type or the STL string.  Note, for more complex data
// types (ie user-defined classes), an operator>>() method
// would need to be associated with that data type.
// A user-defined class would also require a copy-constructor.
// 
template <typename T>
T getInput(const char* prompt)
{
   using namespace std;

   // declare local object on the stack; this requires
   // that the data type T have a no-arg constructor.
   //
   T input;

   // loop forever until valid input is provided...
   //
   while (true) {
      cout << prompt;   // display the prompt
      cin  >> input;    // acquire input

      // after acquiring the user's input, the next
      // character better be a '\n', and the acquisition
      // of the input should have succeeded.  If so,
      // exit the loop.
      //
      if (cin.peek() == '\n' && !cin.fail()) break;

      // If we are here, the user entered invalid data.
      // Let them know.  Also clear the errors from the
      // cin stream, and clear remaining crap from the
      // stream up to and including the newline character.
      //
      cout << "Invalid input!  Try again...\n" << endl;
      cin.clear();
      cin.ignore(1024, '\n');
   }

   return input;
}

int main()
{
   // declare a local variable, and assign it the value
   // returned by getInput.
   // getInput() is a template function, thus we need to
   // tell it the type of data we want; in this case, we
   // want an unsigned int.
   // The value passed to the getInput() method is a string
   // that represents what we want to prompt the user with.
   //
   unsigned int response = getInput<unsigned int>("Enter a number: ");

   // do something with 'response' ...
}

```


P.S.  The code is above is merely an example; it is not bullet-proof, nor should it be used for open-heart surgery.

---

### Post by MadCow108 on 2010-02-13
cin is a instance of istream
You'll find all functions of cin on the istream site
[http://www.cplusplus.com/reference/iostream/ios/fail/](http://www.cplusplus.com/reference/iostream/ios/fail/)

streams work as followed:
you give them a a type which it should read from the stream, in your case an int
depending on the type cin internally tries to extract the that type from the stream. How it does it depend on the type. Reading a char is simple, reading a float requires more work.
But you don't really have to bother how it works. What is important is that if the extraction fails for some reason the failbit or badbit is set (depending on the kind of error) and the stream is left in its current erroneous state.
A reason for failure is for example expecting a integer number and encountering a non-digit char

So all you have to do to check if the input operation was successful is to check if the fail or badbit was set. This is exactly what fail() does.
If it was set you now have to reset the stream because most stream operations only work on non-erroneous streams, you do this with clear()
And you also have to ignore what is currently in the stream buffer or it will try to extract from the same buffer and fail again, you do this with ignore(number, delimiter). This discards number elements or until it encounters the delimiter.
Now you have a functional stream again and can continue. To discard all you just use a high number or better the maximum size a stream can have determined from the limits header

the peek in dwhitney's function was probably something he required.
You generally don't really need it. It may even be harmful as some people may delimit their input with EOF (ctrl D) instead of a newline (but in this case also adapt the ignore function delimiter)

---

### Post by Enrui on 2010-02-13
I can't 'see' how Dwhitney's version validates data unless I replace '\n' with the values I want it to either screen in or screen out. I do however want to screen out letters and I don't see how this template could do it. 

Madcow your version also doesn't seem to deal with screening out characters. Although numeric_limits might help. 

Isn't there a better way to limit the input to just a valid set of natural numbers else invalid data? 

(confusion due to not enough knowledge more than likely)

hang on...

specific to Dwhitney's code. 

Does that make sure that the inputted data is actually an int and not a char or otherwise? (just for clarification)

Okay working on implementation getInput wants to be declared apparently


These are the errors I get back

```

error: &#8216;getInput&#8217; was not declared in this scope
127: error: expected primary-expression before &#8216;unsigned&#8217;
127: error: expected &#8216;,&#8217; or &#8216;;&#8217; before &#8216;unsigned&#8217;

```and the line is almost == yours in main()

---

### Post by MadCow108 on 2010-02-13
neither my nor dwhitneys code check the actual inputed values.

Streams just check if the inputed data matches the type (int, char, float etc.) requested and nothing else (and it does that under the hood, you can't 'see' it except you look at the sourcecode of the streams themself).

All further handling of that data is up to you.

@your error: getInput must be declared before use so the compiler knows what to do with the expression. Either by placing the whole body above the usage or by providing a prototype above it.

---

### Post by Enrui on 2010-02-13
I thought as much. I'm using dwhitney's in this case, because... //valid excuse what's a valid excuse...erm...// because it clicked :D I really don't know why, if I chose yours that'd be less lines of code that's for certain, but templates is something I probably should get into sooner rather than later.

@Madcow:

Ooh, I see, prototype it is, I'm assuming that getInput is a void type?

---

### Post by MadCow108 on 2010-02-13
I missed that its a template function. Templates are any type you want them be. Also these can't be be prototyped. You'll have to put the body above the use.

Also I just posted a snippet to solve your loop problem, it does not do much on its own. If you look sharply you see the exact same code is also in dwhitney's complete example

---

### Post by Enrui on 2010-02-13
my mistake... error was on my part.

---

### Post by Enrui on 2010-02-13
Dwhitney, you're a genius. Thanks for the help and thank you Madcow for all of those explanations.

---

