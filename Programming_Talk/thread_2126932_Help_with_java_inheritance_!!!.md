---
title: "Help with java inheritance !!!"
date: 2013-03-18
forum: Programming Talk
---

### Post by vikkyhacks on 2013-03-18
```
class A { int a = 10; }
class B extends A { int a = 20; }


class C {
	
	public static void main(String[] args) {
		A a = new B(); // why does this work ??
		B b = new A(); // why does this not ??
	}
	
}

```

I just can't understand why 

BASE_CLASS <var_name> = new DERIVED_CLASS (will work)
DERIVED_CLASS <var_name> = new BASE_CLASS (will not work)

HELP !!!!!!!

---

### Post by diesch on 2013-03-18
If *b* is a variable of Type *B* it needs to ysupport all the operations that type *B* supports. This is only guaranted if its value is an instance of *B* or one of its subclasses, so you'll get a compile time error if you try to assign a value to *b* that is not such an instance.

It may be more obvious if you define *B* as 

```
class B extends A { int b = 20; }
```

Then if *b* is of type *B* it has to have the class variables *a* (inherited from *A*) and *b*. 
As doesn't have *b* if it is an instance of *A* it is not allowed to be such an instance.

---

### Post by slickymaster on 2013-03-18
Java Inheritance defines an is-a relationship between a superclass and its subclasses. This means that an object of a subclass can be used wherever an object of the superclass can be used. The inheritance relationship is transitive: if class x extends class y, then a class z, which extends class x, will also inherit from class y.

---

### Post by Vaphell on 2013-03-18
to visualize the problem better
```
class HasFourLegs {} // base class
class Dog extends HasFourLegs { <dog stuff> }
class Table extends HasFourLegs { <furniture stuff> }

HasFourLegs a = new Dog(); // makes sense
Dog b = new HasFourLegs(); // doesn't make sense, especially because it would also mean that Dog is compatible with Table
```

in other words inheritance is a one way street. Every DerivedClass object is of BaseClass type at the same time, but not every object under the umbrella of BaseClass belongs to DerivedClass

---

