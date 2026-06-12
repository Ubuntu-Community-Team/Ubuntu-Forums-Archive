---
title: "Java ArrayList question"
date: 2010-04-08
forum: Programming Talk
---

### Post by kahumba on 2010-04-08
Hi,
when creating a new ArrayList with no arguments Java ensures an initial capacity of 10.
I don't want it to ensure any capacity, just to be non-null, so I do like "new ArrayList(0)", but, do you think Java obeys to it or **does Java (for some reason) default back to 10 if the initial capacity passed in the constructor is zero**?

---

### Post by falconindy on 2010-04-08
Well...

```
import java.util.ArrayList;

public class ALTest {
  public static void main(String[] args) {
    ArrayList al = new ArrayList(0);

    System.out.println(al.size());

  }
}
```

The real question is, why are you declaring an ArrayList with a size zero? Why not just allocate for the reference:

```
ArrayList al;
```

And then assign the reference to an object once you know how big the initial list needs to be:

```
al = new ArrayList(omgiknonao)
```

---

### Post by doas777 on 2010-04-08
Edit: The Anbu got there first. don't they always?

my guess is that you would get an exception, but couldn't tell you for sure.

why would you want a null arraylist? how would it be signifigantly differant from: ```
ArrayList<Object> al
``` and initialise the reference later once you know how many elements you need?

one last thought; java is not usually a very efficient language from a memory or operations perspective, so are you really saving any significant resources by not accepting the default?

---

### Post by kahumba on 2010-04-08
@[falconindy]("http://ubuntuforums.org/member.php?u=863375")
1) The size and the capacity are 2 different things.
2) As to why, not a big deal of course, I just want Java to allocate resources to it as needed because it's used very rarely in my app.

---

### Post by kahumba on 2010-04-08
> **doas777 said:**
> 
one last thought; java is not usually a very efficient language from a memory or operations perspective, so are you really saving any significant resources by not accepting the default?
Exactly, I'm was just curious whether it's possible. And yes, since I'm using _Java_ there's very little reason to do what I'm asking for, just curious.

---

### Post by doas777 on 2010-04-08
> **kahumba said:**
> @[falconindy]("http://ubuntuforums.org/member.php?u=863375")
1) The size and the capacity are 2 different things.
2) As to why, not a big deal of course, I just want Java to allocate resources to it as needed because it's used very rarely in my app.

try al.trimToSize(). it may cause an exception though if the size is 0 at the time you run it.
[http://java.sun.com/j2se/1.4.2/docs/api/java/util/ArrayList.html](http://java.sun.com/j2se/1.4.2/docs/api/java/util/ArrayList.html)

---

### Post by falconindy on 2010-04-08
> **kahumba said:**
> @[falconindy]("http://ubuntuforums.org/member.php?u=863375")
1) The size and the capacity are 2 different things.

Valid point. Serves me right for not checking the API.

Well, looking at the source of the ArrayList(int) constructor:

```
public ArrayList(int initialCapacity) {
  super();
  if (initialCapacity < 0)
    throw new IllegalArgumentException("Illegal Capacity: "+
                                               initialCapacity);
  this.elementData = new Object[initialCapacity];
}
```
Looks to me like it initializes an array of Objects with length zero. I'm a little surprised that this is valid, but sure enough it gets by the compiler and the JVM in a separate test. Not sure what this looks like in memory, but I assume it's nothing more than a reference.

edit: Looks like this is actually preferred behavior over a null array/list/set/etc. Java has [static methods in the Collections package](http://java.sun.com/javase/6/docs/api/java/util/Collections.html#emptyList()) to generate empty structures. Not quite the same as what you're looking for as these return immutables, but it's similar behavior.

---

### Post by Reiger on 2010-04-08
The reason those empties are useful is that you can still iterate over them (so it is safe to do for(Object o: array) {}).

ArrayList provides List with array-like performance (amortized performance, though). As a result of this design it is really a lot more memory efficient to declare the size of your collection if you know it in advance (the initial capacity of constructor).

---

### Post by kahumba on 2010-04-08
Thanks everybody

---

