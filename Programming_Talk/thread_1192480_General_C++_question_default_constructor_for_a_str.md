---
title: "General C++ question: default constructor for a struct member"
date: 2009-06-20
forum: Programming Talk
---

### Post by MoToR on 2009-06-20
Hi all,

I'm stuck for a few hours (googling and) trying to write the next
```

typedef struct S
{
[INDENT]int a;
int b;[/INDENT]
} S;

class A
{
private:
[INDENT]S aMember;[/INDENT]
public:
[INDENT]A(S s = {0, 0}) : aMember(s) {}[/INDENT]
};
```

I need both a parametric c'tor and a default c'tor and I'd like to combine them as usual using default values in the parameters list of the parametric c'tor, but g++ won't let me, it says: "expected primary-expression before '{' token".

What am I doing wrong? Is there a way to do exactly what I want to do or should I just define a separate default c'tor with field by field initialization of aMember?

Thank you.


BTW, did someone else experience a bug when [_INDENT_] BB tag also added a Break Line that no one asked for?

---

### Post by smartbei on 2009-06-20
You can't do that, not like that anyway. Here is something more along the lines:
Note that in C++, Structs and Classes are identical except that in a struct the members are by default public.
```

typedef struct S
{
    int m_a;
    int m_b;

} S;

class A
{
private:

    S m_Member;

public:

    A(S s) : m_Member(s) {}

};

```
Also note that this works because it uses the default copy-constructor for S, so implementing one is not needed.
If you want there to be a constructor for A that doesn't require you to pass S, I would do something like:
```

typedef struct S
{
    S(int a = 0, int b  = 0) : m_a(a), m_b(b) {}
    int m_a;
    int m_b;

} S;

class A
{
private:

    S m_Member;

public:

    A(S s) : m_Member(s) {}
    A(): m_Member() {}
};

```

---

### Post by Idefix82 on 2009-06-20
smartbei, your code doesn't do exactly what MoToR had asked for. You have to overload the constructor to do what you want:
```
typedef struct S
{
    int m_a;
    int m_b;
} S;

class A
{
private:
    S m_Member;
public:
    A(){m_Member={0,0}}
    A(S s) : m_Member(s) {}
};

```

Edit: ignore this, smartbei has edited his post.

---

### Post by MoToR on 2009-06-20
Thanks, **smartbei** and **Idefix82**.

**smartbei**, the idea of redefining the default c'tor in the S struct is a good solution in general. As **Idefix82** noticed, I wanted to achieve something slightly different, I want to write the class A in a way that:

a) makes it clear to anyone who looks at the class A definition, what default values all A members get when its default c'tor is called.
b) makes it easy to change those default values without affecting any other data type.

As far as I understood, the only way to achieve my goals is to define a default constructor explicitly, moreover it seems that I have to define a parametric c'tor for the struct S and subsequently use it in the default c'tor of class A, since I wasn't able to use that ... = {0,0} syntax in an initializer list either, due to the same error.

It seems that the curly brackets syntax for struct initializing is unsupported by C++. Am I correct?

---

### Post by MoToR on 2009-06-20
**smartbei**, I was looking again at your code and I realized that it's fully suitable for my purpose. I can just define the values this way:
```

    A(): m_Member(0,0) {}

```
the default values are visible in the class A definition and they are exclusive to the class A definition (even though they are equal to the struct S defaults here).

---

