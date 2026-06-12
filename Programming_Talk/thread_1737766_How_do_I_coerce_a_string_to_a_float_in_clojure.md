---
title: "How do I coerce a string to a float in clojure?"
date: 2011-04-23
forum: Programming Talk
---

### Post by josephellengar on 2011-04-23
I am making a struct here and I know that  (line 7) and (line 8) are floating-point values. But they are stored in string format. When I try to coerce like I did on (line 7) below, I get a runtime error:

```
Exception in thread "Thread-1" java.lang.RuntimeException: java.lang.RuntimeException: java.lang.ClassCastException: java.lang.String cannot be cast to java.lang.Number

```

This is the code: Any ideas?

```
location (struct storeinfo (line 0) (line 1) (line 2) (line 3) (line 4) (line 5) (line 6) (Float/parseFloat (line 7)) (line 8) (distance (ourLoc :lat) (ourLoc :long) (line 7) (line 8)))

```

---

### Post by brpylko on 2011-04-27
float yourFloat = Float.parseFloat(yourString); should work.

can you post your code with line breaks?

---

### Post by worseisworser on 2011-04-27
> **josephellengar said:**
> I am making a struct here and I know that  (line 7) and (line 8) are floating-point values. But they are stored in string format. When I try to coerce like I did on (line 7) below, I get a runtime error:

```
Exception in thread "Thread-1" java.lang.RuntimeException: java.lang.RuntimeException: java.lang.ClassCastException: java.lang.String cannot be cast to java.lang.Number

```

This is the code: Any ideas?

```
location (struct storeinfo (line 0) (line 1) (line 2) (line 3) (line 4) (line 5) (line 6) (Float/parseFloat (line 7)) (line 8) (distance (ourLoc :lat) (ourLoc :long) (line 7) (line 8)))

```

```

user=> (+ 0.5 (Float/parseFloat "41.5"))
42.0

```

---

