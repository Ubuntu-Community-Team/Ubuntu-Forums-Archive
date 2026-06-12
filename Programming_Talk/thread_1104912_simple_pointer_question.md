---
title: "simple pointer question"
date: 2009-03-24
forum: Programming Talk
---

### Post by tneva82 on 2009-03-24
Let's assume I have following pointers created:

```
myPointers[4]=new myClass("object1");
myPointers[5]=new myClass("object2");
myPointers[6]=new myClass("object3");
```

Then I do following actions:

```
delete myPointers[6];
myPointers[6]=myPointers[5];
myPointers[5]=myPointers[4];
myPointers[4]=NULL;
```

Now what's the contents of each pointer? If it works like I think/hope it would be:

myPointers[4]=NULL
myPointers[5]=object1
myPointers[6]=object2

And object3 is no more there.

Ie does pointer1=pointer2 cause pointer 1 to point to pointer2(and from there where-ever pointer 2 points) or to object pointer 2 pointed at.

---

### Post by Tony Flury on 2009-03-24
> **tneva82 said:**
> Let's assume I have following pointers created:

```
myPointers[4]=new myClass("object1");
myPointers[5]=new myClass("object2");
myPointers[6]=new myClass("object3");
```

Then I do following actions:

```
delete myPointers[6];
myPointers[6]=myPointers[5];
myPointers[5]=myPointers[4];
myPointers[4]=NULL;
```

Now what's the contents of each pointer? If it works like I think/hope it would be:

myPointers[4]=NULL
myPointers[5]=object4
myPointers[6]=object2

And object3 is no more there.

Ie does pointer1=pointer2 cause pointer 1 to point to pointer2(and from there where-ever pointer 2 points) or to object pointer 2 pointed at.

Actually it would end up like ...
```

myPointers[4]=NULL
myPointers[5]=object1
myPointers[6]=object2

```
Not sure where object4 came from - but in general you are right (assuming you are talking about C (or C++)

---

### Post by tneva82 on 2009-03-24
> **Tony Flury said:**
> Not sure where object4 came from - but in general you are right (assuming you are talking about C (or C++)

Typo. That's where it came from ;-) I punched numbers from numpad(habit I have) and mispressed 4 instead of 1.

---

