---
title: "C++ Regex -- what am I missing?"
date: 2009-04-02
forum: Programming Talk
---

### Post by Dr Small on 2009-04-02
I am trying to learn C++, and have a simple program here (from a tutorial, not mine) that I am trying to compile and run, but the compiler keeps complaining about
"regex.cpp:1:17: error: regex: No such file or directory"

Here is the program:
```
#include <regex>
#include <iostream>
#include <string>

bool is_email_valid(const std::string& email)
{
   // define a regular expression
   const std::tr1::regex pattern
      ("(\\w+)(\\.|_)?(\\w*)@(\\w+)(\\.(\\w+))+");

   // try to match the string with the regular expression
   return std::tr1::regex_match(email, pattern);
}

int main()
{
   std::string email1 = "marius.bancila@domain.com";
   std::string email2 = "mariusbancila@domain.com";
   std::string email3 = "marius_b@domain.co.uk";
   std::string email4 = "marius@domain";

   std::cout << email1 << " : " << (is_email_valid(email1) ?
      "valid" : "invalid") << std::endl;
   std::cout << email2 << " : " << (is_email_valid(email2) ?
      "valid" : "invalid") << std::endl;
   std::cout << email3 << " : " << (is_email_valid(email3) ?
     "valid" : "invalid") << std::endl;
   std::cout << email4 << " : " << (is_email_valid(email4) ?
     "valid" : "invalid") << std::endl;

   return 0;
}
```

Initially, it is the first line that is causing all the problems. The compiler can't find <regex>. I even reinstalled boost, but I'm not sure that mattered much.

Any ideas? (sorry, but I'm *extremely* new to this).

---

### Post by lloyd_b on 2009-04-02
The file in question ("/usr/include/c++/4.3/regex" on Intrepid) is part of the package "libstdc++6-4.3-dev".  Try installing that (though it *should* have been installed as part of "build-essential", I believe).

Also - could you post the compile command you're using? 

Lloyd B.

---

### Post by dwhitney67 on 2009-04-02
I believe the correct file to include is <tr1/regex>.

---

### Post by johnl on 2009-04-03
Including <regex> like you  have is fine.  You just need to pass "-std=c++0x" to g++ in order to enable the tr1 code.

> 
In file included from /usr/include/c++/4.3/regex:40,
                 from main.cc:10:
/usr/include/c++/4.3/c++0x_warning.h:36:2: error: #error This file requires compiler and library support for the upcoming ISO C++ standard, C++0x. This support is currently experimental, and must be enabled with the -std=c++0x or -std=gnu++0x compiler options.


---

