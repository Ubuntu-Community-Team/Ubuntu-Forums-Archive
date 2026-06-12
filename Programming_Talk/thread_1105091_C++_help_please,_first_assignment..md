---
title: "C++ help please, first assignment."
date: 2009-03-24
forum: Programming Talk
---

### Post by Garratt on 2009-03-24
Hi, please don't be alarmed by the wall of text, it is mostly sorted.

well after dropping out last semester due to numbers of reasons, i now re-enrolled in uni to repeat, 4 weeks late only to have my g/f pop out a baby the very next day.... anyway couple weeks later i decide i better start going (week 7), so head on down and receive my first assignment which was due in 4 days.... last sunday, anyway pulled off a bit of an extension so it's not all bad.

I haven't had much experience, and haven't touched any code in over 4 months so I am a little rusty.

The problem:

Count the number of a) non blank characters, b) number of lines, c) length of longest line, and d) number of times longest line occurs
You are to use the C++ string class to solve this problem. No C strings or C string routines are to be used.
You are to write a test script. Your test data is to be placed in the directory &#8221;data&#8221; and your script is to access these test files.
You are to use shell I/O redirection to &#8221;input&#8221; data to your executable.

ok! so my test script is fine, i think and a hell of a lot simpler than the example the teacher gave us (which was a huge wall of text redirecting over 30 files into a.exe):

```
#!/bin/sh
##
#######################
##  Test File for    ##
##  Assignment 1     ##
##  Semester 1 09    ##
#######################
##   Author :        ##
##   G.Campton       ##
#######################
##
#(1) Variables ;-) 

EXECUTABLE=a.exe
TEST_DIRECTORY=data
SOURCE=a1.cpp

##
#(2) Remove old .exe and recompile ;-)

rm -f ${EXECUTABLE}
g++ ${SOURCE}

##
#(3) print and test all files within /data ;-)

for i in ${TEST_DIRECTORY}/*
   do

      echo "Testing file: $i"

      ${EXECUTABLE} < $i
   done

##
#(4) Exit with successful termination ;-)
exit 0
######

```

so that's my scripting assignment part done... the C++ on the other hand is proving to be a challenge.

There's a number of comments throughout and part's im pretty uncertain on, additionally compiling is giving me errors on the same parts i was unsure about in the first place, while my logic is pretty solid it's lack of code knowledge is my downfall.

Logic:
int lineCount, spaceCount, nonBlankCount, nonBlankCountTotal;
int longestLine, longestLineCount;
string line, s1;
s1=" ";
While loop to read in 1 line at a time, add 1 to lineCount, get line.length() and store in longestLine, count number of spaces, and take number of spaces from line.length() store in nonblanks

most of the problems i foresee are marked with ??? question marks
please take a look and any tips would be much appreciated.
the code: 

```
// A1.cpp assignment 1 semester 1 2009
// Author : "Garratt Campton"
// Date : Friday, 20-03-09


#include <iostream>
using std::cout;
using std::cin;
using std::endl;

#include <string>
using std::string;


int main()

{
    int spaceCnt, nonBlnkCnt, nonBlnkCntTotl, lineCnt;
    int longLine, longLineCnt;
    string line, s1;

    size_t where;
    // initialize all variables to 0
    lineCnt=0;
    spaceCnt=0;
    nonBlnkCnt=0;
    nonBlnkCntTotl=0;
    longLine=0;
    longLineCnt=0;

    s1=" "; // search string for spaces

    while (getline(cin, line))
    {
        // b) line counter
        lineCnt += 1;

        // c) longest line 
        if (line.length() > longLine)
        {
            longLine = line.length();
        }
        
        // a) non-blank char counter
        // finding first space
        where = line.find_first_of(s1);

        // if first found is a space
        if (line[where] == s2) //<---- is this valid ???
        {       
            // adding first space to count
            spaceCnt += 1;      
            
            // if length of string is longer
            // than the position of 'where'
            // search for more spaces

            // can this while statement work ???
            // was the only way i could think of without
            // making an infinite loop
            while (line[where] < line.length())
            {
                where = line.find_first_of(s1, where+1);
                spaceCnt +=1;
            }


        }
        else
        {
            // THIS LINE IS BLANK 
            // I shouldn't need an else in here
            // as variables simply wont count
            // a blank line such as this...
            // i think ???
        }
       
        // Here ??? casting int to string values
        // I'm going to see errors for sure
       nonBlnkCnt = line.length() - spaceCnt;
       nonBlnkCntTotl += nonBlnkCnt;
           
       // reinitialize variables somehow
       // need to set space-count and 
       // non-blank-count back to 0
       // possibly before while loop...?

            
    // end while
    }

    // d) number of longest lines
    // now count number of longest lines
    // using our stored longest-Line variable
    // check if variables will stay stored 
    // out of while loop ???

    while (getline(cin, line))
    {
        if (line.length() == longLine)
        {
            longLineCnt += 1;
        }
    }

    return 0;

}
```

the end, actually just while reading over my code i did have another idea for the non-blank count while loop:

If i search for first space, then use find_last_of storing in a separate variable such as whereLast. I could do something like

while ( line[where] < line[whereLast])
{
keep looking for spaces... using 'where'
}
or would this not change while value, for example, if i had spaces at 4, 6, 8, 13, 15, 19, 23, 28.
then it would be like saying
while ( 4 < 28 )
{
keep looking ---> would the 4 value change for each increment of 'where' ?
}

would this work? and I would still need to figure out how to cast variables to int counters for other values.

thanks for reading this far :D

---

### Post by dwhitney67 on 2009-03-24
First of all, consider declaring and initializing your variables in one-step.  For example:
```

    string line;
    string blank(" ");    // better name than s1!

    size_t where = string::npos;
    int lineCnt = 0;
    int spaceCnt = 0;
    int nonBlnkCnt = 0;
    int nonBlnkCntTotl = 0;
    int longLine = 0;
    int longLineCnt = 0;
...

```
The next thing is to check that 'where' does not equal std::string::npos in your code _after_ calling find_first_of(); otherwise if it does, your app is going to crash.

Also, I could not find the declaration for 's2', so I have no idea what that is.

Your loop for checking for additional spaces looks ok, but you need to test it to ensure that you get the desired results.

P.S.  Typically counts are never less than zero; thus you may want to consider declaring your count variables as 'unsigned int' values.

---

### Post by Garratt on 2009-03-24
in essence the logic behind the non-blank character count is these couple of lines.


        // Here ??? casting string values to int
        // I'm going to see errors for sure


       nonBlnkCnt = line.length() - spaceCnt;
       nonBlnkCntTotl = nonBlnkCntTotl + nonBlnkCnt;

---

### Post by Garratt on 2009-03-24
> **dwhitney67 said:**
> First of all, consider declaring and initializing your variables in one-step.  For example:
```

    string line;
    string blank(" ");    // better name than s1!

    size_t where = string::npos;
    int lineCnt = 0;
    int spaceCnt = 0;
    int nonBlnkCnt = 0;
    int nonBlnkCntTotl = 0;
    int longLine = 0;
    int longLineCnt = 0;
...

```
The next thing is to check that 'where' does not equal std::string::npos in your code _after_ calling find_first_of(); otherwise if it does, your app is going to crash.

Also, I could not find the declaration for 's2', so I have no idea what that is.

Your loop for checking for additional spaces looks ok, but you need to test it to ensure that you get the desired results.

P.S.  Typically counts are never less than zero; thus you may want to consider declaring your count variables as 'unsigned int' values.

Thanks that was fast, s2 is a typo, pretty sure it was meant to be s1, that said i will change to blank as a better naming convention.

---

### Post by dwhitney67 on 2009-03-24
> **Garratt said:**
> Thanks that was fast, s2 is a typo, pretty sure it was meant to be s1, that said i will change to blank as a better naming convention.

In that case, you really want to check to ensure that 'where' is not equal to std::string::npos.  If it is, then this implies that a blank space was _not_ found; otherwise a blank space was found, and hence the if-conditional where you check if the character within the 'line' string is a blank space (i.e. s2) is moot.

P.S.  You should also consider augmenting the 'blank' string for tab-spaces too.  I believe find_first_of() supports the specification of multiple delimiters.

Edit:  Yep, it does.  Here's a [link]("http://www.cplusplus.com/reference/string/string/find_first_of.html") to find_first_of().  Consider bookmarking the main-page of Cplusplus.com/reference.

---

### Post by Garratt on 2009-03-24
> **dwhitney67 said:**
> In that case, you really want to check to ensure that 'where' is not equal to std::string::npos.  If it is, then this implies that a blank space was _not_ found; otherwise a blank space was found, and hence the if-conditional where you check if the character within the 'line' string is a blank space (i.e. s2) is moot.

P.S.  You should also consider augmenting the 'blank' string for tab-spaces too.  I believe find_first_of() supports the specification of multiple delimiters.


By that do you mean placing 1 space, and 1 tab inside 'blank' so that find_first_of() will find either tabs or spaces? i just looked this up and i think that's right. didn't even cross my mind ;p

---

### Post by dwhitney67 on 2009-03-24
> **Garratt said:**
> in essence the logic behind the non-blank character count is these couple of lines.


        // Here ??? casting string values to int
        // I'm going to see errors for sure


       nonBlnkCnt = line.length() - spaceCnt;
       nonBlnkCntTotl = nonBlnkCntTotl + nonBlnkCnt;

Btw, I do not see any issues with the code above.  You're performing simple arithmetic.  Note that length() returns a size_t value.

---

### Post by dwhitney67 on 2009-03-24
> **Garratt said:**
> By that do you mean placing 1 space, and 1 tab inside 'blank' so that find_first_of() will find either tabs or spaces? i just looked this up and i think that's right. didn't even cross my mind ;p

Yes.  Something like:
```

string blank(" \t");

```

---

### Post by Garratt on 2009-03-24
cool i wasn't sure, I just noticed a few "cast" errors on first compile so assumed it might be whinging about it. ill try compile again after i fix it up a bit from your suggestions.

---

### Post by Garratt on 2009-03-24
ok I think that's worth a test run, assuming i placed string::npos in the right position.

```
// A1.cpp assignment 1 semester 1 2009
// Author : "Garratt Campton"
// Date : Friday, 20-03-09


#include <iostream>
using std::cout;
using std::cin;
using std::endl;

#include <string>
using std::string;


int main()

{
    // declare & initialize all variables to 0
    int lineCnt=0;
    int spaceCnt=0;
    int nonBlnkCnt=0;
    int nonBlnkCntTotl=0;
    int longLine=0;
    int longLineCnt=0;

    string line;
    string blank=" \t"; // search string for spaces

    size_t where;

    while (getline(cin, line))
    {
        // b) line counter
        lineCnt += 1;

        // c) longest line 
        if (line.length() > longLine)
        {
            longLine = line.length();
        }
        
        // a) non-blank char counter
        // finding first space
        where = line.find_first_of(blank);

        // if first found is a space
        if (where != string::npos) 
        {       
            // adding first space to count
            spaceCnt += 1;      
            
            // if length of string is longer
            // than the position of 'where'
            // search for more spaces
            while (line[where] < line.length())
            {
                where = line.find_first_of(blank, where+1);
                spaceCnt +=1;
            }


        }

        nonBlnkCnt = line.length() - spaceCnt;
        nonBlnkCntTotl += nonBlnkCnt;
           
        // reinitialize variables back to 0
        spaceCnt =0;
        nonBlnkCnt =0;

            
    // end while
    }

    // d) number of longest lines
    // now count number of longest lines
    // using our stored longest-Line variable
    while (getline(cin, line))
    {
        if (line.length() == longLine)
        {
            longLineCnt += 1;
        }
    }

    return 0;

}
```

---

### Post by Garratt on 2009-03-24
lol, compiles well.... no data?

oh YES cout statements help :P

---

### Post by dwhitney67 on 2009-03-24
I see a problem here:
```

...
            while (line[where] < line.length())
...

```
You probably meant to check if 'where' is less than (or equal?) than the line length.

Also, your app is capturing input (from a user?) via std::cin.  Thus, at the conclusion of you main function, I do not quite understand what you are doing here (that could be, or perhaps was, done before)...
```

    // d) number of longest lines
    // now count number of longest lines
    // using our stored longest-Line variable
    while (getline(cin, line))
    {
        if (line.length() == longLine)
        {
            longLineCnt += 1;
        }
    }

```

---

### Post by Garratt on 2009-03-24
> **dwhitney67 said:**
> I see a problem here:
```

...
            while (line[where] < line.length())
...

```
You probably meant to check if 'where' is less than (or equal?) than the line length.

Also, your app is capturing input (from a user?) via std::cin.  Thus, at the conclusion of you main function, I do not quite understand what you are doing here (that could be, or perhaps was, done before)...
```

    // d) number of longest lines
    // now count number of longest lines
    // using our stored longest-Line variable
    while (getline(cin, line))
    {
        if (line.length() == longLine)
        {
            longLineCnt += 1;
        }
    }

```

yes firstly ```
while (line[where] < line.length())
```  that's right, but line[where] gives a position, eg:
cout << "the position the space occurs in the string is: " << line[where] << endl;
printout would be:  4   (as an example)
so i figured it would work in this instance,
also the last part is counting the number of times the longest lines occurs, it is part d of the assignment, i couldn't find where to place it in the while loop as the value of the longest line is constantly changing, and I needed a separate algorithm to search the number of times the longest line appears once the file was completed, so I figured re-opening and searching using the value of longest line would work....

ALAS, 

I just compiled and ran my program, everything seemed to work perfectly on a test file i had:

```
This is a test file for looping exercise.
This is line 2.


This is line 5 and further down, 

     is line 7.

This is line 9 and hopefully end of file.     

```

so this counted the number of nonblanks, lines, and longest line i used wc -lmL to check and also did a manual count.

but the number of longest lines reported 0.

---

### Post by dwhitney67 on 2009-03-24
> **Garratt said:**
> ...that's right, but line[where] gives a position...

I do not have time to write a test program (I have to leave to run an errand), but I believe you are incorrect.  The line[where] (presuming 'where' is a valid index), will return the character within the string at that position.

So if 'line' = "Hello", and 'where' = 1, then line[where] would be 'e'.

Your program will be happy to compare 'e' with a length of a string (and not complain about it!), but I do not think that is what you want.

---

### Post by Garratt on 2009-03-24
> **dwhitney67 said:**
> I do not have time to write a test program (I have to leave to run an errand), but I believe you are incorrect.  The line[where] (presuming 'where' is a valid index), will return the character within the string at that position.

So if 'line' = "Hello", and 'where' = 1, then line[where] would be 'e'.

Your program will be happy to compare 'e' with a length of a string (and not complain about it!), but I do not think that is what you want.

ahhh ok, i'll check on that... you know what they say if it aint broke don't fix it :P


thanks for all your help i think i am just about done, except for the number the longest line appears, I'll have to try and rethink that code.

you have done a+ work

i hope :) 
takes a lot of pressure off me too, now i can concentrate on the java assignment due in 2 weeks.
edit: ^^ and more importantly look after bub.

I can't thank you enough.

---

### Post by Garratt on 2009-03-24
currently my code looks like this, it's 3am so i better get at least 2 hours sleep..

I thought that adding the second while loop at the bottom and re-reading the file checking for the amount of times the longest line appears would work, seeing that it should jump straight from the top while loop down to the next while.

```
// A1.cpp assignment 1 semester 1 2009
// Author : "Garratt Campton"
// Date : Friday, 20-03-09


#include <iostream>
using std::cout;
using std::cin;
using std::endl;

#include <string>
using std::string;


int main()

{
    // declare & initialize all variables to 0
    int lineCnt=0;
    int spaceCnt=0;
    int nonBlnkCnt=0;
    int nonBlnkCntTotl=0;
    int longLine=0;
    int longLineCnt=0;

    string line;
    string blank=" \t"; // search string for spaces or tabs

    size_t where;

    while (getline(cin, line))
    {
        // b) line counter
        lineCnt += 1;

        // c) longest line 
        if (line.length() > longLine)
        {
            longLine = line.length();
        }
        
        // a) non-blank char counter
        // finding first space
        where = line.find_first_of(blank);

        // if first found is a space
        if (where != string::npos) 
        {       
            // adding first space to count
            spaceCnt += 1;      
            
            // if length of string is longer
            // than the position of 'where'
            // search for more spaces
            while (where < line.length())
            {
                where = line.find_first_of(blank, where+1);
                spaceCnt +=1;
            }


        }

        nonBlnkCnt = line.length() - spaceCnt;
        nonBlnkCntTotl += nonBlnkCnt;
           
        // reinitialize variables back to 0
        spaceCnt =0;
        nonBlnkCnt =0;

            
    // end while
    }

    // d) number of longest lines
    // using our stored longest-Line variable
    while (getline(cin, line))
    {
        if (line.length() == longLine)
        {
            longLineCnt += 1;
        }
    }
    
    // print statements

    cout << " A) Number of non-blank characters: "
        << nonBlnkCntTotl << endl;
    cout << " B) Number of lines: " << lineCnt << endl;
    cout << " C) Length of longest line: "
        << longLine << endl;
    cout << " D) Number of longest lines: " 
        << longLineCnt << endl;

    return 0;
// end main
}


```

---

### Post by dwhitney67 on 2009-03-24
As you read the file the first time, insert this code in the loop:

```

size_t longLine = 0;
int    longLineCnt = 0;
...
size_t where;

while (getline(cin, line))
{
  ...
  if (line.length() > longLine)
  {
    longLine    = line.lenth();
    longLineCnt = 1;
  }
  else if (line.length() == longLine)
  {
    ++longLineCnt;
  }
}

...

```
This will obviate the need to read the file twice.

---

### Post by Garratt on 2009-03-24
> **dwhitney67 said:**
> As you read the file the first time, insert this code in the loop:

```

size_t longLine = 0;
int    longLineCnt = 0;
...
size_t where;

while (getline(cin, line))
{
  ...
  if (line.length() > longLine)
  {
    longLine    = line.lenth();
    longLineCnt = 1;
  }
  else if (line.length() == longLine)
  {
    ++longLineCnt;
  }
}

...

```
This will obviate the need to read the file twice.

I can't see that working but maybe i'm missing something, lets say for example the file contains:
```

1. This is
2. A small file
3.     with a couple
4. of tabs and spaces..

```

first, being that longLine is 0, it will count line 1 as longLine and add 1 to longLineCount, then 2nd line will be longer so it will make longLine length of line2 and add 1 to longLineCount, 3 is longer and so on and so forth.
The correct answer would be that there is 1 longLine with length of 20, but the longLineCount would say this appeared 4 times.

---

### Post by Garratt on 2009-03-24
Ahh silly me i wasn't reading your code properly, I thought it was incrementing the count by 1 each time the line was longer (+= 1), I only just realized it is resetting it to 1, each time...

Thank you again :D

I think that is it !, will use post-increment from now on so i don't make that mistake again.
cheers.

---

### Post by Garratt on 2009-03-24
Works beautifully, I had to change values of non-blank count total to 0 on files that contain only spaces as the values would fall into negatives, but that was an easy fix.
...
if (nonBlnkCntTotl < 0)
    {
        nonBlnkCntTotl =0;
    }
...

```
// A1.cpp assignment 1 semester 1 2009
// Author : "Garratt Campton"
// Date : Saturday, 21-03-09


#include <iostream>
using std::cout;
using std::cin;
using std::endl;

#include <string>
using std::string;


int main()

{
    // declare & initialize all variables to 0
    int lineCnt=0;
    int spaceCnt=0;
    int nonBlnkCnt=0;
    int nonBlnkCntTotl=0;
    int longLine=0;
    int longLineCnt=0;

    string line;
    string blank=" \t"; // search string for spaces or tabs

    size_t where;

    while (getline(cin, line))
    {
        // b) line counter
        ++lineCnt;

        // c) longest line &
        // d) # of longest lines
        if (line.length() > longLine)
        {
            longLine = line.length();
            longLineCnt = 1;
        }
        else if (line.length() == longLine)
        {
            ++longLineCnt;
        }

        // a) non-blank char counter
        // finding first space
        where = line.find_first_of(blank);

        // if first found is a space
        if (where != string::npos) 
        {       
            // adding first space to count
            ++spaceCnt;      
            
            // if length of string is longer
            // than the position of 'where'
            // search for more spaces
            while (where < line.length())
            {
                where = line.find_first_of(blank, where+1);
                ++spaceCnt;
            }

        // end if
        }

        nonBlnkCnt = line.length() - spaceCnt;
        nonBlnkCntTotl += nonBlnkCnt;
           
        // reinitialize variables back to 0
        spaceCnt =0;
        nonBlnkCnt =0;

            
    // end while
    }

    // added if statement for files containing
    // no characters but blanks
    if (nonBlnkCntTotl < 0)
    {
        nonBlnkCntTotl =0;
    }

    // print statements

    cout << " A) Number of non-blank characters: "
        << nonBlnkCntTotl << endl;
    cout << " B) Number of lines: " << lineCnt << endl;
    cout << " C) Length of longest line: "
        << longLine << endl;
    cout << " D) Number of longest lines: " 
        << longLineCnt << endl;

    return 0;

}
// end main

```

---

### Post by dwhitney67 on 2009-03-25
Great!  There's nothing like getting the first assignment out of the way.

---

