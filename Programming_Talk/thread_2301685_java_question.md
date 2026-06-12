---
title: "java question"
date: 2015-11-04
forum: Programming Talk
---

### Post by thisisbasil on 2015-11-04
I'm not a java person so this may have a simple answer, but I just don't know it.

I have an object that has multiple elements of the same naming format i.e. element0, element1, element2, etc

Right now, I am adding them to a an ArrayList in the following manner:

```

list.add(element0);
list.add(element1);
...

```

So on and so forth.

They are all of the same type but there are other elements that are also of the same type but not of the same naming convention (plus, I won't really be using them in the same manner). Is there any way to add these elements to the list in a looping manner? Something like:

```

for(int X=0; i<SIZE; X++)
    list.add(elementX);

```

I know how to get cute and do this type of thing in C-based languages but not in java. As it is, it looks really hacky and messy and I'd like to clean it up if at all possible.

---

### Post by PaulM1985 on 2015-11-06
Rather than naming your objects elementX when you create them, why not add them create them in an array:

SomeClass[] elements = new SomeClass[SIZE];

Then you could add to a list:
for(int X=0; i<SIZE; X++)
    list.add(elements[X]);

---

### Post by thisisbasil on 2015-11-10
Thanks for the reply. Unfortunately, this is not an option. To further clarify, I am delving into Java and Android programming at the same time. I have no way to do such a thing (to my knowledge) with the screen layout. I am trying to get an ArrayList of buttons. Its not a big deal, its just the way I'm doing it seems so ugly. Figured this might be a time where I can learn some non-beginner Java stuff.

---

### Post by Abderrahmen on 2015-11-18
You can't do that in JAVA.

---

