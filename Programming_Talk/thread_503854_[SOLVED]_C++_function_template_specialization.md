---
title: "[SOLVED] C++ function template specialization"
date: 2007-07-18
forum: Programming Talk
---

### Post by Soybean on 2007-07-18
I'm still a little fuzzy on some of the details of C++ templates. I managed to get something like the following example working, but I don't understand *why* it works one way and not the other.

Without the bolded "inline", the following "thingy.hpp" still compiles, but fails to link if it's #included from more than one .cpp file. Inlining the specialization fixes it. Does anyone know why? Is there a way to do the same thing without inlining the function?

The relevant part of the linker error is "multiple definition of `void thingy::set<std::basic_string..." if that helps at all.

```

#ifndef THINGY_H_
#define THINGY_H_

#include <string>
#include <sstream>
using namespace std;

class thingy
{
	public:
		template<typename T>
		void set(const T & s);
	private:
		string value;
};

template<typename T>
void thingy::set(const T & s)
{
	stringstream ss;
	ss << s;
	ss >> value;
}

template<>
**inline** void thingy::set<string>(const string & s)
{
	value = s;
}

#endif

```

---

### Post by hod139 on 2007-07-18
Member function template specializations do not belong in a header file, as they will be defined multiple times, once for each inclusion (as you just saw).  It should be defined once in a Thingy.cpp file.  If you cut
```

template<>
void thingy::set<string>(const string & s)
{
    value = s;
}
```and paste it in the implementation file Thingy.cpp, everything should work fine.


However, there is another solution.  Why use template specialization at all?
```

#ifndef THINGY_H_
#define THINGY_H_

#include <string>
#include <sstream>

using namespace std;

class thingy
{
    public:
        template<typename T> void set(const T & s);
        void set(const string & s)
        { 
           value = s; 
        }
    private:
        string value;
};

template<typename T>
void thingy::set(const T & s)
{
    stringstream ss;
    ss << s;
    ss >> value;
}
#endif

```When the function set is called with a string, it will use the non templated function.   Else, it will instantiate a function for the calling type.

---

### Post by Soybean on 2007-07-18
> **hod139 said:**
> Member function template specializations do not belong in a header file, as they will be defined multiple times, once for each inclusion (as you just saw).  It should be defined once in a Thingy.cpp file. 
Ahh... ok! That makes sense. I had the two things categorized together in my head, but I guess the specialization is really closer to a normal function definition. 

> However, there is another solution.  Why use template specialization at all?
Heh... I considered something similar to your suggestion. But then I read a bit about how overloading interacts with templates. I got confused by the rules governing the decision between set(string) and set<string>(T), so I decided to go with template specialization since it seemed like the less confusing option. ;)

Anyway, thanks for your help! :) I'll try both, and maybe read up a bit more thoroughly on the overloading rules.

---

