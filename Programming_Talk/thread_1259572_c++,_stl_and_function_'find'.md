---
title: "c++, stl and function 'find'"
date: 2009-09-06
forum: Programming Talk
---

### Post by januzi on 2009-09-06
Hi

I have got problem with function "find". G++ says that:
> 
g++ -Wall -pedantic -g -pg  -I/usr/include/graphviz -L/usr/lib/graphviz/ -I/usr/include/fltk-1.1/ -L/usr/lib/fltk-1.1/  -c Plik.cpp -o Obj/Plik.o

error: no matching function for call to ‘find(__gnu_cxx::__normal_iterator<std::basic_string<char, std::char_traits<char>, std::allocator<char> >*, std::vector<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::allocator<std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > >, __gnu_cxx::__normal_iterator<std::basic_string<char, std::char_traits<char>, std::allocator<char> >*, std::vector<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::allocator<std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > >, char*)’
The same cpp "works" fine under gentoo and mingw32. 
As for the function and file, it looks like that:
```

using namespace std ;

void Plik::dodaj_include( int i, string include, int nr_linii,
              vector<string> &nazwy_plikow ) {
// ...
vector<string>::iterator iter ;
  iter = find( nazwy_plikow.begin(), nazwy_plikow.end(), (char *)nowy.c_str());
// ...
}

```Could somebody tell me what is wrong with this code ?

---

### Post by dwhitney67 on 2009-09-06
EDIT:

I misread your post; you are perhaps looking to use the find() as defined in the <algorithm> header file.

--------------------

EDIT #2:

Here's an example of find():
```

#include <vector>
#include <algorithm>
#include <cassert>

int main()
{
   std::vector<int> vec;

   vec.push_back(10);
   vec.push_back(20);
   vec.push_back(30);

   std::vector<int>::iterator it = std::find(vec.begin(), vec.end(), 20);
   assert(it != vec.end());

   it = std::find(vec.begin(), vec.end(), 40);
   assert(it == vec.end());
}

```
--------------------

EDIT #3:

Damn... the Bacardi is working overtime today.

The issue with your code is the third parameter; since it appears you already have an STL string, just pass it directly.
```

vector<string>::iterator iter ;
  iter = find( nazwy_plikow.begin(), nazwy_plikow.end(), nowy);   // <--- see 3rd param

```

--------------------------

INITIAL RESPONSE - Disregard.

Umm, I hate to be the bearer of bad news, but the STL vector does not support the find() function.  Perhaps you are thinking of the STL map or multimap?

Refer [here for information]("http://www.cplusplus.com/reference/stl/vector/") on what the STL vector does provide.

---

### Post by Hosmion on 2009-09-06
What is STL?  Is it a programming C++ notepad or something?

If it is, I suggest using [SciTE]("http://scintilla.org/SciTE.html")..  I use it for my HTML/JavaScript Coding

---

### Post by Mirge on 2009-09-06
> **Hosmion said:**
> What is STL?  Is it a programming C++ notepad or something?

If it is, I suggest using [SciTE]("http://scintilla.org/SciTE.html")..  I use it for my HTML/JavaScript Coding

No, it's not an editor/IDE. See: [http://en.wikipedia.org/wiki/C++_STL](http://en.wikipedia.org/wiki/C++_STL)

---

### Post by Hosmion on 2009-09-06
Ok, thanks...

sorry..  I probably shouldnt post unless I know what it is :D

---

### Post by januzi on 2009-09-06
Thanks, I forgot about <algorithm>. 

So, mingw32 includes algorithm without asking ?

---

### Post by Habbit on 2009-09-07
> **dwhitney67 said:**
> Umm, I hate to be the bearer of bad news, but the STL vector does not support the find() function.

What requirement of the find function is left unfulfilled by the vector container class?
--EDIT--
or were you talking about a hypothetical find member function? (and thus your first edit)

---

### Post by dwhitney67 on 2009-09-07
> **Habbit said:**
> What requirement of the find function is left unfulfilled by the vector container class?
--EDIT--
or were you talking about a hypothetical find member function? (and thus your first edit)
Yes (to your second question).

---

### Post by dribeas on 2009-09-07
> **januzi said:**
> Thanks, I forgot about <algorithm>. 

So, mingw32 includes algorithm without asking ?

It might be the case. You should always add all the includes you need in your code. The fact that not including something works in a platform/compiler does not mean it will work in all other situations.  The standard defines minimum requirements on the inclusion headers. After including header X you will have X1...Xn symbols declared... but it does not require that only those symbols are declared. As a matter of fact, the STL can declare any and all symbols it wants within the standard limitations: all symbols beginning with double underscore (__) or single underscore and a capital letter (_X) or single underscore an a lower case letter as a symbol in the global namespace, or any and all symbols it so desires within the std namespace.

It is quite common that different compiler/STL versions have different inclusion paths. In some implementation of the STL the method std::basic_string<>::find could be implemented by a call to std::find on the string contents by calculating the difference of the resultant and begin() iterators. In that implementation including anything that included the string header would also include the std::find algorithm. That is just a simple example of why something that you did not ask for gets included.

Going back to the beginning, if you do not include all your required headers you will end with code that works in your current c++ implementation (compiler+stl) but does not in another environment.

As a side note, according to the C++ standard, the standard headers could have no real storage backup, that is, they could not exist as files as long as the compiler declared the same symbols after the header was included with angle brackets (<>). In the real world, I know of no compiler that decided to take that path, and all compilers do have a copy of the STL in real header files.

---

