---
title: "Java Opposite of Generics"
date: 2010-04-06
forum: Programming Talk
---

### Post by sharpdust on 2010-04-06
I am trying to extend the java.util.Hashtable class. However, I would like it so that when somebody tries to use my CustomHashtable class, they can only construct it use Strings for the types for the key/value pair.

Here is my code:

```
import java.util.Hashtable;

public class CustomHashtable <K, V> extends Hashtable
{
  public static void main(String [] args)
  {

    // Should be okay
    Hashtable myStringTable = new CustomHashtable();
    myStringTable.put("Entry 1", "Entry 2");
    System.out.println(myStringTable);

    // Not okay
    Hashtable myIntTable = new CustomHashtable();
    myIntTable.put(5, 6);
    System.out.println(myIntTable);
  }

}
```

So in the example, I want the first CustomHashtable construction to be okay, but for the second to not to be okay. 
I realize that in general, classes should be generic as possible, but in this case I want to force the programmer to only construct Hashtables with key/value pairs of type String.
In other words, I don't want any casting to be done in the main method. I was hoping there was a way to cast <K, V> to be something like <(String) K, (String) V>, but java doesn't like that.

Sorry if this is a simple question, I haven't done java programming in a long time.

---

### Post by Reiger on 2010-04-06
You should not extend the raw type Hashtable but rather a parametrised type:
```

public class CustomHashtable extends Hashtable<String,String>

```

You may want to read up on generics here: [http://java.sun.com/j2se/1.5/pdf/generics-tutorial.pdf](http://java.sun.com/j2se/1.5/pdf/generics-tutorial.pdf) (is a PDF file).

---

### Post by sharpdust on 2010-04-06
Thank you Reiger, that's exactly what I wanted.

---

### Post by Some Penguin on 2010-04-06
As a side note, if you don't need concurrency control at the level of the map you're going to be better off with HashMap instead of HashTable, and if you *do* need concurrency control at the level of the map you're still likely to be better off with ConcurrentHashMap.

More related, if you wanted to do something more flexible, Java does accept significantly more complicated syntax such as 

```

class Tree<V extends Serializable &  Comparable<V>>

```

---

