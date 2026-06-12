---
title: "Problems Creating C++ Library"
date: 2010-04-10
forum: Programming Talk
---

### Post by StunnerAlpha on 2010-04-10
Ey guys, I am following this: [http://bcahelper.blogspot.com/2008/11/how-to-make-library-in-c.html](http://bcahelper.blogspot.com/2008/11/how-to-make-library-in-c.html) and I have this function that works just fine in my main.cpp file:

```

template <class T>
void printVect(vector<T> vect){
	for(long itr = 0; itr < (long)vect.size(); itr++){
		cout << vect.at(itr) << " ";
	}
	cout << endl;
}//printVect()

```
...that I would like to move to my "library". So in my .h library file I have:
```

#include <vector>
#include <iostream>

template <class T>
void printVect(vector<T> vect);

```
and my .cpp library file:
```

#include "utilityFunctions.h"

template <class T>
void utilityFunctions<T>::printVect(vector<T> vect){
	for(long itr = 0; itr < (long)vect.size(); itr++){
		cout << vect.at(itr) << " ";
	}
	cout << endl;
}//printVect()

```
But the errors I get are as follows and I can't seem to figure out why... I definitely need to use the template feature, if it isn't possible please let me know. Anyways, here are the errors:
```

 make
g++ -ansi -Wall -g -c utilityFunctions.cpp 
utilityFunctions.h:31: error: variable or field ‘printVect’ declared void
utilityFunctions.h:31: error: template declaration of ‘int printVect’
utilityFunctions.h:31: error: ‘vector’ was not declared in this scope
utilityFunctions.h:31: error: expected primary-expression before ‘>’ token
utilityFunctions.h:31: error: ‘vect’ was not declared in this scope
utilityFunctions.cpp:13: error: expected initializer before ‘<’ token
make: *** [utilityFunctions.o] Error 1

```
Thanks in advance for any help!

---

### Post by nvteighen on 2010-04-10
Because templates need to be known at compile-time. In order to have it working, you'll have to place the template's implementation in your header. So, it's usually a bad idea to have them in .cpp files unless you want it to be private to a module.

---

### Post by StunnerAlpha on 2010-04-10
So you are saying I should only put down "template<class T>" in only the .h files, or are you suggesting I do something else?

---

### Post by CptPicard on 2010-04-10
Essentially, most template stuff ends up completely inside headers, and that includes implementation. This is a side-effect of modern template-style C++ programming -- just look at heavily templated libraries such as boost.

The reason for this is that, as nvteighen said, the actual definition, not just declaration, needs to be known to the compiler so that the compiler can actually compile the actual code that the template needs to become once the template parameters are filled in.

---

### Post by StunnerAlpha on 2010-04-10
Thanks for the reply. I downloaded the boost library and have been looking for those files with the template implementation but can't find a file with that implementation(the boost lib is HUGE!). Could you happen to point me to a specific file for instance? I understand what you are saying about how the compiler needs to know the type before compile time, so then I would need to specify all the types the template could possibly be such as string,float,etc? Thanks for all the help.

---

### Post by CptPicard on 2010-04-10
> **StunnerAlpha said:**
> Could you happen to point me to a specific file for instance?

I don't understand... what specific file? Pretty much all of boost is in the headers and there are no compiled objects to link against, exactly because most of the stuff uses templates a lot, and therefore, everything ends up in headers. (Another reason for this is of course that boost seems to strive to avoid causing binary dependencies)

> 
 I understand what you are saying about how the compiler needs to know the type before compile time, so then I would need to specify all the types the template could possibly be such as string,float,etc?

It's not just about knowing the type, it's about having the code, so that specific instantiations can actually be compiled from scratch when needed. You can, however, precompile certain instantiations of your templates so that you have in your binary object instances Foo<int> and Foo<string> for example, and then you just need to merely declare those in the header. But this kind of defeats the whole point of templates IMO.

3000th post btw. \\:D/ :popcorn:

---

### Post by MadCow108 on 2010-04-10
you can't build a library, as described in the link, containing templates as templates need to be compiled each time their used with a different type.
You have to add the whole implementation into a header file.

in addition to the template problem  you are also missing the std namespace in the header
you need to add a std:: in front of vector, cout and endl

do not place a using namespace std; in the header as this would force the namespace on all users including that header

and the proper type for iterating the vector would be vector<T>::size_type not long

---

### Post by StunnerAlpha on 2010-04-11
I read this: [http://www.cplusplus.com/doc/tutorial/templates/](http://www.cplusplus.com/doc/tutorial/templates/)
and learned that with templates you cant split up interface and implementation like you normally do, thus I moved everything into the .h file and it works just fine. Thanks to everyone who responded.

---

### Post by StunnerAlpha on 2010-04-11
> **MadCow108 said:**
> you can't build a library, as described in the link, containing templates as templates need to be compiled each time their used with a different type.
You have to add the whole implementation into a header file.

in addition to the template problem  you are also missing the std namespace in the header
you need to add a std:: in front of vector, cout and endl

do not place a using namespace std; in the header as this would force the namespace on all users including that header

and the proper type for iterating the vector would be vector<T>::size_type not long

Oh shoot, I didn't even see this post. Thanks for the response man! I will be sure to make those changes.

EDIT: Hmm... I took your advice but am getting errors and am not understanding them. This is what I have:
```

template<class T>
class utilityFunctions{
public:
	static void printVect(std::vector<T> vect){
		for(vector<T>::size_type itr = 0; itr < vect.size(); itr++){ //all errors occur for this line
			cout << vect.at(itr) << " ";
		}
		cout << endl;
	}
};

```
Errors:
```

error: expected ';' before 'itr'
error: 'itr' was not declared in this scope
error: dependent-name '__gnu_debug_def::vector<T>,std::allocator<_CharT> >::size_type' is parsed as a non-type, but instantiation yields a type
error: dependent-name '__gnu_debug_def::vector<T>,std::allocator<_CharT> >::size_type' is parsed as a non-type, but instantiation yields a type

```
Apparently it works fine until I change long to vector<T>::size_type. I have tried putting std:: in front of every 'vector' as well to no avail. Any idea how to rectify this? Thanks.

---

### Post by gusnan on 2010-04-11
You have forgotten a std:: before the first vector on the line with the *for*.

---

### Post by StunnerAlpha on 2010-04-11
> **gusnan said:**
> You have forgotten a std:: before the first vector on the line with the *for*.

```

template<class T>
class utilityFunctions{
public:
	static void printVect(std::vector<T> vect){
		std::cout << "\nBeg printVect" << std::endl;
		for(std::vector<T>::size_type itr = 0; itr < vect.size(); itr++){
			std::cout << vect.at(itr) << "\n";
		}
		std::cout << "End printVect" << std::endl;
	}
};

```
Still gives me the same errors... :/

---

### Post by MadCow108 on 2010-04-11
I'm sorry you also need add a typename
```

for(typename std::vector<T>::size_type itr = 0; itr < vect.size(); itr++){

```
as this is a dependent type

it this is to complicated just use an unsigned integer type, it should be fine in almost all cases

---

### Post by StunnerAlpha on 2010-04-11
> **MadCow108 said:**
> I'm sorry you also need add a typename
```

for(typename std::vector<T>::size_type itr = 0; itr < vect.size(); itr++){

```
as this is a dependent type

it this is to complicated just use an unsigned integer type, it should be fine in almost all cases

Yeah my compiler still didn't seem to like that either so I just ended up making it an unsigned int. Thanks.

---

