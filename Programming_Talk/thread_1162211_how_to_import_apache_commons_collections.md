---
title: "how to import apache commons collections"
date: 2009-05-17
forum: Programming Talk
---

### Post by r.stiltskin on 2009-05-17
I've installed libcommons-collections3-java and libcommons-collections-java but can't work out how to use them.

I'm trying to use PriorityBuffer with
```
import org.apache.commons.collections.buffer.PriorityBuffer;
```
and compiling with the command line:
```
javac BufferTest.java
```
but apparently there's more to it than that -- I'm getting "cannot find symbol" errors referring to PriorityBuffer.

As you can see, my familiarity with Java is pretty limited. What am I missing?

---

### Post by r.stiltskin on 2009-05-17
For anyone faced with the same or a similar question, the import line shown above was correct. 

The solution is to compile with the following:
```
javac -classpath /usr/share/java/commons-collections3.jar BufferTest.java
```

---

