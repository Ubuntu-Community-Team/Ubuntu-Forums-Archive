---
title: "[C++] STL  map &amp; vector"
date: 2010-10-15
forum: Programming Talk
---

### Post by erotavlas on 2010-10-15
Hi,

I have a newbie problem, how can I access to elements of a map if the key is a vector of string?

```
typedef map<vector<string>, float> Map;

Map myMap;

typedef vector<string> Vector;

Vector myVector;
```
Adding a values
```

myVectore.push_back("x1");
myMap[myVectore] = value1;

myVectore.push_back("x2"); 
myMap[myVector] = value2;

myVector.push_back("x1, x3");
myMap[myVector] = value3;
```If I try to read the map

```
for (map<vector<string>, float>::const_iterator i = myMap.begin(); i != myMap.end(); ++i)
     cout << i->first << " " << i->second;
```I get a compilation error because the first element of the map is a vector of string. How can I read it correctly?

---

### Post by dwhitney67 on 2010-10-15
I think you may need to re-evaluate your design.

Using a vector<whatever> as the key to the (hash) map seems dubious.

What information are you trying to associate together?

P.S.  Each of the assignments you make to the map is overwriting the previous.

---

### Post by erotavlas on 2010-10-15
> **dwhitney67 said:**
> I think you may need to re-evaluate your design.

Using a vector<whatever> as the key to the (hash) map seems dubious.

What information are you trying to associate together?


Hi,

I would like to associate the following functions A(x1,x2,x3)=2 where A is a function name and xi are the parameters while 2 is the value.

map <vector <string>, float>

---

### Post by MadCow108 on 2010-10-15
the key of a map (which btw. cannot be a classic hash container according to standard [map requires logN worst case]) must satisfy the weak ordering constraint.
meaning it must have a less than (<) operator.

a vector does not have this by default
you would have to write your own
edit: not correct, see below

quick hackup:
```

#include <iostream>
#include <map>
#include <vector>
#include <string>
#include <functional>

using namespace std;

typedef vector<string> Vector;
struct comp : public binary_function<Vector, Vector, bool> {
  bool operator()(const Vector &a, const Vector &b) const
  {
    // some random ordering function
    for (Vector::const_iterator it = a.begin(), itb = b.begin(); it !=a.end() && itb !=b.end(); ++it, ++itb) {
      if (*it < *itb)
        return true;
    }
    return false;
  }
};

int main(int argc, const char *argv[])
{
  typedef map<vector<string>, float, comp> Map;

  Map myMap;


  Vector myVector;
  
  myVector.push_back("x1");
  myMap[myVector] = 1;

  myVector.push_back("x2"); 
  myMap[myVector] = 2;

  myVector.push_back("x1, x3");
  myMap[myVector] = 3;
  for (Map::iterator it = myMap.begin(); it != myMap.end(); ++it) {
    for (Vector::size_type i = 0; i < it->first.size(); i++) {
      cout  << it->first[i] << " ";
    }
    cout <<  it->second << endl;
  }
  return 0;
}

```
as you see by the output the assignments are correct, the map copies the keys (which are then immutable inside the map).

but do not expect such a structure to be very fast

---

### Post by spjackson on 2010-10-15
> **MadCow108 said:**
> the key of a map (which btw. cannot be a classic hash container according to standard [map requires logN worst case]) must satisfy the weak ordering constraint.
meaning it must have a less than (<) operator.

a vector does not have this by default
you would have to write your own

I'm puzzled by this. std::vector does have a less than operator in ISO C++98. Could you please clarify?

---

### Post by dwhitney67 on 2010-10-15
> **erotavlas said:**
> Hi,

I would like to associate the following functions A(x1,x2,x3)=2 where A is a function name and xi are the parameters while 2 is the value.

map <vector <string>, float>

You stated that you want to store functions, yet you only presented the one "function" above.

Perhaps if you created a structure to define the function??
```

struct Function
{
   std::string              name;
   std::vector<std::string> variables;
   double                   value;
};

```
Then something like:
```

std::map<std::string, Function>;

```
Where the map "key" is the name of the function itself.

Initially you proposed using the "same" key in your map, over and over again, all you are doing is augmenting the vector each time, thus creating a unique key, but probably not what you want.

Test the following code to see the output:
```

#include <string>
#include <vector>
#include <map>
#include <iterator>
#include <iostream>

using namespace std;

typedef vector<string>      Vector;
typedef map<Vector, double> Map;

int main()
{
   Vector vec;
   Map theMap;

   vec.push_back("x1");
   theMap[vec] = 2;

   vec.push_back("x2 x3");
   theMap[vec] = 4;

   vec.push_back("x2");
   theMap[vec] = 6;

   for (Map::const_iterator it = theMap.begin(); it != theMap.end(); ++it)
   {
      const Vector& mapVec = it->first;
      const double  mapVal = it->second;

      copy(mapVec.begin(), mapVec.end(), ostream_iterator<string>(cout, " "));
      std::cout << " = " << mapVal << std::endl;
   }
}

```

---

### Post by TheBuzzSaw on 2010-10-15
I'll just add to what's already been said: having an STL vector as the key to an STL map is a major red flag. A *pointer* would not be a big deal, but keeping the original vectors in as those map keys is just asking for so much trouble.

---

### Post by schauerlich on 2010-10-15
> **dwhitney67 said:**
> You stated that you want to store functions, yet you only presented the one "function" above.

I think he wants to do some sort of memoization. Just a guess though, his description is a bit vague.

---

### Post by MadCow108 on 2010-10-15
> 
I'm puzzled by this. std::vector does have a less than operator in ISO C++98. Could you please clarify?

sorry I overlooked the operators in the reference :/
vectors have lexical_compare as less than operator.

> **TheBuzzSaw said:**
> I'll just add to what's already been said: having an STL vector as the key to an STL map is a major red flag. A *pointer* would not be a big deal, but keeping the original vectors in as those map keys is just asking for so much trouble.

why is it asking for trouble?
it is probably not very efficient, but it works flawlessly besides that.

using a (normal) pointer on the other hand is asking for trouble. Pointers can be invalidated, the vector map keys not (they are immutable). An immutable pointer is not worth much if the memory it points to is not.
If you want to save some copying during inserts and removes (which is implementation dependent) use shared pointers.

---

### Post by TheBuzzSaw on 2010-10-15
> **MadCow108 said:**
> 
why is it asking for trouble?
it is probably not very efficient, but it works flawlessly besides that.

using a (normal) pointer on the other hand is asking for trouble. Pointers can be invalidated, the vector map keys not (they are immutable). An immutable pointer is not worth much if the memory it points to is not.
If you want to save some copying during inserts and removes (which is implementation dependent) use shared pointers.

Seriously?

OK, first off, how do you attempt a lookup? Create a new vector, fill it with elements, and that becomes your key? What design would possibly justify this type of data organization?

As for using pointers as keys, it's not that big of a deal because it technically does not matter if the pointers become invalidated. (They shouldn't, provided you have a good data flow, and scope is elegantly maintained.) A dead pointer is still just a number, and it works great as a key lookup. You are addressing the issue of *dereferencing* that pointer, which is another aspect of design entirely. As a map key, though, it's just a number, and it is far safer and more useful (and able to handle math operators) than an actual vector instance.

---

### Post by worksofcraft on 2010-10-15
> **TheBuzzSaw said:**
> 
OK, first off, how do you attempt a lookup? Create a new vector, fill it with elements, and that becomes your key? What design would possibly justify this type of data organization?


Hum, interesting discussion you got going here ;)

I tend to use ordinary c strings for my map keys specially because quite often they are constant literal strings in my code.

One thing to realize though is that STL containers do not actually necessarily imply a lot of overhead.

Certainly some other languages might well produce huge data structures with cascades of methods calling parent class method, involving dynamic memory allocations and garbage collection.

However, the beauty of a language that provides **templates** is that the compiler can generate *just what it needs*. A while back I was looking at the overhead in using STL vectors and I discovered the compiler was essentially translating it directly into pointers and arrays that I could see little scope for coding any more efficiently myself :)

p.s. see here is a bit of my code where G is an STL map that represents my graphical user interface and the map contains Gtk widgets that inherit the STL implemented Glib:ustring... so in the following I use constant C string to index my GUI and obtain the value stored in widgets on the display as a c_string that I pass to my function. It reads easily and the code it produces has little overhead :)
[php]
set_digits(
    G["NormDigits"].c_str(),
    G["AltDigits"].c_str()
);
[/php]
note: here NormDigits and AltDigits are the names that I gave two different combo boxes defined in my .glade file.

---

### Post by MadCow108 on 2010-10-15
> **TheBuzzSaw said:**
> Seriously?
OK, first off, how do you attempt a lookup? Create a new vector, fill it with elements, and that becomes your key? What design would possibly justify this type of data organization?


why shouldn't it become a key?
Anything which can be compared weakly in a way that makes sense can be a map key.
This is one of the great benefits of the template system. You could even use an map as the key of a map!
And where is the problem in filling a vector before doing the lookup?
The key data must come from somewhere, you might as well save it in a vector if it is composed of more than one entity.

What makes sense of course depends on the application.
e.g. this pseudocode makes a very simple memorizer for dynamic programming:
```

map["1", "plus", "2"] = 3;
map["3", "minus", "2"] = 1;

{
res = map.insert(["3", "horribly expensive operation I never want to do more than once", "2"], "dummy_value");
if (res.second == true)
  res.first = do_the_calculation();
return res.first;
}


```

you could obviously also just concatenate the list of strings to a larger string and receive the same result with a more "classical" map.
(and of course there may be much better solutions for these problems, but that does not necessarily make this one wrong)

and of course you can use pointers, but it is generally considered good style in C++ to avoid their use. It simplifies many aspects of complex designs.
Of course there is no problem in using them correctly, but sometimes it simplifies things if you avoid them (and this might very well be such a case, you don't gain much from using pointers on a good map implementation)

---

### Post by erotavlas on 2010-10-20
> **dwhitney67 said:**
> You stated that you want to store functions, yet you only presented the one "function" above.

Perhaps if you created a structure to define the function??
```

struct Function
{
   std::string              name;
   std::vector<std::string> variables;
   double                   value;
};

```Then something like:
```

std::map<std::string, Function>;

```Where the map "key" is the name of the function itself.

Initially you proposed using the "same" key in your map, over and over again, all you are doing is augmenting the vector each time, thus creating a unique key, but probably not what you want.

Test the following code to see the output:
```

#include <string>
#include <vector>
#include <map>
#include <iterator>
#include <iostream>

using namespace std;

typedef vector<string>      Vector;
typedef map<Vector, double> Map;

int main()
{
   Vector vec;
   Map theMap;

   vec.push_back("x1");
   theMap[vec] = 2;

   vec.push_back("x2 x3");
   theMap[vec] = 4;

   vec.push_back("x2");
   theMap[vec] = 6;

   for (Map::const_iterator it = theMap.begin(); it != theMap.end(); ++it)
   {
      const Vector& mapVec = it->first;
      const double  mapVal = it->second;

      copy(mapVec.begin(), mapVec.end(), ostream_iterator<string>(cout, " "));
      std::cout << " = " << mapVal << std::endl;
   }
}

```


If I use your code the result is

```


x1 = 2

x1 x2 x3 = 4

x1 x2 x3 x2 = 6



```but I would like to get 

```


x1 = 2

x2 x3 = 4

x2 = 6



```I need to use an iterator for vector
```

for(Map::const_iterator it = theMap.begin(); it != theMap.end(); ++it) {


for(Vector::const_iterator vt = it->first.begin(); vt != it->first.end(); ++vt) {

cout << *vt  << " = " << it->second;

}

}
```This is uncorrect. How can I solve it?

---

### Post by dwhitney67 on 2010-10-20
erotavlas,

I think you are missing a fundamental issue... the usage of a vector as the key to a map is flawed.  Consider using a different key value.

---

### Post by erotavlas on 2010-10-20
> **dwhitney67 said:**
> erotavlas,

I think you are missing a fundamental issue... the usage of a vector as the key to a map is flawed.  Consider using a different key value.


Sorry, but I can't understand how I can realize what I want. ](*,)

I need to use map<vector<string>, float> because the first element of the map is a vector of input variables (f(x1,x2,x3,...). I have many function f1,f2,..., for each of this I have to define a value on a set of input variables (f1(x1)=2, f1(x2, x3)=3; f2 (x1)=0...). The functions are defined in separate data structure that is linked to the map.

---

### Post by dwhitney67 on 2010-10-20
What is wrong with the following approach?
```

#include <string>
#include <vector>
#include <map>

struct Function
{
   std::string              name;
   std::vector<std::string> vars;
   double                   result;
};

typedef std::map<std::string, Function> Map;

int main()
{
   Function f1;

   f1.name = "f1";
   f1.vars.push_back("x1");
   f1.result = 2;

   Map theMap;

   theMap[f1.name] = f1;

   ...
}

```

---

### Post by schauerlich on 2010-10-20
> **dwhitney67 said:**
> What is wrong with the following approach?

He's not mapping a function name to a result, he's mapping a representation of a function call to a result. If I'm understanding correctly, he wants something like this:

```
{
fact(1) : 1,
fact(3) : 6,
fact(4) : 24,
fib(6)  : 8,
fib(7)  : 13,
...
}
```

but using functions that take string arguments. Basically, memoization. Your example only stores one call per function at a time.

Of course, this will only work on pure functions (referential transparency and all).

---

### Post by MadCow108 on 2010-10-20
> **erotavlas said:**
> If I use your code the result is

```


x1 = 2

x1 x2 x3 = 4

x1 x2 x3 x2 = 6



```but I would like to get 

```


x1 = 2

x2 x3 = 4

x2 = 6



```

clear the vector before each insert, or use a new one.

---

### Post by erotavlas on 2010-10-21
> **dwhitney67 said:**
> What is wrong with the following approach?
```

#include <string>
#include <vector>
#include <map>

struct Function
{
   std::string              name;
   std::vector<std::string> vars;
   double                   result;
};

typedef std::map<std::string, Function> Map;

int main()
{
   Function f1;

   f1.name = "f1";
   f1.vars.push_back("x1");
   f1.result = 2;

   Map theMap;

   theMap[f1.name] = f1;

   ...
}

```

I need of a little bit complex structure. Here is too long to describe all the reasons.

Final result is to store every function and its values for a set of input variables (f1(x1)=2, f(x2)=3,f1(x3, x4)=0, f2(x2)=0...). I have a external map that contains all function, each function is stored in a class. ( map <string, Function>) where string is name function and Function is class that stores the function and  its values for a set of variables.
The class contains a map map< vector <string>, float> > where for each function are stored the values.

For this reason I need this type of map. I'm not a C++ expert programmer and I don't know how I can read the map after filling it. ](*,)

---

