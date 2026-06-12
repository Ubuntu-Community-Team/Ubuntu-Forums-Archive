---
title: "C++ and Templates"
date: 2013-03-29
forum: Programming Talk
---

### Post by Dirich on 2013-03-29
I am trying to read data from file and store it into structures. These structures are quite similar, but for a couple of fields. As an example:

```

typedef struct
{
   int a;
   int b;
   char c;
} STRUCT_A;

typedef struct
{
   int a;
   int b;
   float d;
} STRUCT_B

```

I use STRUCT_A to make a list of such objects, which are collected in another structure (OVERSTRUCT_A). The same goes on for STRUCT_B and OVERSTRUCT_B (I actually have 4 of such structures, 2 of the used in one OVERSTRUCT and the other 2 in the other, but I'll keep the example simple).

```

typedef struct
{
   STRUCT_A* pA;
} OVERSTRUCT_A;


typedef struct
{
   STRUCT_B* pB;
} OVERSTRUCT_B;

```

Everything is really similar, and since the function that fills the lists of STRUCT_A and STRUCT_B contained in OVERSTRUCT_A and OVERSTRUCT_B respectively is so elaborated, I would like to keep this templetized, so that managing the code is easier (or I would have to type manually every modification twice).
The function looks like this:

```

template <typename T, typename R>
int func (T* STRUCT, R& OVERSTRUCT)
{ /* what I return is irrelevant in this example */ }

```

In the end, all the function does is work with a list, STRUCT is the head of one of the lists (type either STRUCT_A or STRUCT_B) and OVERSTRUCT is the struct containing the head of the list itself (type OVESTRUCT_A or OVERSTRUCT_B respectively).
I need to pass OVESTRUCT because the function needs to conceal any work done on the head of the list (which is automatically ordered while data is read from file). 
Since I have more than 2 STRUCT_X types, it is necessary to pass STRUCT separately  from OVERSTRUCT, to specify which one of the STRUCT in the OVERSTRUCT I want to work with.

I tried:

```

if (typeid (T) == typeid (STRUCT_A)) {OVERSTRUCT.pA}
if (typeid (T) == typeid (STRUCT_B)) {OVERSTRUCT.pB}

```

But this is an error since when OVESTRUCT == OVERSTRUCT_A, the compiler rightly argue that there is no field pB in OVERSTRUCT_A.

Aside from doing something like this:
```

template <typename T>
T* func (T* STRUCT)
{/* the head of the list may change, but the scope of STRUCT is inside func, thus I pass the pointer to the new head by returning by value */}


int main ()
{
  ...
  STRUCT_A.pA = func (pA);
  STRUCT_B.pB = func (pB);
  ...
}

```

How can I solve the problem alternatively?
I tried to explore the option of passing a pointer by reference, but people try to discourage this (I'm not sure why, though). Any other ideas?

---

### Post by dwhitney67 on 2013-03-29
There's no need to typedef a struct in C++.  A struct and a class are identical in every aspect except one:  all members in a struct are public, unless otherwise indicated.  With a class, all members are private, unless otherwise indicated.

With this in mind, you should consider augmenting your structures to provide a friend method that can accept a reference to an istream object so it can read the data from the file itself.

For example (and this code has not been compiled/tested):
```

struct A
{
    int a;
    int b;
    char c;

    friend std::istream& operator>>(std::istream& is, A& objA)
    {
        is >> objA.a >> objA.b >> objA.c;
        return is;
    }
};

struct B
{
    int a;
    int b;
    float d;

    friend std::istream& operator>>(std::istream& is, B& objB)
    {
        is >> objB.a >> objB.b >> objB.d;
        return is;
    }
};

int main()
{
    A a;
    B b;

    std::fstream file("datafile.txt", std::fstream::in);

    if (file)
    {
        file >> a;
        file >> b;
    }
}

```
Alternatively, if your structures have common data, you can create a base structure, along with specialized sub-classes (err, structures).  For example:
```

struct Base
{
    int a;
    int b;
};

struct A : public Base
{
    char c;

    ...
};

struct B: public Base
{
    float d;

    ...
};

```
Using templates may be over-complicating what you require.  Or perhaps I did not fully understand your requirements.

---

### Post by Dirich on 2013-03-29
Eh... My c++ Seems to be a bit rusty.
And the typedef indeed I need only to make lists.

I like both tour ideas. They are very elegant.

The template though is still needed because of reasons related to other stuff I do in the func. If not  for that, I could avoid it with your suggestions.

Thanks!

---

### Post by akvino on 2013-04-03
Dare I say - template metaprograming .. . . . . .. :-)

---

