---
title: "[C++]  reinterpret_cast in a base class"
date: 2010-11-25
forum: Programming Talk
---

### Post by lucasart on 2010-11-25
Hello,

Here is my code in a simplified form:

```
extern T func(const Derived &D);

class Base
{
protected:
    Base();

    virtual T f(...) const
    {
        ... somewhere in this code I use
        func(static_cast<const Derived&>*this, ...some base data...);
        ...
    }

private:
    ... base data ...
};

class Derived : public Base
{
public:
    Derived();

    T f(...) const
    {
        ... somewhere in this code I use
        func(*this, ...some base + derived data...);
        ...
    }

private:
    ... derived data ...
};

```Where

[LIST]
[*]T is a type that doesn't matter to detail here
[*]func is a function that, in general, needs all the info of the Derived class
[/LIST]
The point of all this is that

[LIST]
[*]func(*this, ...some base + derived data...) will use the base data and the derived data
[*]func(static_cast<const Derived&>*this, ...some base data...) will actually not to use the derived data, so it's OK to do it. especially as the memory will have been allocated from the derived data, since a base class cannot be instanciated (protected ctor)
[/LIST]
So if I understand correctly, the reinterpret_cast will shift this pointer by sizeof(derived date) -- and maybe more due to some alignment stuff. And all this should do the trick.

I could have just coded f in the Derived class, but as there might be several derivations to the base class and the code in Base.f is the common part, I don't want to duplicate it.

However, I really don't like using this nasty static_cast, as it makes the code somewhat obscure, and you really have to look into func to understand why it's actually OK to do all this.

Perhaps my design choice is just wrong in the first place. I'm still quite a newbie in C++, but I wonder how a serious developper would have concieved all this instead.

Suggestions and criticism (even harsh) are welcome!

---

