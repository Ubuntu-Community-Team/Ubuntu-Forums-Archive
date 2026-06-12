---
title: "STUCK: file input problem with c++"
date: 2008-05-18
forum: Programming Talk
---

### Post by nite owl on 2008-05-18
Hi I am completely stuck on this problem. Id be fine if there was just a number and then a new line, but I am unsure of how to get c++ to differentiate between the commas and brackets between numbers and filter each into separate variables?

Here's a sample of the file below :

[0,7,19,3,1092][1,5,16,4,1064][2,15,14,3,1740][3,4,5,3,108]

So basically I am stuck on how you'd filter the numbers from the text file when there arranged like this and read them into a c++ program?

---

### Post by SledgeHammer_999 on 2008-05-18
maybe, read each line in a string and then parse the string into whatever you want.

---

### Post by nite owl on 2008-05-18
> **SledgeHammer_999 said:**
> maybe, read each line in a string and then parse the string into whatever you want.

thanks for your reply :) I don't that would work though.

Imagine a plain old .txt file filled with 100+ of the entries 

[23,434,5,3411][5,34,3453,35]...etc

All next to one another separated by blocks of brackets with no new lines separating each one, and inside each entry is 4 integers of variable lengths separated by commas i.e. as above.

How would you separate each entry from one another and then order the integers in each into variable? So basically I already have designed the classes and variables etc.. The whole program is done besides the feeding of this file into it which I am completely stuck on.

---

### Post by SledgeHammer_999 on 2008-05-18
I understand what you are saying. Here's another solution:
1.[Have a look at this tutorial](http://www.cplusplus.com/doc/tutorial/files.html)
2.[Have a look at the overloaded get() method of istream](http://www.cplusplus.com/reference/iostream/istream/get.html) I think the "istream& get (char* s, streamsize n, char delim ); " is the one for you.

---

### Post by nvteighen on 2008-05-18
Are you required to use that file format??

I don't think it can be that difficult to get your program recognize the format and read in one step using a formatted string reading function (like fscanf() in C). C++ should have something like that...

---

### Post by dwhitney67 on 2008-05-18
Here's a solution using the istringstream container:
[PHP]#include <fstream>
#include <sstream>
#include <vector>
#include <iostream>

using namespace std;


struct Values
{
  int val1;
  int val2;
  int val3;
  int val4;

  friend istream& operator>>( istream &is, Values &values )
  {
    char dontCare;

    is >> dontCare           // open bracket
       >> values.val1
       >> dontCare           // comma
       >> values.val2
       >> dontCare           // comma
       >> values.val3
       >> dontCare           // comma
       >> values.val4
       >> dontCare;          // close bracket

    return is;
  }

  friend ostream& operator<<( ostream &os, const Values &values )
  {
    os << "["
       << values.val1
       << ","
       << values.val2
       << ","
       << values.val3
       << ","
       << values.val4
       << "]";

    return os;
  }
};


typedef vector< Values > AllValues;


int main( int argc, char **argv )
{
  if ( argc != 2 )
  {
    cout << "Usage: " << argv[0] << " <filename>" << endl;
    return 1;
  }

  fstream   fs( argv[1], ios::in );   // open data file
  char      buf[1024] = {0};
  AllValues allValues;

  if ( !fs )
  {
    cout << "Error:  Failed to open file" << argv[1] << endl;
    return 1;
  }

  while ( fs.getline( buf, sizeof buf ) )    // read single line from file
  {
    istringstream istr( buf );   // place buf into istringstream container
    Values values;               // declare a Values object

    while ( istr >> values )     // get Values data from istr
    {
      allValues.push_back( values );   // put into vector
    }
  }

  // display results
  for ( unsigned int i = 0; i < allValues.size(); ++i )
  {
    cout << allValues[i] << endl;
  }

  return 0;
} [/PHP]

---

### Post by dempl_dempl on 2008-05-18
I would use    [stringstream]("http://www.cplusplus.com/reference/iostream/stringstream/") class .

Cheers!

---

### Post by nite owl on 2008-05-18
Thankyou very much for all your responses. I haven't had time to look over them in detail yet which I'm sure will take me just a little bit of time. Especially thanks to 'dwhitney67' for your detailed response, was not expecting all this :)

---

### Post by slavik on 2008-05-18
why not just read in integers? doesn't operator>>() ignore non-digit characters when you are reading an integer?

---

### Post by nite owl on 2008-05-18
In regards to the source code whitney67 provided I am still a little unclear where you would put the name of the file to access in it i.e. "myfile.txt"

---

### Post by SledgeHammer_999 on 2008-05-18
Replace "argv[1]" with your filename. The source code assumes that the filename is given as a parameter when the program launches(eg myexe.exe c:\file.txt)

---

### Post by dwhitney67 on 2008-05-18
> **slavik said:**
> why not just read in integers? doesn't operator>>() ignore non-digit characters when you are reading an integer?
operator>>() must be implemented, and when doing so, it must read all characters/strings/values that are and are not wanted.

---

### Post by slavik on 2008-05-18
I meant the generic function, not the specific one operator>>(void) (because it can't usefully exist anyway).

IOW: C's scanf() when reading %d (decimal numbers) will skip over whitespace (maybe commas, too, haven't checked).

---

### Post by dwhitney67 on 2008-05-18
> **slavik said:**
> I meant the generic function, not the specific one operator>>(void) (because it can't usefully exist anyway).

IOW: C's scanf() when reading %d (decimal numbers) will skip over whitespace (maybe commas, too, haven't checked).
In this respect, you are correct.  The format statement in scanf() can be set up to skip unwanted characters.  For example:

[PHP]
int val1, val2, val3, val4;
scanf( "[%d,%d,%d,%d]", &val1, &val2, &val3, &val4 );
[/PHP]

The same applies to fscanf().

---

### Post by slavik on 2008-05-19
> **dwhitney67 said:**
> In this respect, you are correct.  The format statement in scanf() can be set up to skip unwanted characters.  For example:

[PHP]
int val1, val2, val3, val4;
scanf( "[%d,%d,%d,%d]", &val1, &val2, &val3, &val4 );
[/PHP]

The same applies to fscanf().

I think just calling scanf("%d", &val); will skip over the non-digit characters. (I have not tested it for non-whitespace characters, but I know it is true for whitespace).

---

### Post by dwhitney67 on 2008-05-19
Yes, it will skip whitespace(s), but for non-whitespace(s) it will not.  I know for a fact.

Thus a *scanf( "%d", &val1 )* would "choke" if I gave it input such as ',1'.

---

