---
title: "dynamic array encapsulation problem, C++"
date: 2007-12-10
forum: Programming Talk
---

### Post by carl.alv on 2007-12-10
Hi all!

I am not very knowledgeable in C++ and I'm trying to encapsulate a 2D dynamic array (called Parray) which stores objects of a certain class Base. This is my Parray class header:

```
class Parray {
 private:
    int _size;
    int _type;
    Base** _data;

 public:
    Parray(int, int);
    class BadSize {};
    class BadType {};
    ~Parray();

    Base* operator[](int);
    class BoundsViolation {};
};
```

the .cc file with the definitions:

```
#include "Tobvir.h"
#include "Parray.h"

inline Parray::Parray(int size, int type) : _size(size), _type(type){
    if(size == 0)
	throw BadSize();
    _data = new Base*[size];
    switch(_type){
	case 1:
	    for(int i = 0; i < _size; i++)
		_data[i] = new Derived1;
	case 2:
	    for(int i = 0; i < _size; i++)
		_data[i] = new Derived2;
	default:
	    throw BadType();
    }
}

inline Parray::~Parray(){
    for(int i = 0; i < _size; i++)
	delete _data[i];
    delete[] _data;
}

inline Base* Parray::operator[](int pos){
    if(pos >= _size)
	throw BoundsViolation();
    return _data[pos];
}

```

where Tobvir.h defines the Base and Derived classes. Finally the main is

```
#include "Tobvir.h"
#include "Parray.h"

int main(){
   int type = 1;
   int N = 10;
    
   Parray b(N, type);

   return 0;
}
```

When I comment the line with the Parray declaration in main() the compiler does not complain, but when I attempt to declare it it says:

```
TobMain.cc:(.text+0x28): undefined reference to `Parray::Parray(int, int)'
TobMain.cc:(.text+0x34): undefined reference to `Parray::~Parray()'
TobMain.cc:(.text+0x46): undefined reference to `Parray::~Parray()'
```

and since I included the header I don't know what is the problem.

Thanks in advance for any help :)

---

### Post by llonesmiz on 2007-12-10
You need to use g++ this way:

g++ -o program_name TobMain.cc Parray.cc

or maybe create a library with Parray and then link your program to that library.

---

### Post by carl.alv on 2007-12-10
Yes, the files are compiled and linked (properly I think, because I have used this kind of makefiles for a log time). That is why I don't understand the problem.

---

### Post by geirha on 2007-12-10
I don't think you can use the inline keyword on constructors and destructors.

---

### Post by carl.alv on 2007-12-10
> **geirha said:**
> I don't think you can use the inline keyword on constructors and destructors.

Yup, it seems that was the problem, now it compiles, thanks :)

---

### Post by iharrold on 2007-12-10
You should use the std::vector<Base> and let it handle the dynamic creation/deletion.  The overhead is only O(n)+. Just slightly higher due to a constant overhead.

You can also predimention it for increased time savings via

```

const unsigned int START_SIZE = 100;
std::vector<Base> _data (START_SIZE,BASE_DEFAULT) ;

```

The compiler will dimention _data to have to be 100 "array" of Base.  And BASE_DEFAULT is an arbitrary value you assign as the default of base.  Thus you would have an array of size 100 filled with BASE_DEFAULT.  Anything larger than 100 will automatically be dimentioned.  Though you should still always have a "try ... catch" around all vector operations incase it throws  unable to allocate memory.

Edit, looking back I see you have a 2D array and I only showed a 1D.  So you will need to tweak as necessary.

---

### Post by Majorix on 2007-12-10
Don't declare functions as inline explicitly. The compiler will (hopefully) handle it on itself. If you had followed this simple rule you wouldn't have run into any problems :)

---

### Post by aks44 on 2007-12-10
You can't declare a function inline in the cpp file, because if you do this the implementation is not visible to other units using that class (also, contrary to what has been said previously, you CAN declare constructors & destructors inline).

As a rule of thumb, inline functions must be defined next to (or inside) the class declaration (ie. *_in the header file_*) so that they are visible to other units.


Also, I have to strongly agree with iharrold. Unless this is a specific assignment (for school?) you should not reinvent the wheel, better use std::vector.
FWIW the code you showed is not exception-safe, if anything throws during the construction you'll end up with memory leaks. Using std::vector would solve that.

---

