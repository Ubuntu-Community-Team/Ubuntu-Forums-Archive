---
title: "Java string question"
date: 2009-03-14
forum: Programming Talk
---

### Post by g3k0 on 2009-03-14
Hey,
I am setting a string in java equal to  another string.  However, it seems to be only changing the reference.

I have two objects of the same type. Each have a string called *name*.
I have a replace function that does this

```
public void replace(String newName){
  this.name = newName;
}
```

If I call it, both objects *name* are changed to that value.  How do I make it copy a string instead of the reference?  I only want the one to change.

---

### Post by kjohansen on 2009-03-14
in java strings are immutable, thus you always change the reference not the value.  but your function should set the reference of only one of the instances not both, so I dont think the problem is in the function you showed...

---

### Post by myrtle1908 on 2009-03-14
*this* refers to the current class instance, so when you write 

[PHP]this.name = newName;[/PHP]

you are setting the class level variable named 'name' to the variable 'newName' thus any subsequent accesses to this.name will reflect the change.

You probably want to localise the name variable to the replace method or maintain two class level variables.

---

### Post by g3k0 on 2009-03-14
sorry.  Perhaps I was unclear with the post.  I just want the two objects to have different values for the strings that they have declared within them.
```

Class Example{
  Private String name;
  public void replace(String newName){
  this.name=newName;
  }
}

```

When I pass a string to both objects for some reason they always have the same value.  I can't figure out why...

so if I pass in "fred" to one object it is fred
then if I pass "steve" to the other object they are both steve!

---

### Post by eye208 on 2009-03-14
> **g3k0 said:**
> When I pass a string to both objects for some reason they always have the same value.  I can't figure out why...

so if I pass in "fred" to one object it is fred
then if I pass "steve" to the other object they are both steve!
I guess you did something like this:
```
Example a = new Example();
Example b = a;
a.replace("fred");
b.replace("steve");
```
a and b are not independent copies but refer to the same instance of the Example class. To make independent copies, you have to implement the Cloneable interface, add a public clone() method, and use that to make the copy like this:
```
Example b = a.clone();
```

---

### Post by g3k0 on 2009-03-14
Thats not exactly what I did, but you showed me what the problem was (the object had same ref).  I was doing something.push(new object(new object1(Object2.atype))) and object2 had the string in it I was trying to change.  I was thinking it was the string I was passing not the object itself...

Thanks for the help

---

