---
title: "C++ Extract int from string"
date: 2010-07-14
forum: Programming Talk
---

### Post by tdheff on 2010-07-14
How would one extract an integer from a string that contains characters and a number?

The strings could be in the form of "abc123", "abc123def" or "123def". In other words, they contain a string with one integer in it somewhere. Any help is much appreciated. Thanks.

---

### Post by trent.josephsen on 2010-07-14
I can think of at least two ways:
1) use regular expressions
2) use an iterator to step through the string, and copy each consecutive digit to a temporary buffer.  Break when it reaches an unreasonable length or on the first non-digit after a string of consecutive digits.  Then you have a string of digits that you can easily convert.

Another way is to complain violently when the input isn't a valid number.

---

### Post by stair314 on 2010-07-14
Rather than using an iterator to step through the whole string, you can use the string's find_first_of / find_last_of methods.

---

### Post by tdheff on 2010-07-14
I'm going to give the iterator thing a go since I am clueless about regex.

Thanks for the help.

---

### Post by nvteighen on 2010-07-14
> **tdheff said:**
> I'm going to give the iterator thing a go since I am clueless about regex.

Thanks for the help.

Are you required to use C++? If not, trying Perl would make this much easier with its native regexps.

---

### Post by SledgeHammer_999 on 2010-07-14
Don't forget that an std:string is a container. And you can use some C++ features(like streams). Some example code:

[php]
#include <string>
#include <sstream>
#include <iostream>
#include <cctype>

int main(int argc, char *argv[])
{
    std::string str("abc123def");
    std::string temp;
    int number=0;
    
    for (unsigned int i=0; i < str.size(); i++)
    {
        //iterate the string to find the first "number" character
        //if found create another loop to extract it
        //and then break the current one
        //thus extracting the FIRST encountered numeric block
        if (isdigit(str[i]))
        {
            for (unsigned int a=i; a<str.size(); a++)
            {
                temp += str[a];               
            }
          //the first numeric block is extracted
          break;
        }    
    }
    
    std::istringstream stream(temp);
    stream >> number;
    
    std::cout << number << std::endl;    
}
[/php]

Some doc links: [cctype](http://www.cplusplus.com/reference/clibrary/cctype/), [stringstreams](http://www.cplusplus.com/reference/iostream/stringstream/)

Also note that you can change the type of the 'number' variable to any other numeric type without any additional code modification.(eg from "int number=0;" to "float number=0;")

---

### Post by Yarui on 2010-07-14
> **tdheff said:**
> I'm going to give the iterator thing a go since I am clueless about regex.

Thanks for the help.
I would definitely recommend learning how to use regular expressions eventually.  They are extremely useful and not as difficult as they may seem at first.

---

### Post by dwhitney67 on 2010-07-14
Boost supports regular expression parsing; unfortunately I have yet to learn how to define 'efficient' expressions.  Nevertheless, I conjured up the following to meet the OP's requirement:
```

#include <boost/regex.hpp>
#include <string>
#include <sstream>
#include <iostream>

int main(int argc, char** argv)
{
   if (argc != 2)
   {
      std::cout << "Usage: " << argv[0] << " <data>" << std::endl;
      return -1;
   }

   boost::regex re("[*0-9*]");   // the regular expression
   std::string  data = argv[1];

   // Find the desired expression
   boost::sregex_iterator m1(data.begin(), data.end(), re);
   boost::sregex_iterator m2;
   std::stringstream      ss;

   // Save the result(s)
   while (m1 != m2)
   {
      ss << *m1++;
   }

   int num = -1;
   ss >> num;

   std::cout << "num = " << num << std::endl;
}

```
To build:
```

g++ regex.cpp -lboost_regex-mt

```

---

### Post by trent.josephsen on 2010-07-14
@Yarui:  Yes, but for a simple project (as this one appears to be) they are probably way overkill.  For C++ at any rate; you wouldn't try the character-by-character approach in a language like Perl that supports native regexes.

---

### Post by Sockerdrickan on 2010-07-14
Note that C++0x has support for this [http://en.wikipedia.org/wiki/C%2B%2B0x#Regular_expressions](http://en.wikipedia.org/wiki/C%2B%2B0x#Regular_expressions)

---

