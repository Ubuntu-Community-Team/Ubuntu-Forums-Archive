---
title: "[SOLVED] split string on multiple values c++"
date: 2008-09-19
forum: Programming Talk
---

### Post by monkeyking on 2008-09-19
Hi, I need to tokenize a string, but I have multiple delims.
It seems a program that in perl would be a very short oneliner,
is quite non-trivial in c++.

I very quickly made tokenizer that splits on a specific string.

But my code has exploded, there must be an easier way.
Can someone point me in the right direction.

I want to split a string that looks like
```
"23:35, 345 \t 35"
```
into the numerals.

thanks

---

### Post by dwhitney67 on 2008-09-19
There is probably a Boost library solution, but for the life of it, I do not know it.  Thus I will present a C/C++ solution and a "pure" (albeit lame) C++ solution.

C/C++ solution:
[PHP]#include <cstring>
#include <vector>
#include <iostream>

int main()
{
  std::string str( "23:45, 123 \t 35" );

  // begin tokenizing the string
  //
  char *token = strtok( const_cast<char*>( str.c_str() ), ":, \t" );

  std::vector<int> values;

  while ( token != NULL )
  {
    // save the numeral
    values.push_back( atoi(token) );

    // get next token (if any)
    token = strtok( NULL, ":, \t" );
  }

  // output results
  //
  std::cout << "original str = " << str << std::endl;
  for ( size_t i = 0; i < values.size(); ++i )
  {
    std::cout << values[i] << std::endl;
  }

  return 0;
}[/PHP]


C++ example:
[PHP]#include <string>
#include <sstream>
#include <iostream>

int main()
{
  std::string str( "23:45, 345 \t 223" );

  std::istringstream istr( str );

  int value[4];
  char dontcare;

  istr >> value[0] >> dontcare >> value[1] >> dontcare >> value[2] >> value[3];

  std::cout << "original str = " << str << std::endl;

  for (size_t i = 0; i < 4; ++i )
  {
    std::cout << value[i] << std::endl;
  }
  return 0;
}[/PHP]
Both of my examples are simple, yet functional.  Anyhow, I'm off to get another beer.

---

### Post by joe_bruin on 2008-09-19
There are many ways to do this depending on what you care about.

Here's a simple one: Allocate a buffer and copy the string to it.  Then, iterate through the string.  When you find the start of a numeral, save a pointer to it in an array.  When you find a non-numeric character, replace it with '\0'.  Now you have a bunch of pointers to null terminated strings of numerals.  Tada!

Implementation is left as an exercise to the reader.

---

### Post by monkeyking on 2008-09-19
:confused:
omg can it be this simple.
I was using 4 different vectors some iterators, some find_first_not_of, find_last_of.

I'm of to bed, after having wasted half the night.
your solution dwhitney looks beautifull.
Thanks alot for your help.

---

### Post by dribeas on 2008-09-19
> **dwhitney67 said:**
> There is probably a Boost library solution, but for the life of it, I do not know it.  Thus I will present a C/C++ solution and a "pure" (albeit lame) C++ solution.

[Boost::Tokenizer]("http://www.boost.org/doc/libs/1_36_0/libs/tokenizer/index.html")

---

### Post by dwhitney67 on 2008-09-19
> **dribeas said:**
> [Boost::Tokenizer]("http://www.boost.org/doc/libs/1_36_0/libs/tokenizer/index.html")
I figured there would be one!

[PHP]#include <boost/tokenizer.hpp>
#include <iostream>
#include <string>


int main()
{
  std::string str( "11:44, 233 \t 32" );

  boost::tokenizer<> tok( str );

  std::cout << "original str = " << str << std::endl;

  for ( boost::tokenizer<>::iterator it = tok.begin(); it != tok.end(); ++it )
  {
    std::cout << *it << std::endl;
  }

  return 0;
}[/PHP]

---

### Post by StOoZ on 2008-09-19
just wondering , what is the difference between using a tokenizer to a regex?

---

