---
title: "const struct member initializing"
date: 2008-10-28
forum: Programming Talk
---

### Post by Sydius on 2008-10-28
This is in C++.

I have been making a special-purpose linked list (for a cache system) and my nodes look like this:

```
struct CacheItem
{
    const K key;
    const D * const data;
    CacheItem * next;
}
```

Is there a way to initialize the const members without adding a constructor, when allocating them from memory with new? Example:

```
CacheItem * item = new CacheItem;
```

If not, which is more efficient: keeping them const, so the compiler can use that information to write more efficient assembly but with the price of an (empty) constructor, or removing const and just being careful not to write to them?

---

### Post by Sydius on 2008-10-28
In my case, using const with a constructor seems very slightly faster, but I'm still curious about whether or not the constructor is required.

---

### Post by dribeas on 2008-10-28
> **Sydius said:**
> In my case, using const with a constructor seems very slightly faster, but I'm still curious about whether or not the constructor is required.

I believe that you are required to create the constructor if you want to instantiate with new. If you were creating objects in the stack you could use initialization lists. But allocating with new you cannot use this method. Of course, you could create a local object and then use the default provided copy constructor:

```

struct X
{
   const int a;
   const double b;
   const X* next;
};

int main()
{
   X x = { 5, 4.2, 0 }; // Initialization list
   X *xp = new X( x ); // Valid: implicit copy constructor
}

```

But I guess this limits the usefulness of the performance boost you could get from having all members const. (I wonder how you meassured the boost and what the results were).

Of course, providing a constructor will not make it any less efficient:

```

X::X( int _a, double _b, X const * _next ) : a(_a), b(_b), next(_next) {};

```

---

### Post by Sydius on 2008-10-28
[QUOTE=dribeas]I wonder how you meassured the boost and what the results were[/QUOTE]

My cache class has "add" and "get" methods.  I made a loop to add/get 10,000,000 entries (storing 100 at a time, but no cache misses), and it took ~4.8 seconds with const and a constructor, but ~4.9 without const and without a constructor.  I ran the tests a few times and they were consistently about 0.1 seconds apart.  Not enough to matter, I'd say.  That's with gcc 4.2.4 with the "-O" option.

I thought maybe the constructor would add overhead of some sort.

---

### Post by dribeas on 2008-10-30
> **Sydius said:**
> My cache class has "add" and "get" methods.  I made a loop to add/get 10,000,000 entries (storing 100 at a time, but no cache misses), and it took ~4.8 seconds with const and a constructor, but ~4.9 without const and without a constructor.  I ran the tests a few times and they were consistently about 0.1 seconds apart.  Not enough to matter, I'd say.  That's with gcc 4.2.4 with the "-O" option.

I thought maybe the constructor would add overhead of some sort.

In most cases, it reduces overhead instead of adding. You should run the tests once again, this time with non-const and a constructor and check results.

The fact that you do not have a constructor only means that the compiler will automatically generate one for you.

```

struct X
{
   int x;
   double y;
   std::string str;
};
// Default constructor is created by compiler equivalent to:
// X::X() : x(0), y(0.0), str() {} // empty string

int main()
{
   X x; // calls default constructor
   x.x = 1;
   x.y = 2.0;
   str = "Hi";
}

```

In the code above, memory is allocated in the stack, x gets initially a 0, y a 0.0, str an empty string. Then values are overwritten by the code. The result is that each of the data members is assigned two different values.

If you provide a constructor with initialization list ( the funny : syntax between constructor parameters and the { ) then the value is assigned only once.

If the constructor is created, but the assignment is inside the brackets you are back with the initial problem: double assignment.

---

