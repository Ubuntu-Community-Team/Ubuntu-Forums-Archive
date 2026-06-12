---
title: "Java iterators"
date: 2009-10-21
forum: Programming Talk
---

### Post by swappo1 on 2009-10-21
Does Java have iterators for strings like C++?

---

### Post by Reiger on 2009-10-21
Not directly but a String can be converted to a char array which can be accessed using the for-each syntax:
```

public void test(String test) {
 for(Character c: test.toCharArray()) {
   System.out.println(c);
 }
}

```

---

### Post by Gwasanaethau on 2009-10-21
You could also do:
```
public void test(String test) {
 for(int i = 0; i < test.length(); i++) {
   System.out.println(test.charAt(i));
 }
}
```
Though I guess this does a conversion from a String to a char at every iteration of the for loop, where the previous example only converts once at the for loop's initialisation. However, I thought I'd add it nonetheless.

---

### Post by geirha on 2009-10-22
There's [http://java.sun.com/javase/6/docs/api/java/text/StringCharacterIterator.html](http://java.sun.com/javase/6/docs/api/java/text/StringCharacterIterator.html)

---

