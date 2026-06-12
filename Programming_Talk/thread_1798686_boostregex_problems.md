---
title: "boost::regex problems"
date: 2011-07-06
forum: Programming Talk
---

### Post by evilgeniuz on 2011-07-06
Hello everyone!

I'm trying to know closer boost::regex library and i've got some problems with it. :confused:

I've found some example just to test works or not.

```
int find_data()
{
        std::string xStr("The boost library has a great opportunity for the regex!");
        boost::regex xRegEx("\\b(?:\\w+?)((\\w)\\2)(?:\\w+?)\\b");
        boost::smatch xResults;
        std::cout << "\n==========================Results==============================\n";
        std::string::const_iterator xItStart = xStr.begin();
        std::string::const_iterator xItEnd = xStr.end();
        while( boost::regex_search(xItStart, xItEnd, xResults, xRegEx) )
        {
            std::cout << "Word, we've searched, is \"" << xResults[0] << "\". It has two \"" << xResults[2] << "\" inside itself.\n";
            xItStart = xResults[1].second;
        }

        return 1;
}
```

it must result

```
==========================Results==============================
Word, we've searched, is «boost». It has two «o» inside itself.
Word, we've searched, is «opportunity». It has two «p» inside itself.
```

buuuuuuuuuuuuuut it reults....

```
==========================Results==============================
parser: /usr/local/inluce/boost/smart_ptr/shared_ptr.hpp:412 boost::shared_ptr<T>::reference boost::shared_ptr<T>::operator*() const [with T = boost::regex_traits_wrapper<boost::regex_traits<char> >, boost::shared_ptr<T>::reference = boost::regex_traits_wrapper<boost::regex_traits<char> >&>: Assertion `px !=0' failed.
Aborted
```

So, i'm using ubuntu 11.04, code::blocks and installed boost::regexp from repository. Help me please.

---

### Post by dwhitney67 on 2011-07-06
EDIT:  I read the final line of your post; it seems that you have installed Boost from the repos.
--------------------------------------------

I have no idea if you have installed Boost yourself, or are merely using the version available from the Ubuntu repositories.

The following program compiled and ran successfully for me (of course, I'm using Ubuntu 10.04 and Boost 1.40).
```

#include <boost/regex.hpp>

#include <string>
#include <iostream>

int main(int argc, const char** argv)
{
   std::string   str = "The boost library has a great opportunity for the regex";
   boost::regex  rex("\\b(?:\\w+?)((\\w)\\2)(?:\\w+?)\\b");
   boost::smatch res;

   std::string::const_iterator begin = str.begin();
   std::string::const_iterator end   = str.end();

   while (boost::regex_search(begin, end, res, rex))
   {
      std::cout << "Word, we've searched, is \"" << res[0] << "\".  It has two \""
                << res[2]
                << "\" inside itself."
                << std::endl;

      begin = res[1].second;
   }
}

```
To build the code:
```

g++ search.cpp -lboost_regex

```

Please try building the program above, as indicated, and report back your results.

---

