---
title: "Convert C++ String to Integer"
date: 2007-03-29
forum: Programming Talk
---

### Post by DivineOmega on 2007-03-29
What would be the best way to convert a standard C++ string into an integer

---

### Post by thethawav on 2007-03-29
You mean something like string a[]="64000" into b = 64000?
its as simple as that:
b = atoi(a);

---

### Post by Wybiral on 2007-03-29
Well, with a C++ string, it should be converted to a C string first. This is easy...

integer = atoi( my_string.c_str() );

---

### Post by lnostdal on 2007-03-29
use stringstream for this stuff:

```

#include <iostream>
#include <sstream>

int main()
{
  using namespace std;

  string s = "1234";
  stringstream ss(s); // Could of course also have done ss("1234") directly.
  
  int i;
  ss >> i;
  cout << i << endl;
  
  return 0;
}

```

---

### Post by Wybiral on 2007-03-29
lnostdal is correct. "atoi" is more of the C way of doing it (which is why we have to convert it to a C style string), while lnostdals way is much more C++ esque. But either way will work.

---

### Post by hod139 on 2007-03-29
Actually, you shouldn't use atoi, not even in C.  The problem is that if atoi fails, it returns a 0.  But, if you are converting 0, you also get 0!  Therefore, error detection becomes impossible.  In C you should use sscanf.  For example

```

#include <stdio.h>

int main()
{
  const char* s = "1234";
  int i = 0;
  
  if(sscanf(s, "%d", &i) == EOF)
  {
     //error
  }
  
  return 0;
}

```Now you can detect if a failure occurred. If you want to convert it to a different format, all you have to do is change the format specifier.  For example, to convert to a double  you change "%d" to "%lf".  Be careful that the variable type you want to convert it to matches the format specifier, good ol C doesn't bother to check stuff like that :)

In C++ you use string streams because
1) you can detect conversion failures.  lnostdal didn't check in his example, so hopefully he won't mind me adding to his

```

#include <iostream>
#include <sstream>

int main()
{
  using namespace std;

  string s = "1234";
  stringstream ss(s); // Could of course also have done ss("1234") directly.
  
  int i;
  
  if( (ss >> i).fail() )
  {
     //error
  }
  
  cout << i << endl;
  
  return 0;
}

```2) Using string streams is type safe.  Don't get that with the C way.

---

### Post by thumper on 2007-03-29
Personally these days I use boost::lexical_cast.

```

#include <boost/lexcal_cast.hpp>

// ...
int i = 42;
std::string s = boost::lexical_cast<std::string>(i);
int j = boost::lexical_cast<int>(s)

```

---

### Post by nadamsieee on 2007-09-24
```
#include <iostream>
#include <limits>

using namespace std;

int main ( int argc, char* argv[] )
{
   int i;
   cout << "enter an interger (or some random garbage): ";
   cout.flush();
   while ( (cin >> i).fail() )
   {
      // clear the error flag in the cin object
      cin.clear();
      // discard the erroneous user input
      cin.ignore(numeric_limits<streamsize>::max(), '\n');
      cout << "ooops! please try again: ";
      cout.flush();
   }
   cout << "thank you for entering " << i << endl;
}
```

This technique should be applicable to other stream objects and other non-integer types.

[http://www.cplusplus.com/reference/iostream/ios/fail.html](http://www.cplusplus.com/reference/iostream/ios/fail.html)
[http://www.cplusplus.com/reference/iostream/ios/clear.html](http://www.cplusplus.com/reference/iostream/ios/clear.html)
[http://www.cplusplus.com/reference/iostream/istream/ignore.html](http://www.cplusplus.com/reference/iostream/istream/ignore.html)
[http://www.cplusplus.com/reference/iostream/streamsize.html](http://www.cplusplus.com/reference/iostream/streamsize.html)
[http://publib.boulder.ibm.com/infocenter/comphelp/v9v111/index.jsp?topic=/com.ibm.xlcpp9.aix.doc/standlib/header_limits.htm](http://publib.boulder.ibm.com/infocenter/comphelp/v9v111/index.jsp?topic=/com.ibm.xlcpp9.aix.doc/standlib/header_limits.htm)

---

### Post by public_void on 2007-09-24
Could use strtol function. 

long int strtol (const char *restrict STRING, char        **restrict TAILPTR, int BASE)

It uses TAILPTR to indicate the end of the value. This is much better than using the return value.

---

### Post by aks44 on 2007-09-24
> **public_void said:**
> Could use strtol function.

Again, that's plain old C.

As noted previously, boost::lexical_cast is a very good C++ solution (the cleanest IMHO), unless for some reason you don't want to use boost in which case std::stringstream is the way to go.

The big advantage of boost::lexical_cast is that it throws an exception on error, no need to add clutter for error checking.

---

### Post by hod139 on 2007-09-24
What an old thread to suddenly revive.  Anyways, 

> **aks44 said:**
> 
As noted previously, boost::lexical_cast is a very good C++ solution (the cleanest IMHO), unless for some reason you don't want to use boost in which case std::stringstream is the way to go.

The big advantage of boost::lexical_cast is that it throws an exception on error, no need to add clutter for error checking.

Boost's lexical cast is just a wrapper on top of stringstream; stringstreams will throw exceptions that you can catch so I don't understand why you consider it an advantage to boost.  I agree 100% that lexical_cast cleans up the syntax a ton, but it doesn't really add anything else.

Herb Sutter has a great article about string formatters that is very relevant to this thread: [http://www.gotw.ca/publications/mill19.htm](http://www.gotw.ca/publications/mill19.htm)

---

### Post by aks44 on 2007-09-25
> **hod139 said:**
> stringstreams will throw exceptions that you can catch so I don't understand why you consider it an advantage to boost.

Granted, stringstreams can throw if you throw (!) more garbage in, namely calling the exceptions() method. But by default they don't.

I guess I'm just very exception-centric when it comes to error reporting, since exceptions lead to much cleaner & stable code than manually checking return codes IMHO (you can hardly avoid an exception by inadvertance...).


I guess I should have written
> **aks44 said:**
> The big advantage of boost::lexical_cast is that **by default** it throws an exception on error, no need to add clutter for error checking. ;)

---

### Post by elfinkind on 2010-09-26
First, I admit I'm a beginner. Second, I admit that I am in over my head. This is part of a learning exercise I came up with on my own and am having trouble fine tuning. The rest of the program is exactly right; this one problem is giving me hell!

I am trying to convert a 4 digit int to a string, loop to the end of the string ('/0'), then backtrack to obtain the last 2 places and convert those back to (eventually!) a single int. The reason for this is to separate the numbers without prior knowledge of the numbers. 

Here is my first attempt:

```


int fourDigitIn, tensPlace, onesPlace, twoDigitOut;
int a = 0;

char iterator[];

cin >> fourDigitIn;

itoa (fourDigitIn, iterator, 10);

while (iterator[a] != '/0')
{ a++ }

const char ten = iterator[a-2];
const char one = iterator[a-1];

tensPlace = atoi (&ten);
onesPlace = atoi (&one);

twoDigitOut = tensPlace + onesPlace;

cout << twoDigitOut << endl;


```Output from the above bit of code, when the user inputs 2956, for example, returns a value of 62 to twoDigitOut rather than the expected 56. Further testing indicates that the above code will always add the ones back into itself twice rather than the expected once, so that user input of 6789 will return 98 rather than 89, user input of 1234 will return 38 rather than 34, and so on.

Ok, so I have something odd going on here. To attempt to combat this problem, I tried:

```


twoDigitOut = (tensPlace * 10) + onesPlace;


```The return on that for the same user input of 2956 is 566. This obviously didn't work, either. 

I tried to comment out the lines that set the onesPlace variable and output the tensPlace only, like this:

```


int fourDigitIn, tensPlace, onesPlace, twoDigitOut;
int a = 0;

char iterator[];

cin >> fourDigitIn;

itoa (fourDigitIn, iterator, 10);

while (iterator[a] != '/0')
{ a++ }

const char ten = iterator[a-2];
//const char one = iterator[a-1];

tensPlace = atoi (&ten);
//onesPlace = atoi (&one);

twoDigitOut = tensPlace;// + onesPlace;

cout << twoDigitOut << endl;


```My reasoning was that if multiplying my tensPlace by 10 and adding the onesPlace to it produced 566, and that if adding the tensPlace and onesPlace produced 62, then my tensPlace was producing the needed two digit output I desired. However, the return on that same user input of 2956 now produced an output of 25. Checking other input repeatedly shows me that the code now ignored the ones place completely and returned half of the resulting tens value. Any input with 5 in the tens place produced 25, any input with 7 in the tens place produced 35, and so on. 

Can anyone help me figure out what I need to do to settle this?

Thank you!

---

### Post by GeneralZod on 2010-09-26
> **elfinkind said:**
> snip

This doesn't compile, here: you have no size for the iterator array, and the a++ needs a semicolon.  Please post the full, compileable code :)

---

### Post by elfinkind on 2010-09-26
> **GeneralZod said:**
> This doesn't compile, here: you have no size for the iterator array, and the a++ needs a semicolon.  Please post the full, compileable code :)

Yep, like I said when I edited it - I managed to mis-type some of it...

Ok, try it with those fixes in place, including the entire code as it appears in Microsoft Visual C++ 2010 Express (and while I'm at it, I'll comment it so you know what I was thinking):

```

#include "stdafx.h"
#include <iostream>
#include <string>

int _tmain(int argc, _TCHAR* argv[])
{

int fourDigitIn, tensPlace, onesPlace, twoDigitOut; 
int a = 0, b;  

char iterator[50];  [COLOR=Red]// declare character array with WAY more positions than I need, 
just because[/COLOR]

cin >> fourDigitIn;  [COLOR=Red]// request input from user - don't cheat, stay within the scope 
of the array[/COLOR]

itoa (fourDigitIn, iterator, 10);  [COLOR=Red]// this changes the int fourDigitIn to char iterator. 
the 10 is there to indicate that it needs to be stored as a base ten number in the array[/COLOR]

while (iterator[a] != '/0') [COLOR=Red]// this counts int a up through the array positions until it 
reaches the end, or null so I can work backward through it to the last two numbers[/COLOR]
{ a++; }  

const char ten = iterator[a-2]; [COLOR=Red]// here I declare two const char variables and assign 
them the values I need from the iterator array[/COLOR]
const char one = iterator[a-1];  

tensPlace = atoi (&ten); [COLOR=Red]// here I change each const char back to int values. my intent 
here was to acquire the value of the tens position and the ones position[/COLOR]
onesPlace = atoi (&one);  

twoDigitOut = tensPlace + onesPlace;  [COLOR=Red]// here I attempted to combine the two ints 
into a single number
[/COLOR] 
cout << twoDigitOut << endl; [COLOR=Red]// output the result for validation[/COLOR]

cout << "This is just to pause the console so output can be checked." << endl;
cout << "Press any key followed by enter to end: " << endl;

cin >> b;

return 0;

}

```Knowing my luck, I'm just stuck because I'm using the express version, and it won't do everything I need it to do. That would be par for the course...

---

### Post by GeneralZod on 2010-09-26
> **elfinkind said:**
> 

```

tensPlace = atoi (&ten); [COLOR=Red]// here I change each const char back to int values. my intent 
here was to acquire the value of the tens position and the ones position[/COLOR]
onesPlace = atoi (&one);  


```

atoi expects a null-terminated string, which &ten and &one are not (they are pointers to a single char).

Edit:

Also, a null char is \0, not /0 :)

---

### Post by elfinkind on 2010-09-26
> **GeneralZod said:**
> atoi expects a null-terminated string, which &ten and &one are not (they are pointers to a single char).

That brings me back to my original question - can you help me with the code I will need to make this happen? I feel that I explained myself quite well, but if there is still doubt, I will attempt to explain again in better detail. I also stated from the outset that I am a beginner, and that was intended to mean that I need more than just a hint - I have searched and searched, and this was the best I could come up with on my limited experience.

Thanks!

---

### Post by lloyd_b on 2010-09-26
> **elfinkind said:**
> That brings me back to my original question - can you help me with the code I will need to make this happen? I feel that I explained myself quite well, but if there is still doubt, I will attempt to explain again in better detail. I also stated from the outset that I am a beginner, and that was intended to mean that I need more than just a hint - I have searched and searched, and this was the best I could come up with on my limited experience.

Thanks!

Why exactly are you using strings to get the last two digits?  It would be much simpler to just do something do a something like```
twoDigitOut = fourDigitIn % 100
``` and then format the output to 2 places with leading zeros...

Lloyd B.

---

### Post by elfinkind on 2010-09-27
Ok, will try that, and see what happens.

Thank you!

---

### Post by Geek10 on 2010-09-27
I'm only a beginner in programming too, but I recently did a C++ bit of code that applies. Note that the number I read in was from a large text file, however, I think you could just put in the name of your string where "AddressOfNumberInTextFile" is.

I initialised imgNum earlier in the code as an integer. which is why "numberStream >> imgNum" converts the character stream to a number successfully.

```

string numberString = bufferString.substr(AddressOfNumberInTextFile);

// stringstream provides an interface to manipulate strings as if they were input/output streams. 
stringstream numberStream(numberString); 

if((numberStream >> imgNum).fail()){    // Convert stream to integer
         cout << "ERROR: Failed string to integer conversion";
}
cout << "imgNum integer: " << imgNum << endl;

```

---

### Post by elfinkind on 2010-09-27
Using the modulus was exactly the key I needed. My code works perfectly, now, and I thank you, Lloyd B.!

I also had an instance where I needed the digit in the tenths position of a double. Your solution worked there as well - I multiplied the double by 10, assigned it to an int, and used modulus 10 to get the proper result. AWESOME!

I have always felt that the most elegant code is the most simple code, and your solution, while kicking me in the *** for being dumb enough to miss it, also simplifies my code, thereby making it more elegant, imho. Thank you again!

---

