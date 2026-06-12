---
title: "Need help translating Java to C++"
date: 2010-04-27
forum: Programming Talk
---

### Post by dwhitney67 on 2010-04-27
I need to translate some Java code to C++; I'm not having much success.

Here's an example of the Java code:
```

private static final String ITEMS[][] =
{
   {"one", "two", "three"},
   {"four", "five", "six", "seven", "eight"},
   {"nine", "ten"}
};

```
I've tried replacing the Java String with the STL string, without success.  I've also tried using const char**.  In both cases, I get a syntax error when attempting to compile.

```

static const char** ITEMS[] =
{
   {"one", "two", "three"},
   {"four", "five", "six", "seven", "eight"},
   {"nine", "ten"}
};

```
The code above is merely an example of what of the code I am translating.  The actual code/data I am working with has 7 rows, with a variable number of columns (one of which is 56 columns wide).  However it would be nice if the code would support a variable number of rows too.

Short of specifying the number of columns to some arbitrary number (say 20), is there another approach I should consider?

---

### Post by CptPicard on 2010-04-27
What have you done to the real dwhitney67 so you have to ask a C++ question? ;)

Java is fine with the variable length arrays because they're all objects on heap, with lengths known. A C++ compiler will want to lay that out contiguously so that it's indexable, so the size of the internal stuff needs to be known and the same...

I suppose you'll just have to build this dynamically instead of a static initialization...

---

### Post by dwhitney67 on 2010-04-27
> **CptPicard said:**
> What have you done to the real dwhitney67 so you have to ask a C++ question? ;)

I'm still alive and well, but I just returned from a 3-week holiday.

> **CptPicard said:**
> 
I suppose you'll just have to build this dynamically instead of a static initialization...
Yes, I just got done doing this.  I placed the data in a flat file, and read it in, storing it in an STL vector that is defined to hold an STL vector of STL strings.
```

std::vector< std::vector<std::string> >

```

---

### Post by LKjell on 2010-04-27
Welcome back!

I never knew that C++ had that kind of limitation.
Another way I can think of is to make an array of struct where the structs contains an array of strings. The syntax might seem a bit odd.

---

### Post by CptPicard on 2010-04-27
> **LKjell said:**
> 
Another way I can think of is to make an array of struct where the structs contains an array of strings.

You won't be able to get around the issue. The compiler will still want to know the exact size of the elements of the top-level array.

---

### Post by Zugzwang on 2010-04-27
Probably you know of the following "solution" yourself, but for reference I'll state the following possibility:
```

static const char* LINE1[] = {"one","two","three"};
static const char* LINE2[] = {"four","five","six","seven","eigth"};
static const char* LINE3[] = {"nine","ten"};

static const char** ITEMS[] = {LINE1,LINE2,LINE3};

```

---

### Post by Lux Perpetua on 2010-04-27
As I recall, the new C++ standard was supposed to get around some of these limitations by allowing arbitrary types to be constructed using brace-delimited initializers. So you would be able to do: ```
vector<vector<string>> ITEMS = {
   {"one", "two", "three"},
   {"four", "five", "six", "seven", "eight"},
   {"nine", "ten"}
};
```Speaking of which, it was also supposed to fix the reallocation problems with vector<vector<...>>.

---

### Post by dwhitney67 on 2010-04-27
> **Zugzwang said:**
> Probably you know of the following "solution" yourself, but for reference I'll state the following possibility:
```

static const char* LINE1[] = {"one","two","three"};
static const char* LINE2[] = {"four","five","six","seven","eigth"};
static const char* LINE3[] = {"nine","ten"};

static const char** ITEMS[] = {LINE1,LINE2,LINE3};

```

Sorry for the late reply; I guess my email notification is not working very well today.

Anyhow, I tried what you have shown above earlier as well.  While it is syntactically correct (ie. it compiles), I found that I was unable to deduce how many entries where in a particular LINE.

-------

Wait!  The lite-bulb just came on....

With the idea above, I could insert a null at the end of each LINE, thus allowing me to iterate over the strings without running off into never-never-land.

This works:
```

#include <iostream>

static const char* LINE1[] = {"one","two","three", 0};
static const char* LINE2[] = {"four","five","six","seven","eight", 0};
static const char* LINE3[] = {"nine","ten", 0};

static const char** ITEMS[] = {LINE1,LINE2,LINE3};

int main()
{
   const size_t numItems = sizeof(ITEMS) / sizeof(char*);

   for (size_t n = 0; n < numItems; ++n)
   {
      const char** list = ITEMS[n];
      const char*  str  = *list;

      while (str != 0)
      {
         std::cout << str << std::endl;

         str = *(++list);
      }
   }
}

```

Thanks Zugzwang!

---

### Post by dribeas on 2010-04-27
You can make use of STL containers together with boost::assign, not the prettiest, but hey:

```

#include <boost/assign/list_of.hpp>
#include <vector>

int main() {
   using namespace boost::assign;
   typedef std::vector<std::string> string_vector;

   std::vector< string_vector > v = 
         list_of< string_vector >( list_of("Hi")("there") )
                                 ( list_of("How")("are")("you")("?") )
                                 ( list_of("Say")("goodbye")("!") );

```

---

