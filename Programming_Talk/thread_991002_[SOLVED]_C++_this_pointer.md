---
title: "[SOLVED] C++: this pointer"
date: 2008-11-23
forum: Programming Talk
---

### Post by kvorion on 2008-11-23
I am fiddling around with C++ after several years.
I just wrote a small code snippet to dust off my C++ and I came across a strange thing (apparently) which was not at all familiar to me....I made this simple class:

```

class IntCell
{
      private:
              int storedValue;
      public:
             explicit IntCell(int storedValue);
             IntCell();
             void Write(int input);
             int Read() const;
};

```

And then I started defining my read and write methods as:

```

//read value in IntCell
int IntCell::Read()const
{
    return this.storedValue;
}

//write value into IntCell
void IntCell::Write(int input)
{
     this.storedValue = input;
}

```

This would give me the error:
```
16 IntCell.cpp `storedValue' is not a type 
```

After googling I found that this error is encountered when you write something as this.Foo instead of this->Foo.

Accordingly when I changed this.storedValue to this->storedValue, things did start working.

Now my question is this: Is this behavior specific to the GCC compiler? I hav always treated the this pointer as an object more than a pointer during the time I was learning C++ several years ago, and that is how it used to work in other object oriented programming languages like C#. It may be my memory playing tricks with me, but when I was using turbo C++ to learn C++ in college, I think I used to write it as this.foo

Comments appreciated

---

### Post by samjh on 2008-11-23
You have to keep in mind that [FONT="Courier New"]this[/FONT] is a pointer.

So to put as simply as possible, [FONT="Courier New"]this[/FONT] is a pointer to your [FONT="Courier New"]IntCell[/FONT] object, so you need to use the -> dereference operator in order to access its members, just like other pointers to objects/structs.

[quote=kvorion]Now my question is this: Is this behavior specific to the GCC compiler? I hav always treated the this pointer as an object more than a pointer during the time I was learning C++ several years ago, and that is how it used to work in other object oriented programming languages like C#. It may be my memory playing tricks with me, but when I was using turbo C++ to learn C++ in college, I think I used to write it as this.foo[/quote]No, it's not specific to gcc.

Turbo C++ was not ANSI/ISO compliant.  In fact, there was no C++ standard during its time, so your success with the dot operator would have been due to the compiler's own dialect of C++.

---

