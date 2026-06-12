---
title: "Terminology with object relationships"
date: 2015-01-27
forum: Programming Talk
---

### Post by pelle.k on 2015-01-27
Although i understand the relationship between **parent** and **child *classes***, i'm not quite sure about the relationship (the terminology that is) between an object created within another object.
To clarify with a bit of pseudo-code:
```

class ObjectA {
    // stuff
}

class ObjectB() {
    newobject = new ObjectA()
}  

```
It sure feels like the terminology would be apt here as well (even though it's not the same thing).
In UML diagrams [COLOR="#FF0000"]**newobject**[/COLOR] would be an an aggregate or composition.

In this discussion they do mention **child *object***; [http://programmers.stackexchange.com/questions/176049/what-is-the-use-of-association-aggregation-and-composition-encapsulation-in-c](http://programmers.stackexchange.com/questions/176049/what-is-the-use-of-association-aggregation-and-composition-encapsulation-in-c)
Would it then be correct to assume you could call **ObjectB** a **parent *object*** to [COLOR="#FF0000"]**newobject**[/COLOR]?
I'm not even sure if it's even meaningful to have names for the relationships between them.

---

### Post by ofnuts on 2015-01-27
newObject is just an atttribute of ObjectA. Ther is no special class relationship. newobject can be anything, a base type (int/float), some aggregate (array/struct).  And an object of the same type as newObject could also be an attribute in completely unrelated classes.

---

### Post by pelle.k on 2015-01-28
I saw another guy ask pretty much the same question here; [http://stackoverflow.com/questions/9786355/python-object-hierarchy-referencing-an-owner-instance](http://stackoverflow.com/questions/9786355/python-object-hierarchy-referencing-an-owner-instance), but he referred to an objects "owner" (what i speculated could be a parent object). Perhaps a more apt description, even though as you so kindly pointed  out there really isn't a word for it.
I guess i thought there was a special relationship between objects like that from doing GUI programming, specifically Qt, where most objects (widgets) you create have a "parent", and optionally more own "children" (widgets). I suppose it makes sense in that regard.
Anyway, thanks for clearing that up. :)

---

