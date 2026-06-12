---
title: "[SOLVED] anyone familiar with boost regex?"
date: 2008-09-24
forum: Programming Talk
---

### Post by StOoZ on 2008-09-24
im trying to learn it , now I have a string , which has a LOT of jpg's mentioned in it...
I wonder why this code , returns only one , it should match all of them (isnt it?):
[http://rafb.net/p/IOGJO849.html]("http://rafb.net/p/IOGJO849.html")

---

### Post by dwhitney67 on 2008-09-24
> **StOoZ said:**
> im trying to learn it , now I have a string , which has a LOT of jpg's mentioned in it...
I wonder why this code , returns only one , it should match all of them (isnt it?):
[http://rafb.net/p/IOGJO849.html]("http://rafb.net/p/IOGJO849.html")

There are many utilities in Boost that look wonderful on paper, but when you actually try to implement them, you realize that you could have solved the problem much easier if you implemented (and documented) your code appropriately.

Now... what is it that you are trying to do?  What does you data file contain?  Just strings with the .jpg extension?

If you are bent on using Boost, will this example not help you?
[http://www.boost.org/doc/libs/1_35_0/libs/regex/example/snippets/regex_iterator_example.cpp](http://www.boost.org/doc/libs/1_35_0/libs/regex/example/snippets/regex_iterator_example.cpp)

P.S.  I would prefer if you post your code directly onto the Ubuntu Forums, without referring to another site.

---

### Post by StOoZ on 2008-09-26
mmm ok , what im trying to do , to be more precise , is , I have something like this , a file with many links , could be https , http , etc , all of them are jpg links only , now I would like to keep all these links in a vector or set , the file looks something like this (i manually wrote that one , the other can have anything in it , but it also has links , like this one has) :
> hhh....fdsfds jpj<>http://www.gg.com/h.jpg<<>fdsfs
hhh....fdsfds jpj<>http://www.gg.com/h.jpg<<>fdsfs
sdfsfsdsd
hhhsd....fdsfds jpj<>http://www.gg.com/h.jpg<<>fdsfs
sf...sdfsfsdfdsfds jpj<>http://www.gg.com/h.jpg<<>fdsfs
sdfsdfsdfsdf
sfsf
hhh.f
hhhsf.fsd...fdsfdsfds jpj<>http://www.gg.com/h.jpg<<>fdsfs


hhh....fdsfds jfdfdsfdspj<>http://www.ggdsssssss.com/h.jpg<<>fdsfs
hhh....fdsfds jpj<>http://www.gg.com/h.jpg<<>fdsfs
hhfsdfsdh....fdsfds jpj<>http://www.fsfsdfsfsdgg.com/fffh.jpg<<>fdsfs
hhh....fdsfds jpj<>http://www.gg.com/h.jpg<<>fdsfs
sdfsdfdshfh.sdf...fdsfds jpj<>http://www.gddsdsdsdsg.com/h.jpg<<>fdsfs
hhhds....fdsfds jpj<>http://www.gdfgfddg.com/h.jpg<<>fdsfs
hhhdf....fdsfds jpj<>http://www.gg.com/h.jpg<<>fdsfs
hhhf....fdsfds jpj<>http://www.gg.com/h.jpg<<>fdsfs
hhhsd....fdsfds jpj<>http://www.ggfff.com/h.jpg<<>fdsfs
hhsdfh....fdsfds jpj<>http://www.gg.com/h.jpg<<>fdsfs
hfhh....fdsfds jpj<>http://www.gg.com/h.jpg<<>fdsfs
hhh...sdf.fdsfds jpj<>http://www.gg.com/h.jpg<<>fdsfs
hhh...sd.fdsfds jpj<>http://www.gg.com/uuuuh.jpg<<>fdsfs
hhhfds...sfsddfdsfds jpj<>http://www.gAAAAAAADDDg.com/h.jpg<<>fdsfs
hhh..fsd..fdfsdsfds jpj<>http://www.gg.com/iuiuh.jpg<<>fdsfs
vv hhh....fdsfds jpj<>http://www.gg.com/hiuiu.jpg<<>fdsfs
hhh....fdsfds jpj<>http://www.gg.com/iuh.jpg<<>fdsfs



so basically I want to grab all of these links...

---

### Post by Zugzwang on 2008-09-26
RegExes seem to be overkill here. Just split your input strings on the characters '>' and '<' and apply a check for each of the strings you get. See [here, section 7.3]("http://www.oopweb.com/CPP/Documents/CPPHOWTO/Volume/C++Programming-HOWTO-7.html") for such a tokenizing example.

---

### Post by dwhitney67 on 2008-09-26
> **Zugzwang said:**
> RegExes seem to be overkill here. Just split your input strings on the characters '>' and '<' and apply a check for each of the strings you get. See [here, section 7.3]("http://www.oopweb.com/CPP/Documents/CPPHOWTO/Volume/C++Programming-HOWTO-7.html") for such a tokenizing example.
+1

Now that the data file has been presented, I agree that it would be rather easy to yank a sub-string from each line within the file.

If the OP is still interested in a RegEx solution using Boost, here's something I threw together this morning:


[PHP]
#include <boost/regex.hpp>

#include <string>
#include <vector>
#include <fstream>
#include <iostream>


class HttpRegex
{
  public:
    typedef std::vector< std::string > Results;

    HttpRegex( const char *regExpression )
      : m_re(regExpression)
    {
    }

    Results findResults( std::ifstream& ifs )
    {
      Results results;

      if ( !ifs.bad() )
      {
        // Setup regular expression
        boost::regex expression( m_re );

        std::string line;

        // Read each line of text from the file
        while ( getline( ifs, line ) )
        {
          // Find the desired expression
          boost::sregex_iterator m1( line.begin(), line.end(), expression );
          boost::sregex_iterator m2;

          // Save the result
          while ( m1 != m2 )
          {
            // thru trial/error I determined where the URL is at.
            results.push_back( (*m1)[2] );
            ++m1;
          }
        }
      }

      return results;
    }

  private:
    const char * m_re;
};


int main( int argc, const char** argv )
{
  if ( argc != 2 )
  {
    std::cout << "Usage: " << argv[0] << " <file>" << std::endl;
    return 1;
  }

  // Open the file
  std::ifstream ifs( argv[1] );

  // Get HTTP results
  HttpRegex          regex( "(.*)<>(.*)<<>" );
  HttpRegex::Results results = regex.findResults( ifs );

  // Close the file (if that was not already obvious)
  ifs.close();

  // Display results
  std::cout << results.size() << " matches found." << std::endl;

  for ( HttpRegex::Results::const_iterator it = results.begin(); it != results.end(); ++it )
  {
    std::cout << *it << std::endl;
  }

  return 0;
}
[/PHP]


P.S.  To compile:
```
g++ regex.cpp -lboost_regex -o regex
```

---

