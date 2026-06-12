---
title: "Couple of template-related isues in C++."
date: 2007-10-22
forum: Programming Talk
---

### Post by dempl_dempl on 2007-10-22
I've solved the  problem which I'm about to present you , but  I beleive it could be done more elegantly.

```



//Header File
template <class T>
class MyClass
{
  public:
       T doSomething();
}

// Still have to be in Header File
template<class T> T MyClass<T>::doSomething()
{
 /****  do Something ....****//
}



```


I have to put doSomething() definition inside of  Header File or else  Linker will scream.

I would like to be able to put it inside of .CPP file because it's far better solution .

Is there any way to do it   with no  Linker Errors?

---

### Post by Wybiral on 2007-10-22
> **dempl_dempl said:**
> I've solved the  problem which I'm about to present you , but  I beleive it could be done more elegantly.

Are you going to show us some code? :)

---

### Post by dempl_dempl on 2007-10-22
Sorry , it was an error. I accidentaly clicked on a wrong button too soon :)

---

### Post by aks44 on 2007-10-22
Unless your compiler supports the **export** keyword (which I doubt, AFAIK only Comeau supports it, I may be wrong though since I haven't checked g++ about it for a while), you can forget that.

[Read more]("http://www.comeaucomputing.com/techtalk/templates/#export")

---

### Post by duff on 2007-10-22
You can explicitly instantiate any possible use of the template you may have.

```
tempalte class MyClass<int>;
template class MyClass<std::string>;
```

..etc.

---

### Post by dempl_dempl on 2007-10-22
Thanks for help.

I'll check for it right  away ...


BTW,
I've checked GNU's page, they say G++ 's excuse for not having **export** keyword is that others don't have it too . :-D

---

### Post by rgeddes on 2007-10-22
I do believe there is a way to separate the declarations from the definitions:

Header File   - declaration.h
```

#ifndef (macro definition name here) //to protect against multiple declarations
#define (macro definition name here)

// appropriate includes here
template <class T>
class MyClass
{
  public:
       T doSomething();
}
#endif

```

Definition file - definition.cpp
```

// appropriate includes here
#include "declaration.h"
template<class T> T MyClass<T>::doSomething()
{
 /****  do Something ....****//
}
```
main.cpp
```

// appropriate includes here
#include "declaration.h"

void main() {
  //application program here
}

```

Tie these modules together in your make build file to make a myapp executable:
```

myapp: main.o 1.o
   g++ -o myapp 1.o 
main.o: main.cpp definitions.h
   g++ -c main.cpp
1.o: definitions.cpp declarations.h
   g++ -c definitions.cpp

```

I think many examples are shown with both declarations and definitions in the same (header) file.  It makes things easier for demonstration and education, but for project management it's not good... kind of defeats the reason for having a header file... to tell the user of the module, what it does without showing the implementation.

---

### Post by dwhitney67 on 2007-10-23
> **dempl_dempl said:**
> 
I have to put doSomething() definition inside of  Header File or else  Linker will scream.

I would like to be able to put it inside of .CPP file because it's far better solution .

Is there any way to do it   with no  Linker Errors?

Try something like:
```

#ifndef MYCLASS_H
#define MYCLASS_H

template <class T>
class MyClass
{
  public:
    T doSomething();
};

#include "MyClass.cpp"

#endif
```

where MyClass.cpp is something like:
```
#include <iostream>

template< class T >
T MyClass<T>::doSomething()
{
  std::cout << "I'm doing something!" << std::endl;

  T var;
  return var;
}
```

Some folks like to append an "Impl" to the implementation file.  In such a case, MyClass.cpp would be MyClassImpl.cpp.

---

### Post by aks44 on 2007-10-23
> **rgeddes said:**
> I do believe there is a way to separate the declarations from the definitions
[...]
I think many examples are shown with both declarations and definitions in the same (header) file.  It makes things easier for demonstration and education, but for project management it's not good... kind of defeats the reason for having a header file... to tell the user of the module, what it does without showing the implementation.


Templates do not produce any code until they are instanciated. This is because actual template parameters are not known until instanciation. And no code generated means nothing to link against.

To be able to instanciate a template, you need:
1) either to have the definition available
2) or to use the export keyword
No other option.

Of course as duff noted it, there's the good old trick of explicitely forcing instanciation for a particular type (which is a special case of the first option). And do it again and again whenever you need to use the template with other types. But this is hardly maintenable, so in real life you're left with the two options above.

Anyway your suggestion doesn't work. Did you even try it?

---

### Post by rgeddes on 2007-10-24
> **aks44 said:**
> Templates do not produce any code until they are instanciated. This is because actual template parameters are not known until instanciation. And no code generated means nothing to link against.

To be able to instanciate a template, you need:
1) either to have the definition available
2) or to use the export keyword
No other option.

Of course as duff noted it, there's the good old trick of explicitely forcing instanciation for a particular type (which is a special case of the first option). And do it again and again whenever you need to use the template with other types. But this is hardly maintenable, so in real life you're left with the two options above.

Anyway your suggestion doesn't work. Did you even try it?

Apologies...   I 'included' the declaration file in the definition file.. should have 'included' the definition file in the declaration file.. as dwhitney67 pointed out. anyway here's some working code

something.h
```
#ifndef MYCLASS_H
#define MYCLASS_H


namespace my_class {

        template <class T>
        class MyClass
        {
                public:
                        //Default constructor
                        MyClass();

                        //Constructor with initializer
                        MyClass(const T& init_val);

                        //Destructor
                        ~MyClass(){};

                        //Get the value of Tvar
                    T get_Tvar();

                        //Set the value of Tvar
                        void set_Tvar(const T& T_src);

                private:
                        //Private member of Myclass
                        T Tvar;
        };
}

//MyClass function member definitions in separate file
#include "something.cpp"

#endif
```

something.cpp
```
namespace my_class {

        template <class T>
        MyClass<T>::MyClass(const T& init_val) {

                Tvar = init_val;

        }

        template <class T>
        T MyClass<T>::get_Tvar() {

                return Tvar;
        }

        template <class T>
        void MyClass<T>::set_Tvar(const T& T_src) {

                Tvar = T_src;

        }
}

```

main.cpp
```
#include <iostream>
#include "something.h"

using namespace std;
using namespace my_class;

int main(int argc, char* argv[]) {

        MyClass<int> int_var(5);
        cout << "The value of \"int_var\" is: " << int_var.get_Tvar() << endl;
        int_var.set_Tvar(10);
        cout << "The value of \"int_var\" is: " << int_var.get_Tvar() << endl;

        MyClass<char> char_var('a');
        cout << "The value of \"char_var\" is: " << char_var.get_Tvar() << endl;
        char_var.set_Tvar('z');
        cout << "The value of \"char_var\" is: " << char_var.get_Tvar() << endl;


        return 1;
}

```

Makefile
```
myapp: main.o something.o
        g++ -o myapp main.o something.o

main.o: main.cpp something.h
        g++ -c main.cpp

something.o: something.cpp something.h
        g++ -c something.h

```

With all these files in the same directory run
```
make myapp
```

A file called myapp will be created in that directory.  Make myapp executable by executing
```
chmod u+x myapp
```

execute myapp
```
$1> ./myapp
The value of "int_var" is: 5
The value of "int_var" is: 10
The value of "char_var" is: a
The value of "char_var" is: z
```

Note that there is a separation of the declaration and the definition (or implementation).  The declaration file (header file) gives the user of this class, a good idea what the class does without showing the details of how it's implemented...   

I haven't used the export method or the duff method... I'd appreciate it if you could set up examples that show how those two methods work.

Thanks

---

### Post by dwhitney67 on 2007-10-24
> **rgeddes said:**
> 
A file called myapp will be created in that directory.  Make myapp executable by executing
```
chmod u+x myapp
```

Thanks for the credit.  Btw, you should not have to run the 'chmod'.  Your 'myapp' will already have the appropriate permissions set after your build it.

---

### Post by rgeddes on 2007-10-24
> **dwhitney67 said:**
> Thanks for the credit.  Btw, you should not have to run the 'chmod'.  Your 'myapp' will already have the appropriate permissions set after your build it.

Good catch... I started thinking in Bash for a minute there... :)

---

### Post by aks44 on 2007-10-24
> **rgeddes said:**
> I haven't used the export method or the duff method... I'd appreciate it if you could set up examples that show how those two methods work.

I don't have any compiler available that supports the **export** keyword (and I never used it because of that), so I can't guarantee that the following code is correct. But *in theory* it should be.

template.h```

template<class T>
class Foo
{
private:
  T m_val;
public:
  inline Foo() : m_val() {};

  const T& get() const;
  void set(const T&);
};

export template<class T>
  const T& Foo<T>::get() const;

export template<class T>
  void Foo<T>::set(const T&);
```

template.cpp```
#include "template.h"

template<class T>
const T& Foo<T>::get() const
{
  return m_val;
}

template<class T>
void Foo<T>::set(const T& val)
{
  m_val = val;
}
```

main.cpp```
#include <iostream>
#include "template.h"

int main()
{
  Foo<int> foo_int;
  foo_int.set(3);
  std::cout << foo_int.get() << std::endl;

  Foo<std::string> foo_str;
  foo_str.set("hello world");
  std::cout << foo_str.get() << std::endl;

  // you could go on with *any* type you whish

  return 0;
}
```

Compile:```
$ g++ -o test main.cpp template.cpp
$ ./test
3
hello world
```




Now concerning duff's suggestion (ie. forcing instanciation), here it is:

template.h```
template<class T>
class Foo
{
private:
  T m_val;
public:
  inline Foo() : m_val() {};

  const T& get() const;
  void set(const T&);
};
```

template.cpp```
#include "template.h"

template<class T>
const T& Foo<T>::get() const
{
  return m_val;
}

template<class T>
void Foo<T>::set(const T& val)
{
  m_val = val;
}
```

template_int.cpp```
#include "template.cpp"

template class Foo<int>;
```

main.cpp```
#include <iostream>
#include "template.h"

int main()
{
  Foo<int> foo_int;

  // ok, it can be linked,
  // Foo<int> has been explicitely instanciated in template_int.cpp
  foo_int.set(3);
  std::cout << foo_int.get() << std::endl;

  Foo<std::string> foo_str; // ok as the constructor is "seen" (it is inline)
  // foo_str.set("hello world"); // would produce a linker error
  // std::cout << foo_str.get() << std::endl; // same

  // you CAN'T go on with *any* type you whish, you are restricted
  // to the types you explicitely instanciated
  // or you need to include the definition from template.cpp

  return 0;
}
```

Compile:```
$ g++ -o test main.cpp template_int.cpp
$ ./test
3
```

---

### Post by rgeddes on 2007-10-24
> **aks44 said:**
> I don't have any compiler available that supports the **export** keyword (and I never used it because of that), so I can't guarantee that the following code is correct. But *in theory* it should be.


Thanks for the examples.. the export method didn't work for me..
```
$0> g++ -o test main.cpp template.cpp 
template.h:13: warning: keyword ‘export’ not implemented, and will be ignored
template.h:14: error: declaration of ‘const T& Foo<T>::get() const’ outside of class is not definition
template.h:16: warning: keyword ‘export’ not implemented, and will be ignored
template.h:17: error: declaration of ‘void Foo<T>::set(const T&)’ outside of class is not definition
template.h:13: warning: keyword ‘export’ not implemented, and will be ignored
template.h:14: error: declaration of ‘const T& Foo<T>::get() const’ outside of class is not definition
template.h:16: warning: keyword ‘export’ not implemented, and will be ignored
template.h:17: error: declaration of ‘void Foo<T>::set(const T&)’ outside of class is not definition
```

my compiler:
```
$1> g++ --version
g++ (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
```

are you using a compiler that has implemented the 'export' keyword?

The method mentioned by duff did work... it looks like when you want to instantiate objects of different types, T, you need to have an associated 'template_T.cpp' file for each type.  Little bit of work there if you need the template class to accommodate various types.

Comeau's Resource page you mentioned earlier is quite good:KS... answered some questions I forget I had...

Thanks

---

### Post by aks44 on 2007-10-24
> **rgeddes said:**
> the export method didn't work for me..
[...]
are you using a compiler that has implemented the 'export' keyword?

As I said, I *don't* have a compiler that supports "export". In fact, AFAIK the only one that supports it is Comeau. I know I should get it...

So the above code that uses "export" is only theoric, it *should* work on Comeau but unfortunately I couldn't test it, as no other compiler than Comeau supports it.


> **rgeddes said:**
> The method mentioned by duff did work... it looks like when you want to instantiate objects of different types, T, you need to have an associated 'template_T.cpp' file for each type.  Little bit of work there if you need the template class to accommodate various types.

FWIW I brought up the pattern template_T.cpp only as an example, you may as well instanciate all your needed types in a single .cpp file.
But anyway the fact is: you need to *explicitely* instanciate the template for each and every type you're planning to use. Which is too much of a burden as far as I'm concerned, that's why I prefer the old school method of putting the definitions in the .h file.


> **rgeddes said:**
> Comeau's Resource page you mentioned earlier is quite good

Indeed, Comeau is simply the best C++ compiler out there. In fact, it's the *only* one (that I'm aware of) that is 100% standard-compliant.
Those guys are way more than competent. ;)
As long as I was running Windows I didn't really bother buying it, but now that I'm running Linux (and intend to stay with it) I guess that it would be well worth the $50.

---

### Post by dempl_dempl on 2007-10-24
Indeed, Comeau is simply the best C++ compiler out there. In fact, it's the *only* one (that I'm aware of) that is 100% standard-compliant.
Those guys are way more than competent.
As long as I was running Windows I didn't really bother buying it, but now that I'm running Linux (and intend to stay with it) I guess that it would be well worth the $50.


Well, luckily, I don't even have to bother to spend 50$ . I ask my employer to do so :) .

It goes as any other expence.

---

### Post by dempl_dempl on 2007-10-24
> Indeed, Comeau is simply the best C++ compiler out there. In fact, it's the *only* one (that I'm aware of) that is 100% standard-compliant.
Those guys are way more than competent.
As long as I was running Windows I didn't really bother buying it, but now that I'm running Linux (and intend to stay with it) I guess that it would be well worth the $50.


Well, luckily, I don't even have to bother  spending 50$ . I ask my employer to do so :) .

It goes as any other expence.

---

### Post by dumbsnake on 2007-10-24
> **dwhitney67 said:**
> Some folks like to append an "Impl" to the implementation file.  In such a case, MyClass.cpp would be MyClassImpl.cpp.

If you include a .cpp file then you better not also compile it or even include it multiple times because you will get linker errors.  Unless you are using it as a header file: no actual definitions.  I'd say if you would like to seperate it like this, make the extension something other than .cpp like either .h or .cpt for C++ template.

---

### Post by rgeddes on 2007-10-25
> **dumbsnake said:**
> If you include a .cpp file then you better not also compile it or even include it multiple times because you will get linker errors.  Unless you are using it as a header file: no actual definitions.  I'd say if you would like to seperate it like this, make the extension something other than .cpp like either .h or .cpt for C++ template.

As I understand it, the '#include' macro directive just substitutes the contents of the referenced file for the directive during compilation... so, the name of the include file isn't an issue...  I think the .h extension or no extension is more a convention

Stroustrup talks about the ODR (One Definition Rule), whereby there "must be a unique definition of a class, template, etc." *and* "two definitions of a class, template, or inline function are accepted" as referring to the same unique definition as long as 1) they are exactly the same, 2) they are in different translation units, and 3) their meanings are exactly the same...

This means that you can compile 2 component files of one program with the same header file included in both., and each header has it's associated definition.  

Also, I think the macro construct:

#ifndef <name>
#define <name>

// definitions

#endif

is used to protect against multiple definitions in the same translation unit.

This topic gets a little messy for me because it's not C++ and it sneaks up on me every now and then when I forget about it.

---

### Post by dwhitney67 on 2007-10-26
> **dumbsnake said:**
> If you include a .cpp file then you better not also compile it or even include it multiple times because you will get linker errors.  Unless you are using it as a header file: no actual definitions.  I'd say if you would like to seperate it like this, make the extension something other than .cpp like either .h or .cpt for C++ template.

Rgeddes, I believe what 'dumbsnake' was stating was that one should take care not to explicitly compile the template implementation file, which based on my earlier example, could possibly be done by one who is naive.

His suggestion is to define the implementation file with an extension other than .cpp so that it stands out that is is not a module that should be directly compiled.  Thus, in a simple project, one could have a template.h (or .hpp), a template.cpt, and a main.cpp.  When it is time to compile, something like this would suffice:

$ g++ main.cpp

If one were to name the template.cpt with a name of template.cpp, then one might be tempted to build using this command (which is incorrect):

$ g++ main.cpp template.cpp

Of course, the situation above is unlikely to occur if one relies on Makefiles, of which I normally do unless I am building a test program for this forum.  :-)

Anyhow, any file extension will do.  One however needs to remain consistent with their convention.  I for one will stick with the '.cpp' format for all C++ implementation files, just like I will remain with the .h extension for header files.  There is no standard that states that C++ header files must have the .hpp extension; that is an arbitrary choice.  If one wants, they could use the .foo extension for header files.

P.S.  A file extension of .cpp is required to compile C++ implementation files.

---

