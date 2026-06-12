---
title: "Creating a bash shell in java. HELP!"
date: 2010-03-01
forum: Programming Talk
---

### Post by vik_2010 on 2010-03-01
[]

---

### Post by FreshP on 2010-03-01
As a general rule, when comparing strings use the method compareTo()

like
```
if(stringA.compareTo(stringB)==0)........
```

---

### Post by vik_2010 on 2010-03-01
wow my bad.. thank you. :)

---

### Post by Reiger on 2010-03-01
In general, if you want to compare objects for equality you use the equals() method:
```

String str1 = "a";
Object obj2 = new Object();
if(str1.equals(obj2)) {
  // this is never reached 
}

```

compareTo() is intended for sorting objects that implement the Comparable interface (hence the integer result).

---

### Post by myrtle1908 on 2010-03-01
> **FreshP said:**
> As a general rule, when comparing strings use the method compareTo()

like
```
if(stringA.compareTo(stringB)==0)........
```

The equals() method is better for this purpose.  compareTo() is useful for other reasons beyond the scope of the OPs question.

Also, the line (whilst incorrect)

```
input == "ls -l" || input == "ls" || input=="ls\n"
```

would be better served with a regular expression or if you just want to know if 'ls' is present then use indexOf().

---

