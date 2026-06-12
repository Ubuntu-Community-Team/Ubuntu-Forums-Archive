---
title: "C++ const question"
date: 2009-12-21
forum: Programming Talk
---

### Post by kahumba on 2009-12-21
Folks I know consts are used when the var shouldn't change, but what does this const do here?

```

class Access {
  int i;
public:
  int read() const { return i; }// THIS CONST
  void set(int ii) { i = ii; }
};

int main() {
  Access A;
  A.set(100);
  int x = A.read();
}

```
Anyone?

---

### Post by Some Penguin on 2009-12-21
It stipulates that that particular method does not change the object.

---

### Post by kahumba on 2009-12-21
Which object? The variable "i"? (In Java we call them primitives)

---

### Post by Some Penguin on 2009-12-21
The instance of the class Access.  Such as, say, your variable 'A' -- because read() is marked const, A.read() can be called without changing A.  This might be useful if, say, you have a 'const' instance -- then you'd want to be calling const methods only.

---

### Post by kahumba on 2009-12-21
Thanks!

---

### Post by dwhitney67 on 2009-12-21
There are rare cases where you might come across code such as the following:
```

class Foo
{
public:
   Foo() : value(0) {}

   int getValue() const { return ++value; }

private:
   mutable int value;
};

int main()
{
   Foo foo;
   foo.getValue();
}

```
Note the declaration of the class data member 'value'; it has the keyword "mutable" in front of it.  This allows for 'value' to be changed in a const-declared method.  The compiler will allow it.  Non-mutable variables would not be allowed to be changed within the same method.

---

### Post by era86 on 2009-12-21
> **dwhitney67 said:**
> There are rare cases where you might come across code such as the following:
```

class Foo
{
public:
   Foo() : value(0) {}

   int getValue() const { return ++value; }

private:
   mutable int value;
};

int main()
{
   Foo foo;
   foo.getValue();
}

```
Note the declaration of the class data member 'value'; it has the keyword "mutable" in front of it.  This allows for 'value' to be changed in a const-declared method.  The compiler will allow it.  Non-mutable variables would not be allowed to be changed within the same method.

Pardon my ignorance, but why would you declare a const method to work on a mutable object?  The point of const is to protect that instance right?  If you allow it to modify the variable, you are changing the state of that instance.

Or am I just confusing myself... :confused:

---

### Post by dwhitney67 on 2009-12-21
> **era86 said:**
> Pardon my ignorance, but why would you declare a const method to work on a mutable object?  The point of const is to protect that instance right?  If you allow it to modify the variable, you are changing the state of that instance.

Or am I just confusing myself... :confused:

When developing thread-safe methods, there are cases where one would need to lock a mutex or wait on a semaphore before accessing the data.

For example:
```

int getValueFromTable(int key) const
{
   mutex.lock();

   const int value = table.at(key);

   mutex.unlock();

   return value;
}

```
Here, the container 'table' is not modified, nor does it need to be... thus the justification of declaring the method as const.  However, because the mutex is being manipulated in the method, it must be declared as mutable.

The example I provided in my earlier post was a basic/silly example used to convey the concept of the keyword 'mutable'.

As for your perception/understanding of the purpose of const methods, hopefully you will be a wee-bit more enlightened after reading this post.

---

### Post by era86 on 2009-12-22
Sure am... didn't think about multithreaded apps.  Thanks for the clarification!

---

### Post by Can+~ on 2009-12-22
> **kahumba said:**
> Which object? The variable "i"? (In Java we call them primitives)

In java, variables are called variables. "Primitives" are names for the  pre-defined types in Java that are (exceptionally) not classes.

---

