---
title: "C++ const question"
date: 2011-08-11
forum: Programming Talk
---

### Post by t1497f35 on 2011-08-11
Hi,
Can anyone please explain what the **const** is for in this case?:

```

SomeClass::getSomeValue() const {
    return something;
}

```

---

### Post by dwhitney67 on 2011-08-11
It implies (advertises) that the method will not, and cannot, alter any member data of the class when the method is called.

An exception to this rule is when a member data object is declared with the attribute 'mutable'.

---

### Post by t1497f35 on 2011-08-11
Thanks a lot!
This "advertising" is simply a protection mechanism or to allow the compiler to make some optimizations? ..or both?

---

### Post by PaulM1985 on 2011-08-11
A protection mechanism.  I am not aware of any compiler optimizations.  It helps for situations like this:

```

MyObj::Set(int a)
{
  m_a = a;
}

int MyObj::Get() const
{
  return m_a;
}

void SomeFunc(const MyObj &someObj) // <- someObj is a const reference so you can only call const functions on it
{
  int a = someObj.Get(); // <- This line is fine
  someObj.Set(a + 1); // <- This line will fail to compile
                      // because you are trying to call a
                      // non-const function on a const reference
}

```

So you know that if you pass in an instance of MyObj into SomeFunc in the example above, your MyObj is safe and the internal state of MyObj will not be meddled with.  I know my example is brief and missing lots of code, but hopefully there is enough there for you to get the point, let me know if you need this explaining further.

Paul

---

### Post by vikas.sood on 2011-08-11
To add to it.

If your class object is declared const, only member functions which are const can be called for that object.

eg code
```

const SomeClass someObj;
someObj.getSomeValue(); // This is OK, since getSomeValue() is const
someObj.callToSomeNonConstFunction() // Compile time error.

```

---

### Post by t1497f35 on 2011-08-11
Thanks anyone, I get it now!

---

### Post by dwhitney67 on 2011-08-11
Paul & Vikas,

Both of you made fine comments, however the OP was inquiring about what the attribute 'const' implies when associated at the trailing end of the declaration of a class method.

So, to offer a simple example, here goes:
```

class Foo
{
public:
   ...

   void setValue(int val)
   {
      value = val;
      valueStale = false;
   }

   int getValue() const
   {
      valueStale = true;   // ok, because declared mutable
      return value;
   }

   bool isValueStale() const
   {
      return valueStale;
   }

private:
   int value;
   mutable bool valueStale;
};

```

---

