---
title: "Help understand this singleton c++ code"
date: 2013-11-03
forum: Programming Talk
---

### Post by Mr.Pytagoras on 2013-11-03
Hi

I was looking at gnote source files and I was not able to understand how one code works, it's singleton template base class. Could someone very good at c++ explain how this works? 

Here is the code:
```
#ifndef __BASE_SINGLETON_HPP__
#define __BASE_SINGLETON_HPP__

#include <cstddef>

namespace base {

    template <typename T>
    class Singleton
    {
       public:
       static T & obj()
       {
            return obj(NULL);
       }
       protected:
       Singleton()
       {
           obj(static_cast<T*>(this));
       }
       private:
       static T & obj(T * inst)
       {
           static T *instance = NULL;
           if(inst) {
              instance = inst;
           }
           return *instance;
       }
    };
}

#endif
```

Now, if you call public *obj* it will always call the private obj with NULL, so when the actual instance of the subclassed class is created?

Thanks  for clarification.

---

### Post by dwhitney67 on 2013-11-03
> **Mr.Pytagoras said:**
> Hi

I was looking at gnote source files and I was not able to understand how one code works, it's singleton template base class. Could someone very good at c++ explain how this works? 

Here is the code:
```
#ifndef __BASE_SINGLETON_HPP__
#define __BASE_SINGLETON_HPP__

#include <cstddef>

namespace base {

    template <typename T>
    class Singleton
    {
       public:
       static T & obj()
       {
            return obj(NULL);
       }
       protected:
       Singleton()
       {
           obj(static_cast<T*>(this));
       }
       private:
       static T & obj(T * inst)
       {
           static T *instance = NULL;
           if(inst) {
              instance = inst;
           }
           return *instance;
       }
    };
}

#endif
```

Now, if you call public *obj* it will always call the private obj with NULL, so when the actual instance of the subclassed class is created?

Thanks  for clarification.

The person who developed the code you are inquiring about probably had many Singleton classes in their project.  Rather than re-write numerous lines of code, they created a templated form of the design pattern.

Perhaps the following example will enlighten you as to how your example template is used:
```

template <typename T>
class Singleton
{
public:
    static T& obj()
    {
        return obj(0);
    }

protected:
    Singleton()
    {
        obj(static_cast<T*>(this));
    }

private:
    static T& obj(T* inst)
    {
        static T* instance = 0;

        if (inst)
        {
            instance = inst;
        }

        return *instance;
    }
};

class MySingleton : public Singleton<MySingleton>
{
public:
    void doSomething()
    {
        // blah...
    }
};

int main()
{
    MySingleton ms;

    MySingleton::obj().doSomething();
}

```

---

### Post by Mr.Pytagoras on 2013-11-07
Thanks for your answer but that wasn't the answer I was hopping for.

I know how to use that template, I'm not a c++ beginner, what I don't know is how that base class works.
If you derive a class from it and then use it somewhere in the code by calling the obj method, how is the actuall instance of that derived class created? It has to be created at some point isn't it? That is the "magic" I don't get, could anybody please explain that?

---

### Post by Mr.Pytagoras on 2013-11-07
Ok, I think I get it now

It was actually your edit that get me thinking :)

So to use it correctly you have to at some point it the code create the actuall instance of the class by hand, as you did. The instance, even that it is created locally it actually calls the singleton constructor which inicialize the static field *instance *which is then never actually reinicialized but only referenced by the obj(0) method, is this correct? And the static_cast<T*> is there to be sure you will allways get  the actuall derived class by calling the obj method.

---

### Post by dwhitney67 on 2013-11-07
> **Mr.Pytagoras said:**
> Ok, I think I get it now

It was actually your edit that get my thinking :)

So to use it correctly you have to at some point it the code create the actuall instance of the class by hand, as you did. The instance, even that it is created locally it actually calls the singleton constructor which inicialize the static field *instance *which is then never actually reinicialized but only referenced by the obj(0) method, is this correct? And the static_cast<T*> is there to be sure you will allways get  the actuall derived class by calling the obj method.

I did not explicitly define a constructor for the MySingleton class, thus the compiler provides one.  When I instantiated a MySingleton obj (in main, or wherever), not only is the constructor called, but so is the (protected) constructor in the base-class.  And, voilà, that's how the singleton class is initialized.

P.S.  The singleton example that you found is actually a poor definition; a clearer example would be:
```

class Singleton
{
public:
    static Singleton& instance()
    {
        if (theInstance == 0)
        {
            theInstance = new Singleton;
        }
        return *theInstance;
    }

    void doSomething() {}

private:
    Singleton() {}

    static Singleton* theInstance;
};

Singleton* Singleton::theInstance = 0;

int main()
{
    Singleton::instance().doSomething();
}

```

Now, if you had a s/w project with possibly 10's or 100's of Singleton objects... then my approach is not worthy.  On the other hand, if a project has 10's or 100's of singleton objects, then it would be worth a 1000 laughs, for undoubtedly it is crapola.

---

