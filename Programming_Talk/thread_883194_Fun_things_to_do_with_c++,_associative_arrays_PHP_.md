---
title: "Fun things to do with c++, associative arrays PHP style"
date: 2008-08-07
forum: Programming Talk
---

### Post by cszikszoy on 2008-08-07
If you've ever wanted to create associative arrays, like the ones found in PHP and Perl, you might be interested in this.  After going back to programming in C++ after doing a bit of PHP work, I really missed the ability to create associative arrays.  I researched a bit, and found out that this functionality can be recreated in C++ using the map standard library in C++.  For an example of see the following code:

```

 #include <string>
 #include <map>
 #include <iostream>
 
using namespace std;

int main()
{
    // age is a map from string to int
    map<string, int, less<string> >  age;
 
    age["Fred"] = 42;    // Fred is 42 years old
    age["Barney"] = 37;    // Barney is 37

    cout << "Fred is " << age["Fred"] << " years old" << endl;
    cout << "but Barney is " << age["Barney"] << " years old" << endl;
}

```

---

### Post by StOoZ on 2008-08-07
STL containers are amazing... :popcorn:

---

### Post by dwhitney67 on 2008-08-07
> **cszikszoy said:**
> If you've ever wanted to create associative arrays, like the ones found in PHP and Perl, you might be interested in this.  After going back to programming in C++ after doing a bit of PHP work, I really missed the ability to create associative arrays.  I researched a bit, and found out that this functionality can be recreated in C++ using the map standard library in C++.  For an example of see the following code:

```

 #include <string>
 #include <map>
 #include <iostream>
 
using namespace std;

int main()
{
    // age is a map from string to int
    map<string, int, less<string> >  age;
 
    age["Fred"] = 42;    // Fred is 42 years old
    age["Barney"] = 37;    // Barney is 37

    cout << "Fred is " << age["Fred"] << " years old" << endl;
    cout << "but Barney is " << age["Barney"] << " years old" << endl;
}

```
I recommend that before you become complacent with the map [] operator, that you understand an important pitfall when using it.

This pitfall will occur if you attempt to access the map using a key, in your case an std::string, that doesn't exist.  This will return a value, in your case a 0, and worse, it will create a new entry in your map.

So for instance, this may look good and will actually work, but now your map is "polluted" with an unwanted entry:
[PHP]std::cout << age["Foo"] << std::endl;[/PHP]
What you really want is a wrapper class around the map object, or a C-style static method that does something similar to the following:
[PHP]int getAge( std::string &name, std::map<std::string, int> &age )
{
  int years = -1;   // in case name not found in age map

  if ( age.find( name ) != age.end() )
  {
    years = age[name];
  }

  return years;
}[/PHP]
Btw, an std::multimap works similar to an std::map, however you are allowed to insert duplicate keys, whereas with an std::map, only unique keys are allowed.  A multimap could be used to store the names and telephone numbers you would find in a phone book.  Undoubtedly there is more than one "John Smith" in a particular area.

---

### Post by hod139 on 2008-08-07
Another thing to know about STL's map, it is not stored using a hash table.  It is stored as a red-black tree.  If you want a hash table representation, you can use gnu's hash_map, but know that it won't be portable.  The other option is to use [TR1]("http://en.wikipedia.org/wiki/Technical_Report_1")'s unordered_map, but again, until TR1 becomes officially standard, this is again not portable.

---

