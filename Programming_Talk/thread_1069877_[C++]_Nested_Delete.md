---
title: "[C++] Nested Delete"
date: 2009-02-14
forum: Programming Talk
---

### Post by kjohansen on 2009-02-14
If i have:

[php]
class A
{ 
  int * list;
};

class B
{
  A* list_of_A;
};

....

int main(....)
{
...
B * b_list=new B[10];

b_list[0]->list_of_A=new A[10];

delete[] b_list;

...

}

[/php]


Does the delete cascade down, I mean will deleting the b list delete the children, or do I need to delete the children as well.

If I do need to delete the As separately would it be appropriate to do this in a destructor for B?

---

### Post by dwhitney67 on 2009-02-14
You need to define a destructor in your class B, that will delete the list of A's.
```

class B
{
  public:
    virtual ~B()
    {
      if (list_of_A)
        delete [] list_of_A;
    }

...
};

```

The destructor is declared as virtual in case you should ever subclass from class B.

If you plan to allocate in class A, I also recommend that you define a destructor.  It's pretty common to do so regardless of whether you allocate from the heap or not, so you might as well do it anyhow.

Btw, note that I used the keyword "public" in class B; you should too when posting examples, because by default, anything declared in a class is private.  Thus in your example, you would not have access to list_of_A as you have shown.

---

### Post by DougB1958 on 2009-02-14
As dwhitney67 pointed out, someone does need to delete the A's.

A rule of thumb I find useful for _who_ should delete things is "he who creates, deletes." You can't always follow this rule, but when you can it makes it easier to avoid bugs where one piece of code deletes something that another piece of code is still using. For example, consider the following code inspired by your original main:

[PHP]
int main(...) {
   B* b1 = new B;
   B* b2 = new B;
   A* someAs = new A[10];
   b1->list_of_A = someAs;
   b2->list_of_A = someAs;
   ...
   delete b1;
   ...
}
[/PHP]

If the destructor for B deletes the A's, you're in trouble: deleting b1 indirectly deleted the list of A's that b2 is still using.

I'm not necessarily saying that your destructor for B shouldn't delete the list of A's, but your code will be more robust if you coordinate the deletion and creation. If you want clients to provide the list of A's, like your original example suggested, then clients should delete the A's too. On the other hand, if you want the B destructor to delete the A's, then maybe the B constructor (or other B methods) should create them.

---

### Post by dwhitney67 on 2009-02-14
Consideration should also be given to using Boost's shared_ptr, or using the tr1 shared_ptr (which is basically the same!).  For example:

[php]
#include <tr1/memory>


class A
{
  public:
    A()
      : m_array(std::tr1::shared_ptr<int>(new int[10]))
    {
    }

    A(std::tr1::shared_ptr<int> array)
      : m_array(array)
    {
    }

    ~A()
    {
      // nothing to do!
    }

    std::tr1::shared_ptr<int> getArray() const
    {
      return m_array;
    }

  private:
    std::tr1::shared_ptr<int> m_array;
};

int main()
{
  A a1;
  A a2(a1.getArray());
}
[/php]

---

