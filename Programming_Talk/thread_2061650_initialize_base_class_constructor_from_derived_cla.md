---
title: "initialize base class constructor from derived class in C#"
date: 2012-09-23
forum: Programming Talk
---

### Post by vikkyhacks on 2012-09-23
using System;
class A
{
        public A(int a)
        {
                Console.WriteLine(a);
        }
}
class B:A
{
        public B(int b):base(1)
        {
                Console.WriteLine(b);
        }
}
class MAIN  
{
        public static void Main()
        {
                B b_class = new B(2);
        }
}

OUTPUT:
1
2

... this is fine, but i want to initialize class A constructor with the same variable which was passed inside B
ie I want it like this

class B:A
{
        public B(int b)        
        {
               ** base(b);**
                Console.WriteLine(b);
        }
}

but this does not work :(
any way to initialize both class A and class B constructors with same values

---

### Post by PaulM1985 on 2012-09-23
I think you want:

```

class Derived : Parent
{
   Derived(int a) : base(a)
   {

   }
}

```

Paul

---

### Post by vikkyhacks on 2012-09-23
wow !!!, that was simple. Thanks, but is there any way to initialize with two difference variables 
  like ..

```

class parent:child
{
   public parent(int a):base(int b)
    {
         ... some code 
    }
}

```

---

### Post by vikkyhacks on 2012-10-01
figured it out myself !!!

```

using System;
class A
{
    public A(string a)
	{ Console.WriteLine(a); }
}
class B:A
{
    public B(string b,string a):base(a)
	{ Console.WriteLine(b); }
}
class MAIN
{
    public static void Main()
    {
      B classB =  new B("class b","class a");
    }
}

```

---

