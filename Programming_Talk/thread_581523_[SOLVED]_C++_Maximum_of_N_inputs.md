---
title: "[SOLVED] C++ Maximum of N inputs"
date: 2007-10-19
forum: Programming Talk
---

### Post by TreeFinger on 2007-10-19
I wrote a program that finds the maximum number out of n inputs. Right now the program can not really include negative numbers because I am using a sentinel value of -1. My question is how could I have the user type a character to stop the loop and output the maximum value? Here is my code right now..

```

//finds maximum of n numbers
#include <iostream>
using namespace std;
int maxn();
void main() {
	cout << "Enter as many numbers as you want and I will tell you the maximum.\n";
	cout << "The maximum number is:" << maxn() << endl;
}

int maxn() {
	int max = 0;
	int n = 0;
	
	cout << "Enter first number. Enter -1 when you want to stop.\n";
	while ( n != -1 ) {
	cin >> n;
		if ( n > max ) {
			max = n;
		}
		else
			continue;
	}
	return max;
}

```

I am not sure about this because the input is an integer. I have no idea how to come to a solution for this problem. I'll take some hints if you guys don't want to give me a complete answer. Thanks for the time. Also any tips on improving my code readability/efficiency would be appreciated.

---

### Post by xtacocorex on 2007-10-19
You could input a string and then have a stringstream type convert to an int for you, then you could end the loop with a "q".
 
Or you could use the error catch of inputting a char into an int as a way to stop the loop; but that's a really dirty method and probably wouldn't go over to well if you're turning this in for a grade.
 
EDIT:
You always want main to be an integer function that returns 0; just good programming practice at least for C and C++.
```

int main()
{
    // Code segments
 
    return 0;
}

```

---

### Post by aks44 on 2007-10-19
```
#include <iostream>
#include <sstream>

bool getNumber(int& number)
{
  std::cout << "Enter a number (or an empty line to end): ";

  while (true)
  {
    std::stringstream ss;
    std::cin.get(*ss.rdbuf());
    std::cin.ignore(); // get rid of the newline
  
    if (!ss.rdbuf()->in_avail()) // nothing in the buffer?
      return false;

    int num;
    ss >> num;
    if (!ss.fail()) // extraction successful
    {
      // check for non-whitespace trailing characters
      std::string ws;
      ss >> ws;
      if (ss.fail())
      {
        // nothing or only whitespace was left
        number = num; // (*)
        return true;
      };
    };

    std::cout << "You entered garbage, try again: ";
  };
}


int main()
{
  int n;

  while (getNumber(n))
    std::cout << "=> You entered " << n << std::endl;

  std::cout << "=> Goodbye!" << std::endl;
  return 0;
}

```

(*) As a side note, better try not to modify anything outside the function (even the object's state if you're in a member function) until you know for sure that you are successful.


> **xtacocorex said:**
> You always want main to be an integer function that returns 0; just good programming practice at least for C and C++.

Not only "good practice" but also mandated by the standard. :)

---

### Post by slavik on 2007-10-19
ask for EOF (Ctrl-D) instead of -1 :)

---

### Post by TreeFinger on 2007-10-21
Well I still haven't come to a solution for the problem.

aks44 - I don't understand your code :x Seems to advanced for me.

How do I implement Ctrl-D to end the input? When I hit ctrl-d while running the program on windows right now it just stops and doesn't display the max number.

I usually do have my main function as an int. I was just in class on Friday and my professor uses void main() a lot.  I'll go back to my usual way of int main() :)

I also have another question. I might just forget this... but how do I return 2 values from a function? Like say I wanted to return the max and min. Is it possible?


---

I am thinking the best way to do this with my current knowledge is a switch statement. I'd have the program ask the user if he/she would like to input another number. If user selects Yes it will accept input for the integer. If user selects N it will display the current max number.

---

### Post by dwhitney67 on 2007-10-21
You need to talk to your professor/teacher about getting the requirements for your project... the first step for any project.  It seems that you are unsure if negative numbers should be accepted or not.  If you do not have to worry about them, then I think your original solution (of checking for a -1) will suffice.

If you must accept negative numbers, are you permitted to limit the user to a range of numbers, say -99 to +99?  If you must accept all possible numbers, then in a previous post, someone suggested that you read the given input as a string, thus allowing the operator to enter "q" when they want to quit.  The string, if not "q", then should be converted to a number.

This might be a little advanced for your course, but this is how one could do such a thing:

[PHP]#include <iostream>
#include <string>
#include <sstream>

using namespace std;


int main( int argc, char** argv )
{
  cout << "Enter some numbers, and I will tell you which is the largest." << endl;
  cout << "When you are done entering numbers, enter 'q' to quit." << endl;
  cout << endl;

  string input;
  int maxNum = 0;
  bool maxKnown = false;  // since the initial max num is not yet known.

  while ( 1 )
  {
    cout << "Number (or 'q' to quit): ";
    cin >> input;

    if ( input == "q" )
    {
      break;
    }
    else
    {
      istringstream str( input );
      int num;

      str >> num;

      if ( !maxKnown )
      {
        maxNum = num;
        maxKnown = true;
      }
      else
      {
        maxNum = ( maxNum > num ? maxNum : num );
      }
    }
  }

  cout << "The maximum number entered was " << maxNum << endl;
}[/PHP]

---

### Post by TreeFinger on 2007-10-21
This isn't a project :)
I am doing this for myself.

---

### Post by dwhitney67 on 2007-10-21
Oh, well then use the solution I provided.  If you have any questions... post them.

---

### Post by TreeFinger on 2007-10-21
```

//finds maximum of n numbers
#include <iostream>
using namespace std;

int main() {
	cout << "I will find the maximum if numbers you enter.\n";
	bool enterNumber = true;
	int n;
	int max = -99999;

	while ( enterNumber ) {
		  cout << "Would you like to enter a number? (Y/N):";
		  char yesOrNo;
		  cin >> yesOrNo;
		  switch ( yesOrNo )
		  {
		   		 case 'Y':
		   		 case 'y': { cout << "Enter next number: ";
					  cin >> n;
					  if ( n > max )
					 	 max = n; }
						 break;
		   		case 'n':
		  		case 'N':{ enterNumber = false; cout << "The max number is " << max << endl; }
			}
	}
	int hold;
	cin >> hold;
	return 0;
}

```

Sorry for the sloppy code. I am not finding myself a fan of Dev-C++ IDE.

Seems to be working for me. From what I know of the programming language this seems to be the best solution.

---

### Post by aks44 on 2007-10-22
> **TreeFinger said:**
> aks44 - I don't understand your code

So I'll try to explain it... :)

```
#include <iostream>
#include <sstream>

// getNumber() doesn't return until either
// - a correct number has been entered (returns true, updates "number" parameter)
// - the user hit Enter without entering anything else (empty line, returns false)
// IOW the return value is whether the user entered a number (true)
// or wants to quit (false)
// If the user doesn't enter what is expected, (s)he is asked again.
bool getNumber(int& number)
{
  std::cout << "Enter a number (or an empty line to end): ";

  // infinite loop until a correct number or an empty line has been entered
  while (true)
  {
    // std::stringstream is used both to
    // - check for empty string
    // - extract the number
    std::stringstream ss;
    // std::cin.get() reads stdin until a newline is met
    // it needs a std::stringbuffer to put the data,
    // which is provided  by std::stringstream::rdbuf()
    std::cin.get(*ss.rdbuf());
    // std::cin.get() leaves the newline in the stdin buffer, so we need to get rid of it
    std::cin.ignore(); // discard one character from stdin
  
    // std::stringbuffer::in_avail() is the number of characters in the string buffer
    // if no character has been read (eg. empty line) then we return from the function
    // I could have written "if (ss.rdbuf()->in_avail() == 0)" too
    if (!ss.rdbuf()->in_avail())
      return false;

    int num;
    // there are characters in the string buffer, we try to extract an integer
    ss >> num;
    // std::stringstream::fail() tells whether the previous operation failed
    if (!ss.fail()) // extraction successful
    {
      // check for non-whitespace trailing characters
      // that's a trick... extracting a std::string from a stream will ignore
      // any heading whitespaces
      // so if the string buffer contains either nothing or only whitespace,
      // we'll end up with our string empty AND a failure to extract
      std::string ws;
      ss >> ws;
      if (ss.fail())
      {
        // nothing or only whitespace was left
        // so the number was indeed correct (no trailing non-whitespace)
        // we update the return parameter and return true
        number = num;
        return true;
      };
    };

    // we didn't return from the function, the user didn't enter an empty line
    // nor a correct number, so we display a message and loop again
    std::cout << "You entered garbage, try again: ";
  };
}


int main()
{
  int n;

  // as long as the user entered a number
  while (getNumber(n))
    // display it
    std::cout << "=> You entered " << n << std::endl;

  std::cout << "=> Goodbye!" << std::endl;
  return 0;
}

```

Hope this helps :)



> **TreeFinger said:**
> how do I return 2 values from a function? Like say I wanted to return the max and min. Is it possible?

You can only return a single value from a function.
The most common way to have a function retrun multiple arguments is to pass them as reference arguments :

```
void function(int& outputParam1, int& outputParam2)
{
  outputParam1 = /*...*/;
  outputParam2 = /*...*/;
}
```

You could also return a std:: pair<int,int> to achieve the same result, but it becomes tricky when you must return 3 or more values, so as a matter of uniformity you'd better use the reference-arguments pattern.

As a side note, that's again a case where const correctness is important. An input parameter should be a const reference, non-const references should be reserved for output parameters:

```
void function(const int& inputParam, int& outputParam)
{
  outputParam = inputParam * 2;
}
```


That way you can tell at a glance from the declaration which purpose has each parameter (granted, no point passing a const int& but that's mostly for making the other point).

---

