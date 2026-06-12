---
title: "memory leak with operator overloading c++"
date: 2008-09-09
forum: Programming Talk
---

### Post by monkeyking on 2008-09-09
I'm having problems tracking down a memory leak when I'm using operator overloarding. I'm overloading + and =.
This is the code that calls my arrayclass.
[PHP]
Array<int> ary(10);
Array<int> ary1(10);
Array<int> ary2 = ary + ary1;
[/PHP]
The problem lies in the last line.

This is the array class
[PHP]
template<typename T>
class Array {
 public:
  Array() {data_=NULL;x_=0;}
  Array(int length):x_(length),data_(new T[length]){}
  Array(const Array<T>& var);
  ~Array(){delete [] data_;}
  int length() const                  { return x_;     }
  T& operator() (uint r); 
  T operator() (uint r) const; 
  Array<T>& operator= (const Array<T>&);
  Array<T>& operator+ (const Array<T>&);
private:
  int x_;
  T*  data_;
};
[/PHP]
And this is the implementation of some of the methods
[PHP]
template<typename T>
Array<T>::Array(const Array<T>& var){
  x_ = var.length();
  data_ = new T[x_];
  for(int i=0;i<var.length();i++)
    data_[i]=var.data_[i];
}
template<class T>
Array<T>&  Array<T>::operator=( Array const & other ){
  if (this == &other)//if var = var return var
    return *this;
  if( x_!=other.length()){ // if they don't have the same dim;
    puts("length is different");
    delete [] data_; //delete old array
    x_ = other.length();
    data_ = new T[x_];
    
  }// now copy into the matrix
  for (int i=0;i<x_;i++)
    data_[i]=other.data_[i];
  return *this;
}
template<class T>
Array<T>&  Array<T>::operator+( Array const & other ){
  #if 1
  if (x_ != other.length())
    puts("Length of vectors aren't equal");
  #endif
  Array<T> *tmp = new Array<T>(other.length());
  for(int i=0;i<x_;i++) 
    tmp->data_[i] = data_[i] + other(i);
  return *tmp;
}
[/PHP]

thanks in advance

---

### Post by dwhitney67 on 2008-09-09
> **monkeyking said:**
> [php]...
template<class T>
Array<T>&  Array<T>::operator+( Array const & other ){
  #if 1
  if (x_ != other.length())
    puts("Length of vectors aren't equal");
  #endif
  Array<T> *tmp = new Array<T>(other.length());
  for(int i=0;i<x_;i++) 
    tmp->data_[i] = data_[i] + other(i);
  return *tmp;
}
[/PHP]

thanks in advance

Your memory leak is right there, in the operator+() method.  You allocate memory for an Array<T>; I think you really want to allocate memory for the data_ buffer.

P.S.  When in methods like the one above, it is not necessary to call methods on the 'other' object.  Just access the private data directly to save the overhead of making function calls.

P.S.S.  Also, is the adding of the array values in data_ what you really want for the operator+() method, or is a concatenation of the data what is desired?  Beware that the length of 'this' may be greater than 'other', thus causing you to breach the limits of the data_ array held by 'other'.

---

### Post by dribeas on 2008-09-10
[PHP]
template<class T>
Array<T>&  Array<T>::operator+( Array const & other ){
  #if 1
  if (x_ != other.length())
    puts("Length of vectors aren't equal");
  #endif
  Array<T> tmp(other.length());
  for(int i=0;i<x_;i++) 
    tmp.data_[i] = data_[i] + other(i);
  return tmp;
}
[/PHP]

The problem is that you are allocating memory for Array<T> tmp inside operator+ that never gets destroyed. Change into the code above.

Now two small non-issues, just for completeness:
```

Array<int> ary(10);
Array<int> ary1(10);
Array<int> ary2 = ary + ary1;

```

In this code last line is calling operator+ and copy constructor. Operator = does not get called. Even if it looks like assignment it is construction as it is in the same line ary2 was defined.

In general, all operators that can be overloaded as free functions should. The reason comes around symmetry, if the operator is defined as a method the compiler is not allowed to use the same type matching on both sides of the +, but if it is a free function then both values are treated in exactly the same way. Also note that your version is not constant, so that you cannot add two constant Arrays when there is no reason for it.

---

### Post by dwhitney67 on 2008-09-10
> **dribeas said:**
> [PHP]
template<class T>
Array<T>&  Array<T>::operator+( Array const & other ){
  #if 1
  if (x_ != other.length())
    puts("Length of vectors aren't equal");
  #endif
  Array<T> tmp(other.length());
  for(int i=0;i<x_;i++) 
    tmp.data_[i] = data_[i] + other(i);
  return tmp;
}
[/PHP]

Are you sure this is completely correct?  

You are returning the reference to a local object (tmp) that is created on the stack.  I think you meant to return a copied object, or perhaps the de-reference of 'this'.

Second, the index of the for-loop may index into an area not allocated to 'other'.  The if-block section with the puts() should perhaps throw an exception.

Anyhow, the OP needs to clarify what his/her requirements are for the operator+() method before we can deduce what operation the method needs to perform.

---

### Post by dribeas on 2008-09-10
> **dwhitney67 said:**
> Are you sure this is completely correct?  

You are returning the reference to a local object (tmp) that is created on the stack.  I think you meant to return a copied object, or perhaps the de-reference of 'this'.

You are right! I did not check the signature and assumed that it was operator + (a+b) from the post's code. The signature for that operator must be:

```

template <typename T>
Array<T> Array<T>::operator+( Array<T> const & ) const; // a + b
// or
template <typename T>
Array<T> operator+( Array<T> const &, Array<T> const & ); // another way of a+b

// different from
template <typename T>
Array<T>& operator+( Array<T> const & ); // a += b

```

Without the references. The operator as was defined above was the compound += operator.

Thanks for the correction.

---

### Post by monkeyking on 2008-09-10
Thanks It makes perfect sense now.
Strange I couldn't figure this on out.

I do have one more question.

> 
In general, all operators that can be overloaded as free functions should. The reason comes around symmetry, if the operator is defined as a method the compiler is not allowed to use the same type matching on both sides of the +, but if it is a free function then both values are treated in exactly the same way. Also note that your version is not constant, so that you cannot add two constant Arrays when there is no reason for it.

Free function is a function not related to any class right?
So it's the best to use this kind of signature?
```

myClass operator+ (const myClass first,const myClass second)  

```
thanks again

---

### Post by dribeas on 2008-09-10
> **monkeyking said:**
> ```

myClass operator+ (const myClass first,const myClass second)  

```

Just add references there:

```

namespace myNamespace {
   class myClass;
   myClass operator+( myClass const & lhs, myClass const & rhs );
}

```

Using 'type const &' instead of 'const type &' is just a matter of style (and a little [readability]("http://www.parashift.com/c++-faq-lite/const-correctness.html#faq-18.5") when defining pointers). Using references removes the copy penalty (you get the external objects, not copies of them).

Also note that the operator must be defined in the same namespace as the class.

---

