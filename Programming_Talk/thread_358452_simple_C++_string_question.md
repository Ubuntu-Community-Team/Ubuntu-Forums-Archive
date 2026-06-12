---
title: "simple C++ string question"
date: 2007-02-10
forum: Programming Talk
---

### Post by band-aid on 2007-02-10
I am trying to take user input as a string, then separate it into two parts at the first space for example


```
 Word1(break) word2 word3.....
```

I then want to take the first word as a command and store the rest of the words. The library I am trying to use is apstring.h

Thanks for the help

---

### Post by Choad on 2007-02-10
you talking about command line input?

surely you'd be using *argsv[]

im not familiar with apstring.h tho

---

### Post by thumper on 2007-02-10
You want to read in an entire string then break it up.

```
#include <iostream>
#include <string>

int main()
{
   std::string input;
   while (std::getline(std::cin, input)) {
      // do stuff
   }
}

```

---

### Post by Wybiral on 2007-02-10
Another route would be to use a string stream...

```

#include <iostream>
#include <sstream>
#include <string>

using namespace std;

int main()
{
   string temp;
   stringstream stream;
   string test = "This is my string";
   stream << test;
   while(stream>>temp)
   {
      cout << temp << endl;
   }
}

```

---

### Post by band-aid on 2007-02-11
I think I understand thumper's method the best but how would I go about locating the first space and breaking it there?

---

### Post by lnostdal on 2007-02-11
Wybirals example does what you ask for. It reads one word at a time in sequence into temp, while at each step printing temp. Instead of printing temp you could store temp at each step into a std::vector for instance.

edit: oh, didn't notice the part about the non-standard header/library .. i do not have that header/library available so can't help you with that part

---

### Post by LordHunter317 on 2007-02-11
You'll need to post the apstring headers since it's been years sine I've used them, but they used to have no STL compatiblitiy whatseover, meaning none of these methods will work.

This is unfortunate, but reality.

---

### Post by Wybiral on 2007-02-11
I don't see how a string format isn't compatible with either a "string" or the string representation of "c_str" as in "(string)object.c_str()" unless it's compressed...

I mean... After all, isn't a string just an array of characters? (unless of course it's compressed)

---

### Post by LordHunter317 on 2007-02-11
> **Wybiral said:**
> I don't see how a string format isn't compatible with either a "string"Because it's not a std::string.  It's an apstring, which is a custom string class written by the college board for AP courses and examinations.

Any compatibility with std::string has to be taken up by the class writer, if they choose to create none then you have none.

>  or the string representation of "c_str" as in "(string)object.c_str()" unless it's compressed...Possibly, but even still, he should use as much apstring functionality as he can.   The OP will lose points on the exam if he does not, nevermind what the teacher may or may not do.

> I mean... After all, isn't a string just an array of characters?No.  This isn't C.

---

### Post by Wybiral on 2007-02-11
> **LordHunter317 said:**
> ... No.  This isn't C.

Duh, captain condescending... It may not be an _ARRAY_ of characters... But unless it's compressed that's still how it's represented in machine code... A string/sequence/"array" of byte values representing the ASCII character codes... In other words... An "array" of characters. And if that's the case it takes maybe 3 lines of code to convert a C/C++ string into a sequence of byte values.

It may not be a valid example in an exam (which the OP didn't mention anything about) where that isn't the kind of solution they are looking for... But it's still a valid solution.

---

### Post by LordHunter317 on 2007-02-11
> **Wybiral said:**
> Duh, captain condescending... It may not be an _ARRAY_ of characters... But unless it's compressed that's still how it's represented in machine code...So?  Machine code representation is irrelevant (I don't even know what that means, as machine code on most architectures is typeless).  And no, that may not be the machine representation.

> And if that's the case it takes maybe 3 lines of code to convert a C/C++ string into a sequence of byte values.No, that's not necessarily true.  If you don't expose access to the raw storage, or an iterator-esque interface, or the [] operator (or equivalent method call) then you may not be able to do it or it will be more complicated.

> But it's still a valid solution.Not using apstring, which was one of the requirements mentioned in the OP.

---

### Post by LordHunter317 on 2007-02-11
To be fair, the odds of any string class not accepting const char* as an input are slim, sine string literals are of that form and it would be pretty useless not to accept those.  So a slight modification and things may work.  Your code is of course fairly idomatic C++, but the issue is the AP classes do not teach that, and he really will need an AP-specific solution.

---

### Post by Choad on 2007-02-11
> **Wybiral said:**
> Duh, **captain condescending**... It may not be an _ARRAY_ of characters... But unless it's compressed that's still how it's represented in machine code... A string/sequence/"array" of byte values representing the ASCII character codes... In other words... An "array" of characters. And if that's the case it takes maybe 3 lines of code to convert a C/C++ string into a sequence of byte values.

It may not be a valid example in an exam (which the OP didn't mention anything about) where that isn't the kind of solution they are looking for... But it's still a valid solution.
lol i can actually imagine that superhero

---

### Post by band-aid on 2007-02-11
Here is apstring

```

#ifndef _APSTRING_H
#define _APSTRING_H

#include <iostream.h>
// uncomment line below if bool not built-in type
// #include "bool.h"

// *******************************************************************
//  Last Revised: 11/24/98 - corrected specification comments, dhj
//
//  8/14/98 corrected comments, dhj
//  6/29/98 - commented out the #include "bool.h", dhj
//
//  APCS string class
//
//  string class consistent with a subset of the standard C++ string class
//  as defined in the draft ANSI standard
// *******************************************************************

extern const int npos;  // used to indicate not a position in the string

class apstring
{
  public:

  // constructors/destructor

    apstring( );                         // construct empty string ""
    apstring( const char * s );          // construct from string literal
    apstring( const apstring & str );    // copy constructor
    ~apstring( );                        // destructor

  // assignment

    const apstring & operator = ( const apstring & str ); // assign str
    const apstring & operator = ( const char * s );       // assign s
    const apstring & operator = ( char ch );              // assign ch

  // accessors

    int    length( )                  const;    // number of chars
    int    find( const apstring & str ) const;  // index of first occurrence of str
    int    find( char ch )            const;    // index of first occurrence of ch
    apstring substr( int pos, int len ) const;    // substring of len chars
                                                // starting at pos
    const char * c_str( )             const;    // explicit conversion to char *

  // indexing

    char   operator[ ]( int k )       const;    // range-checked indexing
    char & operator[ ]( int k );                // range-checked indexing

  // modifiers

    const apstring & operator += ( const apstring & str );// append str
    const apstring & operator += ( char ch );            // append char


  private:
      int myLength;                     // length of string (# of characters)
      int myCapacity;                   // capacity of string
      char * myCstring;                 // storage for characters
};

// The following free (non-member) functions operate on strings
//
// I/O functions

ostream & operator << ( ostream & os, const apstring & str );
istream & operator >> ( istream & is, apstring & str );
istream & getline( istream & is, apstring & str );

// comparison operators:

bool operator == ( const apstring & lhs, const apstring & rhs );
bool operator != ( const apstring & lhs, const apstring & rhs );
bool operator <  ( const apstring & lhs, const apstring & rhs );
bool operator <= ( const apstring & lhs, const apstring & rhs );
bool operator >  ( const apstring & lhs, const apstring & rhs );
bool operator >= ( const apstring & lhs, const apstring & rhs );

// concatenation operator +

apstring operator + ( const apstring & lhs, const apstring & rhs );
apstring operator + ( char ch, const apstring & str );
apstring operator + ( const apstring & str, char ch );

// *******************************************************************
// Specifications for string functions
//
// Any violation of a function's precondition will result in an error
// message followed by a call to exit.
//
// The apstring class assumes that '\0' is not a valid
// character in an apstring. Any attempts to place '\0'
// in an apstring will result in undefined behavior. Generally
// this means that characters that follow the '\0' will not
// be considered part of the apstring for purposes of
// comparison, output, and subsequent copying.
//
// constructors / destructor
//
// string( )
//    postcondition: string is empty
//
// string( const char * s )
//    description:   constructs a string object from a literal string
//                   such as "abcd"
//    precondition:  s is '\0'-terminated string as used in C
//    postcondition: copy of s has been constructed
//
// string( const string & str )
//    description:   copy constructor
//    postcondition: copy of str has been constructed
//
// ~string( );
//    description:   destructor
//    postcondition: string is destroyed
//
// assignment
//
// string & operator = ( const string & rhs )
//    postcondition: normal assignment via copying has been performed
//
// string & operator = ( const char * s )
//    description:   assignment from literal string such as "abcd"
//    precondition:  s is '\0'-terminated string as used in C
//    postcondition: assignment via copying of s has been performed
//
// string & operator = ( char ch )
//    description:   assignment from character as though single char string
//    postcondition: assignment of one-character string has been performed
//
// accessors
//
// int length( ) const;
//    postcondition: returns # of chars in string
//
// int find( const string & str)  const;
//    description:   find the first occurrence of the string str within this
//                   string and return the index of the first character.  If
//                   str does not occur in this string, then return npos.
//    precondition:  this string represents c0, c1, ..., c(n-1)
//                   str represents s0, s1, ...,s(m-1)
//    postcondition: if s0 == ck0, s1 == ck1, ..., s(m-1) == ck(m-1) and
//                   there is no j < k0 such that s0 = cj, ...., sm == c(j+m-1),
//                   then returns k0;
//                   otherwise returns npos
//
// int find( char ch ) const;
//    description:   finds the first occurrence of the character ch within this
//                   string and returns the index.  If ch does not occur in this
//                   string, then returns npos.
//    precondition:  this string represents c0, c1, ..., c(n-1)
//    postcondition: if ch == ck, and there is no j < k such that ch == cj
//                   then returns k;
//                   otherwise returns npos
//
// string substr( int pos, int len ) const;
//    description:   extract and return the substring of length len starting
//                   at index pos
//    precondition:  this string represents c0, c1, ..., c(n-1)
//                         0 <= pos <= pos + len - 1 < n.
//    postcondition: returns the string that represents
//                   c(pos), c(pos+1), ..., c(pos+len-1)
//
// const char * c_str( ) const;
//    description:   convert string into a '\0'-terminated string as
//                   used in C for use with functions
//                   that have '\0'-terminated string parameters.
//    postcondition: returns the equivalent '\0'-terminated string
//
// indexing
//
// char operator [ ]( int k ) const;
//    precondition:  0 <= k < length()
//    postcondition: returns copy of the kth character
//
// char & operator [ ]( int k )
//    precondition:  0 <= k < length()
//    postcondition: returns reference to the kth character
//    note:          if this reference is used to write a '\0'
//                   subsequent results are undefined
//
// modifiers
//
// const string & operator += ( const string & str )
//    postcondition: concatenates a copy of str onto this string
//
// const string & operator += ( char ch )
//    postcondition: concatenates a copy of ch onto this string
//
//
// non-member functions
//
// ostream & operator << ( ostream & os, const string & str)
//    postcondition: str is written to output stream os
//
// istream & operator >> ( istream & is, string & str )
//    precondition:  input stream is open for reading
//    postcondition: the next string from input stream is has been read
//                   and stored in str
//
// istream & getline( istream & is, string & str )
//    description:   reads a line from input stream is into the string str
//    precondition:  input stream is open for reading
//    postcondition: chars from input stream is up to '\n' have been read
//                   and stored in str; the '\n' has been read but not stored
//
// string operator + ( const string & lhs, const string & rhs )
//    postcondition: returns concatenation of lhs with rhs
//
// string operator + ( char ch, const string & str )
//    postcondition: returns concatenation of ch with str
//
// string operator + ( const string & str, char ch )
//    postcondition: returns concatenation of str with ch
//
//***************************************************************
#endif

```

---

### Post by LordHunter317 on 2007-02-11
Elaborating on thunmper's method, apstring provdies a find operator you can use to find the first occurance of a character in a string.  You can also use getline(), but with type 'apstring' instead of std::string.  

Hopefully that's enough to get you started.  Post some code if you get stuck.

---

### Post by band-aid on 2007-02-11
Ok, I'm posting some code because I am stuck lol. What this function needs to do is split the string into two pieces and store them in separate local variables "command" and "tobestored". Then I have a horribly inefficient and possibly completely wrong method of looking at command and determining storing tobestored in the correct global variable depending on what command is equal to. Here goes, try not to laugh too much.

```

void separate(apstring total){
       breakpoint = find(total, " ");
       apstring command = substr(0, breakpoint);
       apstring tobestored = substr(breakpoint, (length(total)-breakpoint));
       if(command == up){
                  tobestored = up;
                  }
                  if(command == down){
                             tobestored = down;
                             }
                             if(command == left){
                                        tobestored = left;
                                        {
                                                   if(command == right){
                                                              tobestored = right;
                                                              }
                                                              if(command == both){
                                                                         tobestored = both;
                                                                         }
                                                                         }

```

thanks for the help

---

### Post by band-aid on 2007-02-11
First off, sorry for the double post but I felt it was necessary to give an update on my progress. I have adjusted my function and removed two of the things I needed it to do because they would not work even though they looked fine to me my code now looks like this.

```

void separate(apstring total){
       int breakpoint = total.find(" ");
       apstring command = command.substr(0, breakpoint);
       int len = total.length();
       apstring tobestored = tobestored.substr(breakpoint, (len-breakpoint));
       if(command == above){
                  above = tobestored;
                  }
                  if(command == below){
                             below = tobestored;
                             }
                          
                                                  
                                                              if(command == sandwich){
                                                                         sandwich = tobestored;
                                                                         }
                                                                      
}

```

The two things I removed were my 

```

if(command == left){
left = tobestored;
}

```

and

```

if(command == right){
right = tobestored;
}

```

They look fine to me and similar statements worked just fine.

So now my program compiles but has major linking errors which I am working to correct. It apparently isn't seeing the apstring header file correctly. Any help is greatly appriciated.

---

