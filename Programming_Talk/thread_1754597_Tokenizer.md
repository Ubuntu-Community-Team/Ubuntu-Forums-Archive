---
title: "Tokenizer"
date: 2011-05-10
forum: Programming Talk
---

### Post by gregarion on 2011-05-10
Hey guys, i been trying to tokenize a string using the boost library.
```

int main(){    
using namespace std;    
using namespace boost;
 string s = "This is,  a test";
 tokenizer<> tok(s);    
for(tokenizer<>::iterator beg=tok.begin(); beg!=tok.end();++beg){
  cout << *beg << "\n";    }
```

The problem i am facing currently is that i am unable to tokenize a  string, yet allow it to leave the whitespaces as token also. I tried  replacing the whitespaces with a character , but how am i able to  tokenize the string.

 For example , i subtituted all the white spaces  with "|" , thus the string above will be "This|is,||a test".

From here , how can i go about making sure that the string will continue  being tokenized only leaving the words , but "|" will not be considered  as a char to be removed. Hope for some help here.

---

### Post by dwhitney67 on 2011-05-10
When one tokenizes a string using one or more field delimiters, the delimiters are generally not returned in the results.  That's because they are not of interest; only the tokens are.

If you want to know where your delimiters are at, then I would suggest that you develop your own tokenizer.  The Boost tokenizer is very general, similar as if one were to use strtok().


P.S.  Perhaps I misunderstood what you wanted; here's a simple example that tokenizes a string using the delimiter "|":
```

#include <boost/tokenizer.hpp>
#include <string>
#include <iostream>
#include <cstdlib>

int main()
{
  typedef boost::tokenizer< boost::char_separator<char> > Tokenizer;
  boost::char_separator<char> sep("|");

  std::string str = "|COMPUTERS|LINUX|UBUNTU|100|50|";

  Tokenizer info(str, sep);

  for (Tokenizer::iterator it = info.begin(); it != info.end(); ++it)
  {
    std::cout << "*it =\t" << *it << std::endl;
  }
}

```

---

