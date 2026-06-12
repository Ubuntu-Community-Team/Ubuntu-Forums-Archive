---
title: "[SOLVED] Class to wrap another class instance?"
date: 2008-07-23
forum: Programming Talk
---

### Post by Senesence on 2008-07-23
My method so far has been:

[PHP]
MyClass{
    private:
    SomeOtherClass instance;

    public:
    MyClass(int x, string y, float z){
        instance.A(x);
        instance.B(y);
        instance.C(z);
    }

    void someNameILike(){
        instance.D();
        instance.E();
    }
};
[/PHP]

However, I am now faced with a situation where instead of methods A, B and C, "SomeOtherClass" only has a constructor that would take x, y and z as arguments.

So I'm wondering, in that situation, is there still a way to create an instance of "SomeOtherClass", but invoke it's constructor from the constructor of "MyClass", or is there a better way to do this?

---

### Post by dribeas on 2008-07-23
> **Senesence said:**
> My method so far has been:

[PHP]
MyClass{
    private:
    SomeOtherClass instance;

    public:
    MyClass(int x, string y, float z){
        instance.A(x);
        instance.B(y);
        instance.C(z);
    }

    void someNameILike(){
        instance.D();
        instance.E();
    }
};
[/PHP]


Change your constructor into:

```

MyClass( int x, int y, int z ) : instance(x,y,z) {}

```

You may also consider using [PIMPL idiom]("http://en.wikipedia.org/wiki/Pimpl"). You can, and should, replace the raw pointer in the sample code there with std::auto_ptr so that you do not need to take care of deletion.

---

### Post by Senesence on 2008-07-24
Great, that works.

[quote=dribeas]You may also consider using PIMPL idiom. You can, and should, replace the raw pointer in the sample code there with std::auto_ptr so that you do not need to take care of deletion.[/quote]

Those sound like good alternatives. Although, I'm not sure if I really need something as versatile as "smart pointers" at this stage. I mean I'm not working on anything big/complex, so doing things manually for now is a good way to learn about C++.

But just to make sure I understand this, using the PIMPL idiom with the "raw pointer" would look like this:

[PHP]
MyClass{
    private:
    SomeOtherClass* ptr_instance;

    public:
    MyClass(int x, string y, float z){
        ptr_instance = new SomeOtherClass(x, y, z);
    }

    void someNameILike(){
        ptr_instance->D();
        ptr_instance->E();
    }
    
    ~MyClass(){
        delete ptr_instance;
    }
};
[/PHP]

Right?

Thank you.

---

### Post by dribeas on 2008-07-24
Yes, it would look like that. Some of the interesting points are that you can forward declare the internal class in the header file (as only pointers are used you don't need the complete definition there) and only include the whole definition in your implementation file. And if the internal class changes, only the internal class and the implementation must be recompiled, no user (code) of your class needs recompiling.

I cannot agree with you in that being novice you don't need smart pointers. Smart pointers are the only way in quite a few problems, and the earlier you work with them the better. Just to put up an example:

```

// ...
    MyClass(int x, string y, float z){
        ptr_instance = new SomeOtherClass(x, y, z);

        // some more code with a call that may throw
    } 
// ...
    ~MyClass(){
        delete ptr_instance;
    } 

```

If you later add code as above, after the 'new', but inside the constructor and an exception is thrown the object was never fully constructed and the destructor will not be called. Now you have a memory leak. Using std::auto_ptr<> memory will be released by compiler generated code.

Andrew Koening in [Accelerated C++]("http://www.amazon.com/Accelerated-Practical-Programming-Example-Depth/dp/020170353X") teaches the language starting with STL, I don't have the book here and now, but I don't think you see a pointer in the first half of the book.

The earlier you learn STL the better. But that's just my opinion.

David

---

### Post by Senesence on 2008-07-24
> **dribeas said:**
> If you later add code as above, after the 'new', but inside the constructor and an exception is thrown the object was never fully constructed and the destructor will not be called. Now you have a memory leak. Using std::auto_ptr<> memory will be released by compiler generated code.

Ahh, I see.

Thanks again.

---

