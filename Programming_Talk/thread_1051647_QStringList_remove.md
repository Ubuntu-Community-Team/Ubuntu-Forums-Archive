---
title: "QStringList remove?????"
date: 2009-01-26
forum: Programming Talk
---

### Post by dschu012 on 2009-01-26
I am trying to remove an item from a QStringList. According to the API it inherits from QValueList ([http://doc.trolltech.com/3.3/qvaluelist.html](http://doc.trolltech.com/3.3/qvaluelist.html)).

I was thinking I should just be able to do remove and provide the QString as the arguments but it doesn't seem to be so.
```

foreach(QString s, list)
if(s.contains(word))
list.remove(word);

```

The debugger reports "‘class QStringList’ has no member named ‘remove’"

---

### Post by Zugzwang on 2009-01-27
> **dschu012 said:**
> 
The debugger reports "‘class QStringList’ has no member named ‘remove’"

This is unlikely. It's more likely that the compiler reports this. Anyway, are you sure that you are building your application/library/whatever with QT 3.3? In QT4, there are different functions for doing what you want and indeed, there's no "remove" because they have "removeOne" and "removeAll". 

If you are sure to build against QT 3.3, please provide us with a minimal example we can use for trying to compile.

---

### Post by dschu012 on 2009-01-27
Well its my first time working with Qt. It is for class at school and is Qt4 and the API I was looking at seemed tobe for Qt3. I just needed to use removeAt() instead of remove(). The auto completion QDevelop doesn't seem to help much.

---

### Post by happysmileman on 2009-01-27
I would do something like:
```

for (int i=0; i < list.size(); ++i) {
    if (list.at(i).contains(word))
        list.remove(i);
}
```

The way OP shows doesn't really make sense to me, it checks if each string contains word (presumably a QString), and then calls remove(word), which won't work, remove() needs the id of the String.

Haven't actually tested code above, just going on memory and giving general idea of what i'd do.

---

### Post by Zugzwang on 2009-01-28
> **happysmileman said:**
> 
Haven't actually tested code above, just going on memory and giving general idea of what i'd do.

Well, the OP was concerned about QStringList containers, which do not have the "remove" method in QT4. Your example seems to be for STL.

---

