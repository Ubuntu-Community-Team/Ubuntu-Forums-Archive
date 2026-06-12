---
title: "Declaration Info"
date: 2007-05-28
forum: Programming Talk
---

### Post by YourFriendlyGopher on 2007-05-28
Hi, I've been making a few programs in C++ lately and have been confused with how to 'properly' declare member attributes in classes. I am wondering what the difference between this:

```

class Foo
{
      public:
            Foo();
      private:
            Bar * var; // Pointer variable
};

...

(in cpp file )

Foo::Foo()
{
      var = new Bar("arg"); // Create instance of 'Bar'

      ...
}


```

and this is:

```

class Foo
{
      public:
            Foo();
      private:
            Bar var; // Created with initializer list
};

...

(in cpp file)

Foo::Foo()
 : var( "arg" )
{
      ...
}

```

So far my programs have been fairly inconsistent in regards to this since I'm not sure what the benefits/shortcomings are of these methods (if any), so if anyone can help it will be appreciated ;).

---

### Post by YourFriendlyGopher on 2007-05-29
Bump?

---

### Post by nitro_n2o on 2007-05-29
If you are asking when to use a pointer variable as  oppose to using the normal variable there is a very big difference. In "most cases" when you pass the variable to a function you are passing a copy of that variable so if you have a function like: 
```
int hello(Bar bar)
``` then you are copying the whole thing "bar" to be used in that function, which makes your program very slow if Bar is big object and you pass to other functions many time. However, when you use a pointer you'll not copy the variable instead you'll operate in memory!! Pointers are pretty nasty and very powerful if you know how to use them, especially in issues related to inheritance in c++. In short if the variable is small in size like char or int use them normally otherwise use the pointer. 
hope that helps!

---

