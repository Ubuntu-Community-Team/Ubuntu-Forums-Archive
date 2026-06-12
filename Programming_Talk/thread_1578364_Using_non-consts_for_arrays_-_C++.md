---
title: "Using non-consts for arrays - C++?"
date: 2010-09-20
forum: Programming Talk
---

### Post by fallenshadow on 2010-09-20
Does anyone know if this is possible? It would be neat if I could do this.

I want to use a variable for an array but it wont let me.

---

### Post by Zugzwang on 2010-09-20
It looks like this is easily possible:

[PHP]
#include <iostream>

int main(int argc, char **args) {
    int a;
    std::cout << "How many elements? " << std::endl;
    std::cin >> a;
    int b[a];
    std::cout << "Ok, we're done!" << std::endl;
}
[/PHP]

This code compiles & links very well on my computer using "g++ -o test test.cpp". Try typing in a large constant at runtime and observe the segmentation fault when there's not enough memory available on the stack(?).

---

### Post by MadCow108 on 2010-09-20
do you mean C and not C++?

C89 does not allow variable sized arrays.
but gnu89 and C99 (and of course gnu99) do.

compile with:
gcc -std=gnu99

c++ (=c++98) also allows it.

---

### Post by dwhitney67 on 2010-09-20
In C++, such declarations are in violation of ISO C++ standards.  Use the -pedantic g++ option to see this.

This is probably better than using a wimpy array:
```

#include <vector>
#include <iostream>

int main(int argc, char **args) {
    int a;
    std::cout << "How many elements? " << std::endl;
    std::cin >> a;
    std::vector<int> b(a);
    std::cout << "Ok, we're done!" << std::endl;
}  

```

---

### Post by dribeas on 2010-09-20
In C++ you cannot create an array whose size is not a compile time constant (not only constant, but compile time constant), and that is by design. The problem is that the size of the array is part of the type signature, and it must be known at compile time.

On the other hand, there may be different solutions, depending on what you really need. The simplest would be using a std::vector. It will allocate memory dynamically in the heap, but you will not have to manage the memory. 

If the problem is that you really need the elements to be allocated in the stack, you will need to deviate from the standard. Some compilers (including g++) may have support for arrays with dynamic size --mainly if they implement C99 that is a requirement, and they can offer the same functionality as a c++ extension. On other platforms (Visual Studio is known not to support C99), you can use alloca that will behave similarly to malloc, but allocating the elements in the stack.

At any rate, my advice would be using standard containers (in particular std::vector) first, and only if there is a very strong requirement that cannot be fulfilled with the container think on other solutions.

---

### Post by worksofcraft on 2010-09-21
IMO arrays with run time defined dimensions on the stack are an abomination.

Try to picture what happens when you have two or more such arrays:
The first one might well have a compile time known address, but the second one will be placed depending on the size of the first.
Also it affects all the offsets for subsequent function call parameters. The compiler will probably use indirection via unidentified pointers, but you be really better off using your own explicit pointers IMO. This is not something I would want my C/C++ compiler doing for me.

---

### Post by dwhitney67 on 2010-09-21
> **worksofcraft said:**
> IMO arrays with run time defined dimensions on the stack are an abomination.

Try to picture what happens when you have two or more such arrays:
The first one might well have a compile time known address, but the second one will be placed depending on the size of the first.
Also it affects all the offsets for subsequent function call parameters. The compiler will probably use indirection via unidentified pointers, but you be really better off using your own explicit pointers IMO. This is not something I would want my C/C++ compiler doing for me.

As a programmer, one obviously needs to know when it is wise to declare an array on stack, or when to allocate it on the heap.  In certain systems, the stack size may be limited.

Except perhaps in cases where one is developing for an embedded system, the offsets in memory of where these objects are placed should be irrelevant.  One addresses the array's contents using a "handle" to the first position of the array, along with some offset (which may or may not be zero).

P.S.  I agree about the "abomination" statement.  Perhaps those who wrote the ISO C++ standards think so too.

---

### Post by nvteighen on 2010-09-21
> **worksofcraft said:**
> IMO arrays with run time defined dimensions on the stack are an abomination.

Try to picture what happens when you have two or more such arrays:
The first one might well have a compile time known address, but the second one will be placed depending on the size of the first.
Also it affects all the offsets for subsequent function call parameters. The compiler will probably use indirection via unidentified pointers, but you be really better off using your own explicit pointers IMO. This is not something I would want my C/C++ compiler doing for me.

Well... the ASM gcc and g++ generate for supporting this feature is so dense and convoluted that I don't know how they do it...

I think the abomination is trying to ask a language to do something it shouldn't do. Variable stack arrays aren't bad per se... Forth does them... The thing is that C and C++ aren't dynamic languages and therefore adding a feature like this breaks the language's logic for almost no benefit: 1) if C's malloc doesn't work for you, you're probably using the bad language for your job. 2) C++'s got std::vector for this, much nicer, it's standard and also has other features that you don't get from the "int a[b];" thing... e.g. iteration... And again, if C++'s std::vector doesn't serve you either, you probably need another language.

---

### Post by fallenshadow on 2010-09-21
With all the different responses this is getting quite confusing. I think the overall picture I get is that this can't and should not be done with a standard compiler.

So, I should be using vectors then?

---

### Post by dwhitney67 on 2010-09-21
> **fallenshadow said:**
> With all the different responses this is getting quite confusing. I think the overall picture I get is that this can't and should be done with a standard compiler.

So, I should be using vectors then?

With C++, you have two choices: use an STL vector, or manage an array on the heap.

```

#include <vector>

int main()
{
   std::vector<int> array(10);   // declares an candy-coated array of 10 int elements

   ...
}

```
```

int main()
{
   int* array = new int[10];   // declares an int array on the heap

   ...

   delete [] array;
}

```
As for the value "10" above, it was arbitrarily chosen.  You could use a variable N if you wish.

Read more about the STL vector [here]("http://www.cplusplus.com/reference/stl/vector/").

---

### Post by fallenshadow on 2010-09-23
Could you show me a better example?... something like what ive done below. Although what ive done won't compile. 

If there is some rather embarrassing mistakes in the code then im sorry. I never really learn't how to use arrays! :oops:

```

#include <iostream>

int number,n;

int main()
{
   int* array = new int[number];   // declares an int array on the heap

	for(n=0; n>0; n++;)
	{
	cout<<"Enter a number"<<endl;
	cin>>number[n];
	}
	
   delete [number] array;
   
   return 0;
}

```

---

### Post by dwhitney67 on 2010-09-23
An array can be viewed in a similar fashion as a sequential group of mailboxes at your local post office.  As with each element of an array, each mailbox has a unique address (ie number).

The code you presented does contain bugs/syntax errors.  For starters, you have not initialize the variable 'n'.  There is also no need for it, or the variable 'n' to be declared globally within the module.

When deleting an array, the number of elements in the array is not used in the "delete [] array" statement.

Here's the code, albeit corrected...
```

#include <iostream>

int main()
{
   size_t number = 5;
   int*   array  = new int[number];   // do not write obvious comments!

   for (size_t n = 0; n < number; ++n)
   {
      std::cout << "Enter a number: ";
      std::cin  >> array[n];
   }
	
   delete [] array;
   
   return 0;
}

```

---

### Post by pbrane on 2010-09-23
dwhitney67 beat me to it. also you should compile your code with **-Wall** option, that will help you to see errors and warnings you need to fix.

---

### Post by fallenshadow on 2010-09-23
Thanks guys... I understand how this works now! Very, very happy!

I went ahead and did a more complete example for myself to see does it work as intended. Indeed it does!! :guitar:

```

#include <iostream>

using namespace std;

int num1,num2;

int main()
{
   size_t answer = 0;
   int*   array  = new int[answer];   
	
	cout<<"Enter num1"<<endl;
	cin>>num1;
	
	cout<<"Enter num2"<<endl;
	cin>>num2;
	
	answer=num1+num2;

   for (size_t n = 0; n < answer; ++n)
   {
      cout << "Enter a number: ";
      cin  >> array[n];
   }
	
   delete [] array;
   
   return 0;
}

```

---

### Post by dwhitney67 on 2010-09-23
> **fallenshadow said:**
> Thanks guys... I understand how this works now! Very, very happy!

I went ahead and did a more complete example for myself to see does it work as intended. Indeed it does!! :guitar:

There's not a snowball's chance in a "hot place" that the code works.

You allocated an array of size 0.

---

### Post by fallenshadow on 2010-09-24
Well im afraid it does work. Try putting this after the for loop and see for yourself! :)

```

                cout << "OUTPUT"<<endl;
		cout << array[0]<<endl;
		cout << array[1]<<endl;
		cout << array[2]<<endl;
		cout << array[3]<<endl;

```

---

### Post by dwhitney67 on 2010-09-24
> **fallenshadow said:**
> Well im afraid it does work. Try putting this after the for loop and see for yourself! :)

```

                cout << "OUTPUT"<<endl;
		cout << array[0]<<endl;
		cout << array[1]<<endl;
		cout << array[2]<<endl;
		cout << array[3]<<endl;

```

Pure coincidence!

You have a bug in your code... you did not allocate any space for the array!  Why can't you accept this clear and simple fact?
```

...
   size_t answer = 0;
   int*   array  = new int[answer];
...

```

P.S.  Compile your program with the -g option, and then run it using 'valgrind -v'.

---

### Post by GeneralZod on 2010-09-24
> **dwhitney67 said:**
> Pure coincidence!


Yep - in fact, it crashes on exit, for me.

---

### Post by fallenshadow on 2010-09-24
Setting the array size has no effect on the code.

For example if I set the array size to 3 but the variable is for 4... 4 items will be entered into the array and it outputs those 4 items.

Surely it should only allow 3 items if the array size is set to 3.

---

### Post by dwhitney67 on 2010-09-24
> **fallenshadow said:**
> 
Surely it should only allow 3 items if the array size is set to 3.

It doesn't work that way in C++ (nor C).  If you want an error when attempting to address an array location that is out of bounds, then use a "smart" array such as the STL vector.

---

### Post by fallenshadow on 2010-09-24
If I don't know how many things I want to store in an array then what size should I set it at? :confused:

---

### Post by spjackson on 2010-09-24
> **fallenshadow said:**
> If I don't know how many things I want to store in an array then what size should I set it at? :confused:
If you don't know how many to store than maybe an array is not the right choice. Perhaps a linked list would be better, or some other data structure depending on what you need to do. However, if you need fast random access and absolutely need an array, then you need to allocate a reasonable number - you need to determine what is reasonable. If you find out later that you need more, you either fail elegantly or call realloc() (man realloc).

Better still, as has been pointed out several times already, use a std:vector<>. This automatically takes care of re-allocation.

---

### Post by fallenshadow on 2010-09-24
Yeah I think I will just figure out that "magic" number that works for me.

I am mean't to use arrays for college so I don't think vectors would be acceptable. Many thanks to all that helped me figure this out!

Apologies to anyone I annoyed with my incompetence at arrays! :)

---

### Post by dwhitney67 on 2010-09-24
Impress your instructor and fellow students by using your own array:
```

#include <stdexcept>

template <typename T>
class Array
{
public:
   Array(size_t initSize = 0)
      : myData(initSize > 0 ? new T[initSize] : 0),
        mySize(initSize)
   {
   }

   ~Array()
   {
      delete [] myData;
      mySize = 0;
   }

   void resize(size_t newSize)
   {
      T* tmp = new T[newSize];

      for (size_t i = 0; i < newSize && i < mySize; ++i)
      {
         tmp[i] = myData[i];
      }

      delete [] myData;

      myData = tmp;
      mySize = newSize;
   }

   T& operator[](const size_t index) const
   {
      if (index >= mySize)
      {
         throw std::range_error("Array index out of range.");
      }

      return myData[index];
   }

   inline size_t size() const { return mySize; }

private:
   T*     myData;
   size_t mySize;
};


#include <iostream>

int main()
{
   Array<int> array(2);

   try
   {
      array[0] = 10;
      array[1] = 20;

      std::cout << "array[0] = " << array[0] << std::endl;
      std::cout << "array[1] = " << array[1] << std::endl;
      std::cout << "array[2] = " << array[2] << std::endl;
   }
   catch (std::exception& e)
   {
      std::cerr << e.what() << std::endl;
   }

   std::cout << "resizing array to have 4 elements..." << std::endl;
   array.resize(4);

   try
   {
      array[2] = 30;
      array[3] = 40;

      for (size_t i = 0; i < array.size(); ++i)
      {
         std::cout << "array[" << i << "] = " << array[i] << std::endl;
      }
   }
   catch (std::exception& e)
   {
      std::cerr << e.what() << std::endl;
   }
}

```

P.S.  Feel free to augment the Array class above to meet your needs.  Methods that are missing include:  a copy constructor, an assignment operator, a method to return a pointer to the beginning of the underlying data array, and perhaps another method to return a pointer to the end of the data.   The latter two will be able to be used in other nifty functions that iterate over the data.

---

### Post by fallenshadow on 2010-09-25
Alright, thanks again dwhitney!! Gosh some people here are waaaay too helpful! :)

---

