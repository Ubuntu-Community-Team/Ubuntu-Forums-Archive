---
title: "how to use gbd?"
date: 2009-02-27
forum: Programming Talk
---

### Post by tneva82 on 2009-02-27
Some sort of quick tutorial on how to track segmentation errors with gdb would be appreciated.

Tried on command line gbd executable-file. So far so good.

Then typed run

Program runs a while and I got this output:

```
[Thread debugging using libthread_db enabled]
[New Thread 0xb78366c0 (LWP 10276)]

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xb78366c0 (LWP 10276)]
0xb7b5de04 in strcpy () from /lib/tls/i686/cmov/libc.so.6
```

Not much of a help here. So probably I need to do something bit more to get more of an idea where I'm going kaboom?

---

### Post by dwhitney67 on 2009-02-27
'gdb' was and is helpful if you are running your application in a console.  If you are using a windowing manager (e.g. gnome), then consider using 'ddd' as the GUI front-end to 'gdb'.

As for debugging C or C++ applications, make sure that you compile your source code module(s) with the '-g' option.  This will ensure that symbolic information is included within the executable.

P.S.  'ddd' is available via Synaptic or apt-get.

---

### Post by tneva82 on 2009-02-27
Well. The server side of code will be purely text based since it just deals with information and communicates with client. Clients will use openGL to draw graphical things so I doubt ddd is needed.

As for -g tried but didn't change output from above :(

Atleast I have managed to figure where in general it crashes. When I try to add third creature to vector. Odd that one. Why first and second goes fine but third one crashes? For that I would like more debug information.

Can't figure why that crashes. 3 identical push_back calls, 2 works, 3rd crashes. ARGH!

Edit: Actually DDD was precicely groovy. And found out precicely where segmentation error comes. Here:

```

    temp=strtok(NULL, ";");
    strcpy(name, temp);

```

Very, VERY strange. Why this would work twice in a row and THEN crash? When precicely same line is parsed with strtok()? Odd.

AAAAAAAAARGG!

Ran out of disk space and for some reason that caused parts of code to vanish just like that while debugging. Goddamit. Hopefully this file wasn't that much altered since last backup.

Edit: Thankfully not at all and it was just one file. God bless backups!

---

### Post by monkeyking on 2009-02-27
you should use gdb like this

[PHP]gdb ./yourprog
run yourargs
[/PHP]
when the program crashes type

[PHP]bt[/PHP]
this will give give you the backtrace of the program stack.

If you have compiled with -g this should tell you which line.

---

### Post by tneva82 on 2009-02-27
> **monkeyking said:**
> If you have compiled with -g this should tell you which line.

So that's how it works. Groovy. Confirmed what ddd already told me after stepping over a lot. It's the strcpy. Now all I need to do is figure out WHY that causes crash.

---

### Post by dwhitney67 on 2009-02-27
More than likely "temp" is NULL (0) when you perform the strcpy().

When using 'ddd', you can move your mouse pointer over the variable, and it should be able to tell you its current value.  You may need to set a breakpoint on the line you want to examine so that you can step through the code before the segfault.

Btw, if you are trying to pull individual values from a semi-colon delimited string, then try this:
```

...

// assume str has value like 10;20;30;40;50
char* tmp = strtok(str, ";");

while (tmp)
{
  int value = atoi(tmp);

  ...

  tmp = strtok(0, ";");
}

...

```

---

### Post by tneva82 on 2009-02-27
> **dwhitney67 said:**
> More than likely "temp" is NULL (0) when you perform the strcpy().

Negative. Added printf("%s\n", temp) which showed 3 text lines and then BANG. I'll look over with ddd though.

> Btw, if you are trying to pull individual values from a semi-colon delimited string, then try this:

Isn't that what I'm essentially doing? Except that variables I store aren't in array but named so I can't really do while loop since the variable changes for every strtok.

Of course I could use array but then I would need to keep in mind which index had which item. Not good. Named variables help readability as I don't have to remember variable[0] is id, variable[1] is type, variable[2] is x position etc etc etc.

---

### Post by dwhitney67 on 2009-02-27
I was thinking of ways to assist you with your effort, and I came up with the following Tokenizer class and a follow-up example.  Maybe you can use it within your project?

Tokenizer.h:
```

#ifndef TOKENIZER_H
#define TOKENIZER_H

#include <string>
#include <vector>
#include <cstdlib>
#include <cstring>


class Tokenizer
{
  public:
    class TokenString
    {
      public:
        TokenString(const std::string& str) : m_str(str) {}

        operator int() const                { return atoi(m_str.c_str()); }
        operator unsigned int() const       { return (unsigned int)atoi(m_str.c_str()); }
        operator float() const              { return strtof(m_str.c_str(), 0); }
        operator double() const             { return strtod(m_str.c_str(), 0); }
        operator const char* const() const  { return m_str.c_str(); }

      private:
        std::string m_str;
    };

    typedef std::vector<TokenString> Tokens;
    typedef Tokens::const_iterator   CIter;

    Tokenizer(const std::string& str, const std::string& delims)
    {
      char* tmp1  = strdup(str.c_str());
      char* token = tmp1;

      token = strtok(token, delims.c_str());

      while (token)
      {
        m_tokens.push_back(TokenString(token));

        token = strtok(0, delims.c_str());
      }

      free(tmp1);
    }

    CIter begin() const { return m_tokens.begin(); }
    CIter end()  const  { return m_tokens.end();   }

  private:
    Tokens m_tokens;
};

#endif

```

Example.cpp:
```

#include "Tokenizer.h"
#include <iostream>

struct Data
{
  unsigned int value;
  std::string  str1;
  std::string  str2;
  double       dbl;
  float        flt;

  friend std::ostream& operator<<(std::ostream& os, const Data& data)
  {
    os << "value = " << data.value << '\n'
       << "str1  = " << data.str1  << '\n'
       << "str2  = " << data.str2  << '\n'
       << "dbl   = " << data.dbl   << '\n'
       << "flt   = " << data.flt;

    return os;
  }
};

int main()
{
  char str[256] = "10;string 1;string 2;20.2;13.3";

  Tokenizer        tk(str, ";");
  Tokenizer::CIter it = tk.begin();

  Data data;

  data.value = *it++;
  data.str1  = std::string(*it++);
  data.str2  = std::string(*it++);
  data.dbl   = *it++;
  data.flt   = *it++;

  std::cout << data << std::endl;
}

```

Of course, adapt the Data structure above to match your own, and supply the appropriate string(s) read from your data file in lieu of the test string given above.  This will obviate the need for you to play around with C-strings and with strtok().

P.S.  Boost has a better and more complete Tokenizer object.  The one developed above can be deemed to be a "light-weight" version.

---

