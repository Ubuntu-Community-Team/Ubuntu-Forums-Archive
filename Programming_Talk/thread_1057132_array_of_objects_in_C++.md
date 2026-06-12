---
title: "array of objects in C++"
date: 2009-02-01
forum: Programming Talk
---

### Post by cybo on 2009-02-01
i'm trying to allocate an array of objects in one of my classes, but for some reason my program crashes. i used ddd to find the problem and it looks like that the address of the second element is changing by itself. i think there is something i'm missing. i appreciate any help. below is the code:


```
class MyOtherClass {
  public:
    explicit MyOtherClass(int num)
};

class MyClass {
  public:
    explicit MyClass(int num);
    MyOtherClass* array[];
};

MyClass::MyClass(int num) {
  for (int i = 0; i < num; i++)
    array[i] = new MyOtherClass(2);
}

int main(int argc, char** argv){
  MyClass* obj = new MyClass(4);
  obj->array[2]; // <-- this is where my code fails
                 // i can access obj->array[0], but except that
                 // nothing else
  return 0;
}
```

---

### Post by nvteighen on 2009-02-01
Of course, you're not allocating memory for your array anywhere. You should do it in the constructor and then deallocate that memory in the destructor.

I don't know C++, so I can't bring up any example.

---

### Post by kjohansen on 2009-02-01
in the constructor you would need a line like:

```

array=new MyOtherClass[num];

```

then in the destructor:

```

delete[] array

```

---

### Post by cybo on 2009-02-01
> **kjohansen said:**
> in the constructor you would need a line like:

```

array=new MyOtherClass[num];

```

then in the destructor:

```

delete[] array

```

i need to pass a parameter to each of my objects. i need to do something like this
```

array = new MyOtherClass(2)[num];

```

the compiler won't let me do that.
any suggestions?

---

### Post by Cracauer on 2009-02-01
The first one is an array of pointers to instances of MyOtherClass, not an array of MyOtherClass installed.

You never allocate space for the actual array.

---

### Post by dribeas on 2009-02-01
> **cybo said:**
> i need to pass a parameter to each of my objects. i need to do something like this
```

array = new MyOtherClass(2)[num];

```

the compiler won't let me do that.
any suggestions?

You are confusing there the construction of the array with the construction of the elements. 

```

class MyClass
{
public:
   MyClass();
private:
   MyOtherClass **array;
};
MyClass::MyClass(int num) 
      : array( new MyOtherClass* [num] )  // initialize the array of pointers
{
  for (int i = 0; i < num; i++)
    array[i] = new MyOtherClass(2); // initialize each pointer with a new object.
}

```

---

### Post by dwhitney67 on 2009-02-01
If you are permitted to use STL, then consider using a vector.

[php]
#include <vector>
...

class MyClass
{
public:
   MyClass(const int num);

private:
   std::vector<MyOtherClass*> array;
};

MyClass::MyClass(const int num)
{
  for (int i = 0; i < num; i++)
  {
    array.push_back(new MyOtherClass(2));
  }
}
[/php]

---

### Post by cybo on 2009-02-01
> **dribeas said:**
> You are confusing there the construction of the array with the construction of the elements. 

```

class MyClass
{
public:
   MyClass();
private:
   MyOtherClass **array;
};
MyClass::MyClass(int num) 
      : array( new MyOtherClass* [num] )  // initialize the array of pointers
{
  for (int i = 0; i < num; i++)
    array[i] = new MyOtherClass(2); // initialize each pointer with a new object.
}

```
thank you. i see what my mistake was. i appreciate the help.

---

