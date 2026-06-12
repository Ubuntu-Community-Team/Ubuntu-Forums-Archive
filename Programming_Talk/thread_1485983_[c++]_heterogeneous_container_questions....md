---
title: "[c++] heterogeneous container questions..."
date: 2010-05-17
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2010-05-17
Hi, all. I think I need some heterogeneous container but I am not really sure. I want to consider my options before fully reading about them.

**Why I want them?/What do I want to accomplish?**

I am writing a program and now I am at the stage, where I implement preferences/options read/writing. I want to store the program's settings in a map-like container, so I can retrieve the value by using a descriptive-keystring. The settings are of different value type. Some are integers, some bools, some strings etc. So I cannot use std::map directly.
First of all, is this approach to reading/writing/handling program settings advisable? Can you recommend some other way?
Secondly, how do I store different types in a map-like container? I read some articles that said I can use some base-class and then derive my classes from there and use the STL containers. The problem is I didn't find a good tutorial/guide explaining that. Moreover, is this going to work with simple, fundamental types like int and bool?
Can you give me some examples(with comments)? Or point me to some useful guide/tutorial?

---

### Post by dwhitney67 on 2010-05-17
You can define a common base-class for each of your objects (similar to Java's Object class), or you can consider creating a wrapper object that supports the basic data types you described in your post.

A wrapper object would store it's value, say as a string, yet provide converters for the data types you are interested in.

For example:
```

#include <cstdlib>
#include <string>
#include <sstream>
#include <iostream>

class Data
{
public:
   Data(const std::string& data) : m_data(data) {}

   Data(const int data)
   {
      std::stringstream oss;
      oss << data;
      m_data = oss.str();
   }

   Data(const bool flag) : m_data(flag ? "1" : "0") {}

   // converter routines

   operator const char*() const { return m_data.c_str(); }
   operator int() const         { return atoi(m_data.c_str()); }
   operator bool() const        { return !(atoi(m_data.c_str()) == 0); }

private:
   std::string m_data;
};

int main()
{
   Data data(5);

   const char* str   = data;
   const bool  flag  = data;
   const int   value = data;

   std::cout << "str   = " << str << "\n"
             << "flag  = " << flag << "\n"
             << "value = " << value
             << std::endl;
}

```
This type of object can be used in an STL map.

---

### Post by johnl on 2010-05-17
The "C" way to do this would be to use a union.

If you are open to using the boost library, you can accomplish the same thing with boost::any (which is similar to the wrapper approach described above) or boost::variant (which is similar to a union).

My preference in this situation would be to just create a 'settings' class, with a get/set member for each individual setting.  You could have save() and load() methods, etc.  How you stored the items inside your class would be up to you, but you could for example have a few different std::maps of different types (eg, map<string>, map<bool>, etc) and then get/set functions like so:

```

const std::string& settings::get_string(const std::string& name)
{ return mystringmap[name]; }
int settings::get_int(const std::string& name) 
{ return myintmap[name]; }
/* or you could use template specialization or something 
 * else fancy */

```

---

### Post by SaintDanBert on 2010-05-17
I believe that the Standard Template Library offers an implementation of what I think is called an "associative array."  Here the array indices are a string and the array data can be any known object.

Is that what you are looking for?
~~~ 0;-Dan

---

### Post by MadCow108 on 2010-05-17
no an associative array (map in C++) can only save data of two types, the key and the value.

of course you could use void pointers as the value but then you somehow need type information e.g. by a common base class + RTTI.

I would recommend boost any or the common base class method mentioned by dwhitney and johnl
[http://www.boost.org/doc/libs/1_43_0/doc/html/any.html](http://www.boost.org/doc/libs/1_43_0/doc/html/any.html)

---

### Post by SledgeHammer_999 on 2010-05-17
Thank you guys for your input. I tried to understand what you wrote but I cannot fully wrap my head around this topic :s.  Boost::Any looks cool but I don't want to put another dependency on my project. As far as I can tell, it is a bit overkill to go through this trouble just to store the settings, which will 2-3 simple types. 

I think I'll go with **johnl's** idea of a 'preferences' class. But I especially like this functionality from the std::map:
```

std::map<std::string, something> m;
m.["draw_shadows"] = false;
m.["active_seconds"] = 5;

//some code handler
if (m.["draw_shadows"]) do something;

//a timeoute callback
timeout(m["active_seconds"]);
```

I think I'll overload the [] operator in the preferences class and make it return many types(the one I am using). Internally I will use one variable(of the appropriate type) for each setting. Also I will have predefined key-values of std::string since I don't actually need the functionality of adding/removing elements at runtime. So when a std::string key-value is used in [] then I will if/else if through the predefined key list. I think it will be a little time consuming but it is the easiest on my mind. I just hope this is feasible.

---

### Post by SledgeHammer_999 on 2010-05-17
> **SledgeHammer_999 said:**
> Thank you guys for your input. I tried to understand what you wrote but I cannot fully wrap my head around this topic :s.  Boost::Any looks cool but I don't want to put another dependency on my project. As far as I can tell, it is a bit overkill to go through this trouble just to store the settings, which will 2-3 simple types. 

I think I'll go with **johnl's** idea of a 'preferences' class. But I especially like this functionality from the std::map:
```

std::map<std::string, something> m;
m.["draw_shadows"] = false;
m.["active_seconds"] = 5;

//some code handler
if (m.["draw_shadows"]) do something;

//a timeoute callback
timeout(m["active_seconds"]);
```

I think I'll overload the [] operator in the preferences class and make it return many types(the one I am using). Internally I will use one variable(of the appropriate type) for each setting. Also I will have predefined key-values of std::string since I don't actually need the functionality of adding/removing elements at runtime. So when a std::string key-value is used in [] then I will if/else if through the predefined key list. I think it will be a little time consuming but it is the easiest on my mind. I just hope this is feasible.

Now that I think of it, this is overkill too. I will just make the variables public and access them directly. This will have far more reduced complexity and code writing :D

---

### Post by dwhitney67 on 2010-05-17
Good luck with your project.  :rolleyes:

---

### Post by unknownPoster on 2010-05-17
> **SledgeHammer_999 said:**
> Now that I think of it, this is overkill too. I will just make the variables public and access them directly. This will have far more reduced complexity and code writing :D

[-X

And possibility introduce a plethora of bugs. Any educated software engineer would feel very uncomfortable with public data attributes. What you're doing is a terrible idea.

---

### Post by TheStatsMan on 2010-05-18
I have used something like this before for a heterogenous container

```

#include <iostream>
#include <map>
#include <boost/any.hpp>

using namespace std;
using boost::any_cast;


int main()
{
    map<string,boost::any> mvar;    

    string test="test";

    mvar["double"] =5.3;
    mvar["string"] = test;

    cout << any_cast<double>(mvar["double"]) << endl;
    cout << any_cast<string>(mvar["string"]) << endl;

  return 0;
}


```

---

### Post by nvteighen on 2010-05-18
Clearly, dwhitney67's approach is the most logical... use a base wrapper class and then a "homogeneous" container set to that base class. That's how GTK+/GLib containers work in C, by the way... everything is a gobject or GtkWidget... So, it's not that such approach means heading to unknown realms of programming techniques, as it's a widely and reliable way to do it.

The other possibility is to use Boost, as others have said... The dependency issue is just none, as the Boost code is, IIRC, in its headers, so it's rather a compile-time dependency than a runtime one.

---

