---
title: "What I'am doing wrong?"
date: 2012-06-16
forum: Programming Talk
---

### Post by michalp on 2012-06-16
Hi 

I just started with C++ and I did something like this:

main.cpp
```

int main ( int argc, char** argv )
{
   MyClass * First = new  MyClass();

   First()-> DoSomething();

    First->~MyClass();
    delete First;

    return 0;
}

```and MyClass.h
```

class MyClass
{
    public:
        MyClass();
        virtual ~MyClass();
    protected:
    private:
    AnotherClass * Second;
};

```MyClass.cpp
```

MyClass::MyClass()
{
    Second = new AnotherClass();
}

MyClass::~MyClass()
{
    Second->~AnotherClass();
    delete this->Second;
}

```Let the *AnotherClass* is total empty. What is wrong with this? I got segmentation fault at the end of the program. Could you please help me? As far as I know when I use [COLOR=Blue]new[/COLOR] then I should have use [COLOR=Blue]delete[/COLOR]. When I comment the line with *delete this->Second;* then the program will exit cleary but of course *valgrind *will report a memory leak.

---

### Post by Zugzwang on 2012-06-16
First of all, note that your code doesn't actually compile.

For example, "First()->DoSomething();" won't work, because First() is neither a function, no has some overloaded operator to make the "()" have any semantic meaning. When next posting something, please make a minimal running example.

Note that destructors are called *automatically* upon deletion of an object. You don't have to do it yourself. For example, change
```

Second->~AnotherClass();
    delete this->Second;

```
to simply
```

    delete this->Second;

```

Note that the "this->" is actually not necessary. "delete Second" will do the trick, too.

---

### Post by michalp on 2012-06-16
My mistake my apology. I meant do do it like this:
```

int main ( int argc, char** argv ) 
{    
[INDENT]MyClass * First = new  MyClass();  

//   First()-> DoSomething();      

First->~MyClass();     
delete First;      
return 0; 
[/INDENT]}

```

So thanks fo the tip with destructor, but it doesn't solve my problem with Segmentation fault.

---

### Post by michalp on 2012-06-16
Now I know where was the problem. I called *destructor* explicitly a then again when I used [COLOR=Blue]delete[/COLOR]. It runs *destructor* twice and that is the **problem**!

---

