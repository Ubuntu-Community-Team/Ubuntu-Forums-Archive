---
title: "n00b query on regex; how do you search for ."
date: 2011-03-08
forum: Programming Talk
---

### Post by tarahmarie on 2011-03-08
The dot is a wildcard character, but what if I want to search for a string that contains a dot? Here's an example:

java.awt.dnd

I am new at regex, so when I would previously search for java.awt, I would search for *.awt, because it would at least match what I wanted. Now, I am dealing with bigger docs, and I need to search for java.awt and exclude java.awt.dnd. I am not sure what to do about the dots, since now I will need to include them in the regex, but they represent wildcard characters. I've been going through tutorials like this one: [http://www.regular-expressions.info/quickstart.html](http://www.regular-expressions.info/quickstart.html) but no joy.

---

### Post by tarahmarie on 2011-03-08
> **tarahmarie said:**
> The dot is a wildcard character, but what if I want to search for a string that contains a dot? Here's an example:

java.awt.dnd

I am new at regex, so when I would previously search for java.awt, I would search for *.awt, because it would at least match what I wanted. Now, I am dealing with bigger docs, and I need to search for java.awt and exclude java.awt.dnd. I am not sure what to do about the dots, since now I will need to include them in the regex, but they represent wildcard characters. I've been going through tutorials like this one: [http://www.regular-expressions.info/quickstart.html](http://www.regular-expressions.info/quickstart.html) but no joy.

Hah! I found that a backslash escapes one of the meaningful characters. Thanks anyway!

---

### Post by myrtle1908 on 2011-03-08
Find all java.awt not followed by .dnd ...

```
(java\.awt(?!\.dnd))
```

You could take it step further if you care about other packages eg. java.awt.abc.  Here's an example in javascript

```
var s = 'java.awt,java.awt.abc.def,java.awt.dnd,java.awt.dnd.abc';
var m = s.match(/(java\.awt(?!\.dnd).*?(?=,|$))/g);
console.debug(m); // in firebug or chrome dev console
```

Yields ....

```
["java.awt", "java.awt.abc.def"]
```

---

