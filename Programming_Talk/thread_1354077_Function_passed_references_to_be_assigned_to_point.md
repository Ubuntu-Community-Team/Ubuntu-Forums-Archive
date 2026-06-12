---
title: "Function passed references to be assigned to pointers"
date: 2009-12-13
forum: Programming Talk
---

### Post by Ultros88 on 2009-12-13
Hello, I have something very roughly like this - it should be enough to clarify what my problem is:

```
class String
{
private:
Node* _n1, _n2;
}
```

This is just a link between two locations in space. I need to be able to change the properties of the nodes and have that propagate to all the attached springs.

So, I'm trying to assign the pointers to the nodes in the constructor like this:

```
String::String(const Node& n1, const Node& n2)
{
_n1 = n1; //line 3
_n2 = n2;
}
```

However, the compiler is giving me an
error: cannot convert ‘const Node’ to ‘Node*’ in assignment

How do I work out this issue?

---

### Post by CptPicard on 2009-12-13
A reference is not a pointer. You need to take the address of the referenced items:

```

String::String(const Node& n1, const Node& n2)
{
_n1 = &n1;
_n2 = &n2;
}

```

---

### Post by Ultros88 on 2009-12-13
Now the compiler is telling me
error: invalid conversion from ‘const Node*’ to ‘Node*’

---

### Post by CptPicard on 2009-12-13
Well, take off consts in the parameters as an easy way out :)

---

### Post by Ultros88 on 2009-12-13
Okay, thanks it works now.

---

### Post by dwhitney67 on 2009-12-13
> **CptPicard said:**
> Well, take off consts in the parameters as an easy way out :)

Cpt... you've been demoted to ship's steward.  :-)

It's obvious the OP doesn't know the difference between a pointer and a reference.  Maybe he wanted to copy the contents of the object, instead of assuming ownership of the pointer?

Either way, you are probably correct; the OP seems happy.

---

### Post by LKjell on 2009-12-13
About the ownership and copy content. Is there a way to duplicate the content that the pointer is pointing too, with out accessing each element? For example duplicate a struct?

---

### Post by CptPicard on 2009-12-13
> **dwhitney67 said:**
> Cpt... you've been demoted to ship's steward.  :-)

Hey, at least I did not suggest that he might want to be using Python instead... ;) (although these kinds of "noob gets tripped up by relatively unnecessary problem of pointer/reference distinction" matters are ofc ever so typical)

> 
It's obvious the OP doesn't know the difference between a pointer and a reference.  Maybe he wanted to copy the contents of the object, instead of assuming ownership of the pointer?

True. Although he has got pointer data members, so I'm assuming that's what he wants -- to have something that points to these things. Doing an assignment on Node values will probably blow up his Nodes (wanna bet they aren't safe in that regard), and I was just considering whether I should mention reference members and initialization lists... :)

---

### Post by dwhitney67 on 2009-12-13
> **LKjell said:**
> About the ownership and copy content. Is there a way to duplicate the content that the pointer is pointing too, with out accessing each element? For example duplicate a struct?

Define/implement a copy-constructor that performs a deep copy of each element.
```

class Foo
{
public:
   Foo(int value = 0, SomeObject* obj = 0)
      : _value(value), _obj(obj)
   {
   }

   // Foo's copy-constructor
   Foo(const Foo& other)
      : _value(other._value),
        //_obj(other._obj)     // we don't want this!
        _obj(0)                // this is ok
   {
      if (other._obj)
      {
         _obj = new SomeObject(*other._obj);  // call SomeObject's copy-constructor
      }
   }

   ...

private:
   int         _value;
   SomeObject* _obj;
};

```

P.S.  An easier alternative, but which adds an external dependency to the code, is to use either the TR1 or Boost's shared_ptr container.

---

