---
title: "[C++] Working with char, vector"
date: 2008-09-10
forum: Programming Talk
---

### Post by Glaxed on 2008-09-10
Hello,

I'm trying to debug the following code.
The problem seems to be the char* array in str::get(void).

This header is an attempt at creating a string type (still very immature).

str::get should take the individual characters from the string vector, and piece it together into a char array. I'll work on str::add when I get the nuts and bolts down.

I would appreciate help a lot!
Thanks,
- glaxed

```

#ifndef STR_H
#define STR_H

#include <vector>

using std::vector;

class str {
    protected:
        vector<char> string;
        unsigned long int len;
        unsigned short int x;
    public:
        str(char*);
        ~str(void) {
            string.clear();
        }

        char* get(void);
        void add(char*);
};

str::str(char* line) {
    str::add(line);
}

void str::add(char* line) {
    for (x=0; line[x] != '/0'; x++) {
        string.push_back(line[x]);
        len++;
    }
}

char* str::get(void) {
    char* ret[len];
    for (x=0; x < len; x++) {
        ret[x] = &string.at(x);
    }
    return ret;
}

#endif // STR_H

```

---

### Post by rnodal on 2008-09-10
How many times are you planning on calling the get function? The way I see it is that you need to reset len back to zero once you move the characters from the vector to the array. I may be off.

-r

---

### Post by dwhitney67 on 2008-09-10
Why are you using a vector to store a string?  Perhaps as an exercise??

Consider using the STL string.

Btw, the 'string' variable you have in the code can be confusing since it is the same name as the STL string datatype.

Maintaining the 'len' variable is not necessary.  You can rely on the vector size() method to provide you that information.

The variable 'x' should be treated as a local variable, not a class variable.  It also should be declared as a size_t, not unsigned short.

Your get() function is declaring an array of pointers to char.  This is not what you want.  All you require is an array of char(s).  Unfortunately you will not be able to declare this array during runtime without allocating memory from the heap.  Maybe something like this would suffice:
[php]
class str
{
public:
  str(char *line)
  {
    while ( *line != '\0' )       // risky!!!!
    {
      m_string.push_back( *line );
      ++line;
    }

    m_strChr = 0;
  }

  ~str()
  {
    m_string.clear();   // not necessary, but nice to see

    if ( m_strChr != 0 )
    {
      delete []m_strChr;
    }
  }

  void add(char c)
  {
    m_string.push_back(c);
  }

  const char* str::get(void)
  {
    if (m_strChr != 0)                             // if allocated before, delete
    {
      delete []m_strChr;
    }

    m_strChr = new char[ m_string.size() + 1 ];    // allocate space for string + 1 for null char

    for (size_t x = 0; x < m_string.size(); ++x)   // copy chars from vector to array
    {
      m_strChr[x] = m_string[x];
    }
    m_strChr[ m_string.size() ] = '\0';            // add terminating null-char

    return m_strChr;
  }

private:
  std::vector<char> m_string;
  char *            m_strChr;
};
[/php]
P.S.  I renamed the member data m_string to distinguish it from STL string; also I added m_strChr.

P.S.S.  Unless you have a compelling reason, your class data (m_string) should be declared private, not protected.

---

### Post by Glaxed on 2008-09-10
(I'm writing this str class as a learning experience.)

As long as the str Object is in scope, I was planning to keep all of the characters in the vector. That way, the only time I'd need to modify "len" is if I use "str::add".

Let me explain how I want this thing to work...

The constructor should take a "string", i.e "char*", and put every "char" in the "char* array" into the "vector<char>". Every time it pops a new char in, it increases "len" by 1.

The "str::get" function should derive a "char*" from the "vector<char>".

The "str::add" function is basically the constructor - so I edited the first header I posted to be cleaner about it.

I'd like to keep "len", because it's cleaner than calling string.size() over and over again.

---
I don't understand your str::add or str::get function, at least not in theory.
The add function adds just a single character to the vector.
The get function looks like it should work, but I'm not sure. I get error messages whenever I try to assign a char in a char* to a char in the vector..

---

### Post by dwhitney67 on 2008-09-10
> **Glaxed said:**
> As long as the str Object is in scope, I was planning to keep all of the characters in the vector. That way, the only time I'd need to modify "len" is if I use "str::add".

Let me explain how I want this thing to work...

The constructor should take a "string", i.e "char*", and put every "char" in the "char* array" into the "vector<char>". Every time it pops a new char in, it increases "len" by 1.

The "str::get" function should derive a "char*" from the "vector<char>".

The "str::add" function is basically the constructor - so I edited the first header I posted to be cleaner about it.
Your intentions are crystal clear.  See my previous post.

---

### Post by Glaxed on 2008-09-10
I'm sorry, I was replying to the post before yours.
I updated it after I read yours.

I also wanted to ask;
What is the difference between private and protected?, 
and Why use size_t?

I'll try to run your code tomorrow. Thank you.

---

### Post by dribeas on 2008-09-11
Agreed @dwhitney67 with just small style differences

> **Glaxed said:**
> I'd like to keep "len", because it's cleaner than calling string.size() over and over again.

vector<>::size is a constant time operation, probably even inlined by the compiler so there is no performance advantage to use a local copy of the same data. Using your own copy makes your code less robust, as you must keep your internal data synchronized with that of vector.

---

### Post by Glaxed on 2008-09-11
Thanks for the clarification.

---

