---
title: "const in template methods c++"
date: 2008-08-23
forum: Programming Talk
---

### Post by monkeyking on 2008-08-23
Hi, I'm just getting into template's in c++.

I found a working example on parashift c++ faq lite [http://www.parashift.com/c++-faq-lite/templates.html#faq-35.2](http://www.parashift.com/c++-faq-lite/templates.html#faq-35.2)

```

 // This would go into a header file such as "Array.h"
 class Array {
 public:
   Array(int len=10)                  : len_(len), data_(new int[len]) { }
  ~Array()                            { delete[] data_; }
   int len() const                    { return len_;     }
   const int& operator[](int i) const { return data_[check(i)]; }  &#8592; subscript operators often come in pairs
         int& operator[](int i)       { return data_[check(i)]; }  &#8592; subscript operators often come in pairs
   Array(const Array&);
   Array& operator= (const Array&);
 private:
   int  len_;
   int* data_;
   int  check(int i) const
     { if (i < 0 || i >= len_) throw BoundsViol("Array", i, len_);
       return i; }
 };

```

There are some issues i don't understand why is len() a cons function, instead of just making len_ public. And the last line before the private: line. What is this?

Futher more if I want to make a generic print funktion.
I would add the follwing the the class def.
```

void print(int stop=0);

```

But would I need to do seperate funktion for each datatype I'll be using like int, float,.

like

```

void Array<int>::print(int stop){...}
void Array<float>::print(int stop){...}

```

thanks in advance

---

### Post by dribeas on 2008-08-23
Uhm... your sample code just doesn't look like templated... For the first questions I will assume the non-templated version.

> **monkeyking said:**
> 
There are some issues i don't understand why is len() a cons function, instead of just making len_ public.
And the last line before the private: line. What is this?

```

void print(int stop=0);

```

But would I need to do seperate funktion for each datatype I'll be using like int, float,.


First, you don't want to make len_ field public, else user code would be able to modify it without your class knowledge. This could end with a len_ field greater than the memory held and thus a segmentation fault. That is what encapsulation is about. Now, the accessor method is marked constant as it does not perform any changing operation on the array, and can thus be called through a constant reference. Always mark all non-mutating fields as constant.

The last line before the private keyword:
```

   Array& operator= (const Array&);

```
is the definition of the assignment operator. It will be implemented with whatever logic is required to copy one array into another, probably something in this line [*]:
```

Array& Array::operator=(  Array const & other )
{
   if ( data_ != 0 ) delete[] data_; // Free internal buffer
   data_ = new int[ other.len_ ]; // Request same memory as other
   len_ = other.len_;
   for ( int i = 0; i < len_; ++i )
   {
      data_[ i ] = other.data_[ i ];
   }
   return *this;
}

```

Note that the default copy constructor will not work. Default assignment operator does fieldwise assignment, (len_ = other.len_; data_ = other.data_) which would have both arrays pointing to the same memory.

Now for the last part (and templated version). As long as the code is generic for all data types you won't need to implement all, that is the idea of templates:
```

template <typename T>
class Array
{
   ...
public:
   void print(std::ostream & o, int stop=0) const; // const as it does not change the data
private:
   T* data_; // Data is a template to whichever T is
   int length_;
};

template <typename T>
void Array<T>::print( std::ostream & o, int stop = 0) const
{
   if ( stop == 0 ) stop = len_; // If 0 print all array
   check( stop ); // Validate range, throws if stop out of range

   o << "Array size: " << len_ << "\nPrinting " << stop << " elements:";
   for ( int i = 0; i < stop; ++i )
   {
      o << " " << data_[ i ];
   }
}

```

That will work for all data types T such that the operator<<(ostream&,T const &) is defined.

   David


[*] Note that to simplify the logic in the code this implementation is not exception safe. Simplest exception safe implementation would be:

```

Array& Array::operator=( Array const & other )
{
   Array tmp( other ); // Copy constructor defined above - similar to initial operator= implementation
   // None of the operations below raise exceptions:
   std::swap( tmp.len_, len_ );
   std::swap( tmp.data_, data_ );
}

```

The advantage of this code is that if an exception is raised during processing (inside copy constructor) then the original array is not changed. That is: either the operation completes successfully or else the array is unchanged. When the array is just of ints, this may not seem so important, but once you turn it into generic code you don't know what exceptions can be thrown by the yet-unknown class.

---

### Post by Dancingwllamas on 2008-08-23
> There are some issues i don't understand why is len() a cons function, instead of just making len_ public.

"const" being after the function signature indicates that the function cannot change any non-static member variables in the class. This is meant for debugging purposes mostly (to ensure you don't do things you shouldn't).

len_ is not public because of the ideas behind object oriented programming. Variables are generally made private and only accessible behind getters and setters to prevent undefined behavior. In this case, look what might happen if len_ were public (I haven't tested this code, but it gives the general idea):

```

Array array<int>;
array.len_ = 55; //We don't want this to be able to happen
cout << array[40] //This does not throw a BoundsViol exception, but seg faults instead
```

As for the second question. that is overloading the assignment operator. A better explanation than I can give can probably be found by Googling "overloading assignment operator c++".

As for your third question, the idea behind templates is that you shouldn't need to create separate functions for each potential data type. As long as each type you are trying to print has overloaded the "<<" operator that feeds to an ostream it should print fine.

---

### Post by dribeas on 2008-08-23
> **Dancingwllamas said:**
> "const" being after the function signature indicates that the function cannot change any non-static member variables in the class. This is meant for debugging purposes mostly (to ensure you don't do things you shouldn't).

Const is not done for debugging purposes, it explicits what can and cannot be done with the object. As an example, if you decide to override the << operator:
```

std::ostream& operator<<( std::ostream& o, Array const & a )
{
   o << "array of " << a.len() << " elements:";
   for ( int i = 0; i < a.len(); ++i )
   {
      o << " " << a[ i ];
   }
   return o;
}

```

Now, as the array is passed as a constant reference it can only call constant methods: len() is constant and there is a constant variant of operator[]. If you don't mark len() as constant then the compiler will flag the above code as an error (trying to modify a constant object)

   David

---

