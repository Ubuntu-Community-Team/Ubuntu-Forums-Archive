---
title: "Efficient way to tokenize string?"
date: 2009-02-24
forum: Programming Talk
---

### Post by gvanto on 2009-02-24
Perhaps this is a little simple, but I was wondering what the most efficient way of tokenizing and organizing by <value: pair> would be?  I'm thinking perhaps a function returning a <map> / similar type stl object would be best to store the different types of objects for the values? (key is always string, S is always a string, P a double and the rest int's). I'm a bit of a stl newbie, but would love to use it more.

|S=FGL,P=687.00,Q=387,T=114442,N=66224|

Ideas would be warmly receieved :-)

gvanto
stl noob!

---

### Post by cabalas on 2009-02-24
What language do you want to do this in?  This problem is more difficult in some langauges (say c or c++) than others (any language with a split string function)

---

### Post by mriedel on 2009-02-24
I'm not quite sure what you're trying to accomplish. What does tokenizing a string have to do with doubles, integers and maps? Tokenization means splitting a string (or any other tokenizable entity) up into smaller substrings by a certain pattern. One way to store the result would be an array of strings or a list of strings.

> **cabalas said:**
> What language do you want to do this in?  This problem is more difficult in some langauges (say c or c++) than others (any language with a split string function)

As he mentions the STL (C++ "Standard Template Library"), I suppose he's talking about C++.

---

### Post by dwhitney67 on 2009-02-24
This is probably not the most efficient... using Boost would probably be better.

But since I do not have boost installed on the system (currently) at my fingertips, consider the following solution:
```

#include <algorithm>
#include <map>
#include <iostream>
#include <string>
#include <cstring>
#include <cstdlib>


typedef std::map<std::string, std::string>  Tokens;
typedef std::pair<std::string, std::string> Token;



void tokenize(const std::string& data, const std::string& delims, Tokens& tokens)
{
  char* tmp  = strdup(data.c_str());
  char* seed = tmp;
  char* key  = 0;
  char* val  = 0;

  do
  {
    key  = strtok(seed, delims.c_str());
    seed = 0;
    val  = strtok(seed, delims.c_str());

    if (key && val)
    {
      tokens.insert(Token(key, val));
    }
  } while (key && val);

  free(tmp);
}

void displayToken(const Token& token)
{
  std::cout << "key = " << token.first << ", val = " << token.second << std::endl;
}

int main()
{
  std::string data("|S=FGL,P=687.00,Q=387,T=114442,N=66224|");
  std::string delims("|=,");
  Tokens      tokens;

  tokenize(data, delims, tokens);
  std::for_each(tokens.begin(), tokens.end(), displayToken);
}

```

---

### Post by dwhitney67 on 2009-02-25
And an example using the Boost Tokenizer:
```

#include <boost/tokenizer.hpp>
#include <string>
#include <map>
#include <algorithm>
#include <iostream>

typedef std::map<std::string, std::string>  Tokens;
typedef std::pair<std::string, std::string> Token;

void tokenize(const std::string& data, const std::string& delims, Tokens& tokens)
{
  typedef boost::tokenizer< boost::char_separator<char> > Tokenizer;
  boost::char_separator<char> sep(delims.c_str());

  Tokenizer info(data, sep);

  for (Tokenizer::iterator it = info.begin(); it != info.end(); ++it)
  {
    tokens.insert(Token(*it++, *it));
  }
}

void displayToken(const Token& token)
{
  std::cout << "key = " << token.first << ", val = " << token.second << std::endl;
}

int main()
{
  const std::string data("|S=FGL,P=687.00,Q=387,T=114442,N=66224|");
  const std::string delims("|=,");
  Tokens            tokens;

  tokenize(data, delims, tokens);
  std::for_each(tokens.begin(), tokens.end(), displayToken);
}

```

---

### Post by Krupski on 2009-02-25
> **gvanto said:**
> Perhaps this is a little simple, but I was wondering what the most efficient way of tokenizing and organizing by <value: pair> would be?  I'm thinking perhaps a function returning a <map> / similar type stl object would be best to store the different types of objects for the values? (key is always string, S is always a string, P a double and the rest int's). I'm a bit of a stl newbie, but would love to use it more.

|S=FGL,P=687.00,Q=387,T=114442,N=66224|

Ideas would be warmly receieved :-)

gvanto
stl noob!

Not quite sure what you're looking for, but maybe the following code will be of some help to you:

```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(void)
{
    struct {
        char s[BUFSIZ];
        double p;
        int q;
        int t;
        int n;
    } key;

    int n;
    char tmp[BUFSIZ];

    // original input string
    strcpy(tmp, "S=FGL,P=687.00,Q=387,T=114442,N=66224");

    // advance to first delimiter
    strcpy(tmp, strtok(tmp, "="));

    // copy first item (a string)
    strcpy(key.s, strtok(NULL, "="));

    // get next value (a double)
    key.p = atof(strtok(NULL, "="));

    // get the rest (ints)
    key.q = atoi(strtok(NULL, "="));

    key.t = atoi(strtok(NULL, "="));

    key.n = atoi(strtok(NULL, "="));

    // debug: show the results
    fprintf(stdout, "key.s=%s, key.p=%f, key.q=%d, key.t=%d, key.n=%d\n", key.s, key.p, key.q, key.t, key.n);
    return 0;
}

```

Note that there is a bug in the code... the string part is returned as "FGL,P" which is everything up to the next delimiter.

Hopefully, the example of using a "struct" to hold different data types and using "strtok" to find pieces within a string will lead you in the right direction.

Good luck!

-- Roger

---

### Post by gvanto on 2009-02-27
this looks like a great solutiobn Dwhitney. Weird, I get this error:
i only have ONE implementation of this method anywhere ... renaming it causes the same error to occur again, but for teh new method ... which seems to suggest that perhaps the header is included twice somewhere (though I didn't think this causes a problem?)

Description	Resource	Path	Location	Type
multiple definition of `tokenize(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::map<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::less<std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::allocator<std::pair<std::basic_string<char, std::char_traits<char>, std::allocator<char> > const, std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > >&)'	Utils.h	WLClient/src	38	C/C++ Problem
./src/ClientSocket.o:/home/pacific/workspace/WLClient/Debug/../src/Utils.h first defined here	WLClient		38	C/C++ Problem
make: *** [WLClient] Error 1	WLClient		0	C/C++ Problem



> **dwhitney67 said:**
> And an example using the Boost Tokenizer:
```

#include <boost/tokenizer.hpp>
#include <string>
#include <map>
#include <algorithm>
#include <iostream>

typedef std::map<std::string, std::string>  Tokens;
typedef std::pair<std::string, std::string> Token;

void tokenize(const std::string& data, const std::string& delims, Tokens& tokens)
{
  typedef boost::tokenizer< boost::char_separator<char> > Tokenizer;
  boost::char_separator<char> sep(delims.c_str());

  Tokenizer info(data, sep);

  for (Tokenizer::iterator it = info.begin(); it != info.end(); ++it)
  {
    tokens.insert(Token(*it++, *it));
  }
}

void displayToken(const Token& token)
{
  std::cout << "key = " << token.first << ", val = " << token.second << std::endl;
}

int main()
{
  const std::string data("|S=FGL,P=687.00,Q=387,T=114442,N=66224|");
  const std::string delims("|=,");
  Tokens            tokens;

  tokenize(data, delims, tokens);
  std::for_each(tokens.begin(), tokens.end(), displayToken);
}

```

---

### Post by dwhitney67 on 2009-02-27
> **gvanto said:**
> this looks like a great solutiobn Dwhitney. Weird, I get this error:
i only have ONE implementation of this method anywhere ... renaming it causes the same error to occur again, but for teh new method ... which seems to suggest that perhaps the header is included twice somewhere (though I didn't think this causes a problem?)

Description	Resource	Path	Location	Type
multiple definition of `tokenize(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::map<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::less<std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::allocator<std::pair<std::basic_string<char, std::char_traits<char>, std::allocator<char> > const, std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > >&)'	Utils.h	WLClient/src	38	C/C++ Problem
./src/ClientSocket.o:/home/pacific/workspace/WLClient/Debug/../src/Utils.h first defined here	WLClient		38	C/C++ Problem
make: *** [WLClient] Error 1	WLClient		0	C/C++ Problem
I have no idea.

Maybe you should consider placing the tokenize() function in its own namespace, or perhaps avoid the "using namespace" directive in your code.  The code I provided works in a standalone program, but if you take it piece by piece to integrate into your own application, all bets are off.

---

### Post by gvanto on 2009-03-07
Ok i've made it a inline method, now it works. Guess it was violating the good ol' rule of not having executable code in header files (and if you do, to make it 'inline')

Again, thanks for some wicked good stuff DWhitney

G

---

### Post by dwhitney67 on 2009-03-07
I came up with another piece of code the other day to tokenize strings; you may want to take a look at it.  It's more C++-ish, but without using Boost.

Here's the [link]("http://ubuntuforums.org/showpost.php?p=6844524&postcount=11").

---

### Post by gvanto on 2009-03-07
thanks I like your boost way Dwhitney, its good :-)

---

### Post by &#956; . on 2009-03-07
From what you describe, this is the most efficient way I can think of to store it (which is basically Krupski's approach):
```

//blah blah blah

typedef struct{
	char *s;
	int q,t,n;
	double p;
} thing;

map <string, thing> keys;

//etc

```

The map and char* probably aren't needed though. What exactly you are trying to do?

---

