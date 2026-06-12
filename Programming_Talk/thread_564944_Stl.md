---
title: "Stl"
date: 2007-10-01
forum: Programming Talk
---

### Post by Rij on 2007-10-01
Hello,
I am a little confused with STL functioning.

I have the following:
typedef struct __c1 {
int x, y;
} C1;

typedef struct __c2 {
float f;
C1 *ptr;
} C2;

struct lthan
{
  bool operator()(const C2* s1, const C2* s2) const
  {
    return s1->f < s2->f;
  }
};

typedef struct __c3 {
 int id;
 multiset<C2*,lthan> Q;
} C3;

Finally, I have: vector<C3*> mylist;

Now, I want to create a list of just 1 element.
SO I have:
C1 *c1 = (C1*)malloc(sizeof(C1));
C2 *c2 = (C@*)malloc(sizeof(C2));
c2->ptr = c1;
C3 *c3 = (C3*)malloc(sizeof(C3));
mylist.push_back(c3);
mylist[0]->Q.clear();
mylist[0]->Q.insert(c2);

-- The last two lines are generating SIGSEGV

Am I missing something?

Thanks ...

---

### Post by CptPicard on 2007-10-01
Well, first of all you're mixing malloc with C++. Don't do that. Use "new", and "delete". Or, uh, is this supposed to be C with STL (C++) thrown in? Don't think it works..

Also, I'm not a C++ guru but what's with that struct with operator()? I do understand you're doing a comparison operator for your MultiSet, but I have never seen anything like that... :confused:

---

### Post by Jessehk on 2007-10-01
There are several mistakes in your code. I haven't looked in depth, but correcting them may fix the error.

```

typedef struct __c1 {
int x, y;
} C1;

```

Names with 2 leading underscores are reserved by implementation. Don't use them.

```

bool operator()(const C2* s1, const C2* s2) const
{
return s1->f < s2->f;
}

```

Is there a particular reason you're using pointers here?

Why not this instead?
```

bool operator()( const C2 &s1, const C2 &s2) const {
    return s1.f < s2.f;
}

```


```

typedef struct __c3 {
int id;
multiset<C2*,lthan> Q;
} C3;

```

I'm not entirely sure, but I don't think you want a std::multiset of pointers to C2. Why not just:
```

std::multiset<C2, lthan> Q;

```

Finally, without going through it line by line, you've got to stop writing C. 
it's **new**, not **malloc**.

The container classes don't hold pointers-to-objects, they hold objects.

And use better names; the ones you've got now are really adding to the confusion.

---

### Post by Rij on 2007-10-01
```

typedef struct __c3 {
int id;
multiset<C2*,lthan> Q;
} C3;

```

I'm not entirely sure, but I don't think you want a std::multiset of pointers to C2. Why not just:
```

std::multiset<C2, lthan> Q;

```

-------

I have simplifies my code but in reality, C2 is a big object. Considering that containers store objects by value, I wanted to store the pointers to reduce space requirements. Is that the bane of my woes?

---

### Post by dwhitney67 on 2007-10-02
I think the main issue that has been pointed out is that you are mixing C and C++ concepts, which IMO does make your code confusing.

Dispense with the typedef in front of your struct declarations.  That isn't necessary.  A struct is the same as a C++ class, with the exception that by default, all data members and methods are public.  With a class, by default all data members and methods are private.

Here's your code again, but with some extra touches:

[PHP]#include <vector>
#include <set>

struct C1
{
  C1( int x = 0, int y = 0 ) : x(x), y(y) {}
  int x;
  int y;
};

struct C2
{
  C2( C1* ptr, float f = 0.0 ) : c1_ptr( ptr ), f(f) {}
  float f;
  C1 *c1_ptr;
};

struct LessThan
{
  bool operator()(const C2 *s1, const C2 *s2) const
 {
    return s1->f < s2->f;
  }
};

struct C3
{
  int id;
  std::multiset<C2*, LessThan> Q;
};

int main()
{
  std::vector<C3*> myVector;

  C1 *c1 = new C1();
  C2 *c2 = new C2( c1 );
  C3 *c3 = new C3;

  myVector.push_back( c3 );
  myVector[0]->Q.clear();
  myVector[0]->Q.insert( c2 );

  delete c3;
  delete c2;
  delete c1;
}[/PHP]

---

### Post by ilautar on 2007-10-02
> **Jessehk said:**
> There are several mistakes in your code. I haven't looked in depth, but correcting them may fix the error.

I'm not entirely sure, but I don't think you want a std::multiset of pointers to C2. Why not just:



Of course containers can hold pointers. You might be thinking of not putting auto_ptr<> into containers.

> **Jessehk said:**
> 

The container classes don't hold pointers-to-objects, they hold objects.



Yes they do. Even lookup works correctly, as key is memory address.

---

### Post by hod139 on 2007-10-02
> **dwhitney67 said:**
> 
Here's your code again, but with some extra touches:
<snip> 
I think you did an excellent job rewriting his/her code, but there is a minor problem with it.

```

struct C2
{
  C2( C1* ptr, float f = 0.0 ) : c1_ptr( ptr ), f(f) {}
  float f;
  C1 *c1_ptr;
};

```This is a potential bug, the initializer list must initialize the the variables in the same order they are declared.  If you had attempted to use c1_ptr when you initialized f, you would have had some big problems.  The fix is simple though: 
```

struct C2
{
  C2( C1* ptr, float f = 0.0 ) :  f(f), c1_ptr( ptr ) {}
  float f;
  C1 *c1_ptr;
};

```Also, const correctness is C++ is a giant mess, but you might want to consider add more const protection to the Less than struct functor.
```

bool operator()(const C2 * **const** s1, const C2 * **const** s2) const
 {
    return s1->f < s2->f;
  }


```The additional const makes it so s1 and s2 are const pointers, so something like:
s1 = &foo;
is illegal.
It probably is not important for this function, but you had so much other good const protection in there I figured I mention it.

---

### Post by Rij on 2007-10-02
Thanks folks. The new/delete seems to have done the trick. Thanks also for the great suggestions on the code.

---

