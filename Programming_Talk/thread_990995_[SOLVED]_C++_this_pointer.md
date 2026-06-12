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

Now my question is this: Is this behavior specific to the GCC compiler? I hav always treated the this pointer as an object more than a pointer during the time I was learning C++ several years ago, and that is how it used to work in other object oriented programming languages like C#

Comments appreciated

---

### Post by jimi_hendrix on 2008-11-23
i have never used this in C++ but in C# as you said it seems to be more of an instantiation of the object you are in

---

### Post by SledgeHammer_999 on 2008-11-23
As you said 'this' is a pointer. Every pointer in C++ that points to a class/struct is dereferenced using the "->" symbols.
[http://www.cplusplus.com/doc/tutorial/classes.html](http://www.cplusplus.com/doc/tutorial/classes.html)

I don't know about other languages, this is the way C and C++ works with pointers.

---

### Post by jimi_hendrix on 2008-11-23
wow i just noticed there were pointers in C#...wow

---

### Post by Rany Albeg on 2008-11-23
In java,for example, you write this.Foo cuz of the fact that its all pointers and you can avoid using the -> operator by declaration of Sun.
since C++ isnt Java :) you have to use ->

have a nice day :}

---

### Post by snova on 2008-11-23
Other languages don't have pointers, so they don't even *have* a -> operator. But C++ does, and distinguishes between objects and pointers. 'this' is a pointer and must be used as such.

---

### Post by gnusci on 2008-11-23
"this" is a pointer, you have to use it like **this->foo** otherwise you can use ***this.foo**.

---

### Post by Nemooo on 2008-11-23
> **gnusci said:**
> "this" is a pointer, you have to use it like **this->foo** otherwise you can use ***this.foo**.

A little correction:

**this->foo** is equal to **(*this).foo**. Often called pointer to a member, whereas ***this.foo** would imply that **this **is the name of a structure.

Or does it work differently in C++?

---

### Post by jimi_hendrix on 2008-11-23
when do you use a this pointer in C++ anyway?

---

### Post by snova on 2008-11-23
> **Nemooo said:**
> A little correction:

**this->foo** is equal to **(*this).foo**. Often called pointer to a member, whereas ***this.foo** would imply that **this **is the name of a structure.

Or does it work differently in C++?

No, you are correct. *this.foo is equal to *(this.foo).

As for when it is used, sometimes I think it would be easier to use classes the Python way, with an explicit self. The compiler would probably have an easier time finding the scope (meaning faster compilation), too. And, you don't have to use ugly member names like m_var just to get around stupid scoping rules.

---

### Post by kvorion on 2008-11-23
> **jimi_hendrix said:**
> when do you use a this pointer in C++ anyway?

Well its actually just a matter of programming practice. When setting the value of a member field, and when you have a parameter whose name is the same or similar to that of the member, then I use this to effectively differentiate between the two.

---

### Post by samjh on 2008-11-23
Oh man, I didn't know you posted two threads about this.

My reply from the other thread:

You have to keep in mind that [FONT="Courier New"]this[/FONT] is a pointer.

So to put as simply as possible, [FONT="Courier New"]this[/FONT] is a pointer to your [FONT="Courier New"]IntCell[/FONT] object, so you need to use the -> dereference operator in order to access its members, just like other pointers to objects/structs.

[quote=kvorion]Now my question is this: Is this behavior specific to the GCC compiler? I hav always treated the this pointer as an object more than a pointer during the time I was learning C++ several years ago, and that is how it used to work in other object oriented programming languages like C#. It may be my memory playing tricks with me, but when I was using turbo C++ to learn C++ in college, I think I used to write it as this.foo[/quote]No, it's not specific to gcc.

Turbo C++ was not ANSI/ISO compliant.  In fact, there was no C++ standard during its time, so your success with the dot operator would have been due to the compiler's own dialect of C++.

---

### Post by kvorion on 2008-11-23
Sorry for creating two threads inadvertently. The page timed out on me and I did a refresh which triggered a fresh postback.
Thanks for the comments.

---

