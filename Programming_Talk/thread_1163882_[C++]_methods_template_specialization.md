---
title: "[C++] methods template specialization"
date: 2009-05-19
forum: Programming Talk
---

### Post by Eres on 2009-05-19
I have a template class MyClass (with template argument typename), with a template method:

```

template <typename Derived>
class MyClass
{
  template <int N> inline void method();
};

```

N can be either 0 or 1. I'd like to specilize that method in this way:

```

template <typename Derived>
template<>
inline void MyClass<Derived>::method<0>
{
  /* Some code here... */
}

template <typename Derived>
template<>
inline void MyClass<Derived>::method<1>
{
  /* Some code here... */
}

```

But that doesn't compile: g++ returns
```

MyClass.h:104: error: invalid explicit specialization before &#8216;>&#8217; token
MyClass.h:104: error: enclosing class templates are not explicitly specialized
MyClass.h:105: error: template-id &#8216;method<0>&#8217; for &#8216;void MyClass<Derived>::method()&#8217; does not match any template declaration

```

Can I specialize with templates a method of a class? If yes, how?

---

### Post by hod139 on 2009-05-19
I think method specializations have to be based off of the classes templated parameters (but I could be wrong).  In any case, a workaround for what you want to do would be to introduce a templated helper class, and make a functor.  Code:

```

// general case
template <int N>
struct methodHelper {
    void operator()() const { /* Some code here... */ }
};

// specializations
template<>
struct methodHelper<0> {
    void operator()() const { /* Some code here... */ }
};
template<>
struct methodHelper<1> {
    void operator()() const { /* Some code here... */ }
};


template <typename Derived, int N>
class MyClass
{
  public:
  inline void method() { methodHelper<N> temp; return temp(); };
};

```

---

### Post by Eres on 2009-05-20
Thank you, hod139. That seems to be great!

My method has to read and modify provate properties of MyClass. How can I declare both methodHelper<0> and methodHelper<1> friends of MyClass? Can I do somthing like this?

```

class MyClass
{
  template <int N>
  friend struct methodHelper<N>;

  /* ... */
};

```

---

### Post by hod139 on 2009-05-20
You will have to do something like:
```

template <typename T, int N>
class MyClass
{
public:
  inline void method() { /* code */ };
};

template <typename T>
class MyClass<T,0>
{
public:
  inline void method() { /* code */ };
};

```

---

### Post by dwhitney67 on 2009-05-20
> **Eres said:**
> 
My method has to read and modify provate properties of MyClass. How can I declare both methodHelper<0> and methodHelper<1> friends of MyClass? Can I do somthing like this?


Ding! Ding! Ding!

Looks like you are headed towards a bad design.

I read your first post, and frankly, I could not understand what you are seeking.  Perhaps, in layman's terms, you could describe your requirements.

---

### Post by monkeyking on 2009-05-20
> **dwhitney67 said:**
> Ding! Ding! Ding!

Looks like you are headed towards a bad design.

I read your first post, and frankly, I could not understand what you are seeking.

Agree.
You should use template specialization for different datatypes,
not different values within the same datatype.

I wont argue that it's never usefull to do it,
but in a general context you shouldn't

---

