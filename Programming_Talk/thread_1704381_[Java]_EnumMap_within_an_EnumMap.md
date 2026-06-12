---
title: "[Java] EnumMap within an EnumMap"
date: 2011-03-10
forum: Programming Talk
---

### Post by SpinningAround on 2011-03-10
I would like to create an EnunMap that contains another EnumMap, but compiler wont accept the code.
[PHP]EnumMap<Types,EnumMap<Keys,Integer>> enums = 
new EnumMap<Types,new EnumMap<Keys, Integer>(Keys.class)>(Types.class);[/PHP]

---

### Post by PaulM1985 on 2011-03-11
What error are you getting?

You can do this using the Map interface.

```

Map<Types, Map<Keys,Integer>> enums = 
new EnumMap<Types, Map<Keys, Integer>>(Types.class); 

// Assuming "SomeType" is in the "Types" enum
enums.put(SomeType, new EnumMap<Keys, Integer>(Keys.class));

```

This is untested, but I am pretty sure it will work.

Paul

---

### Post by PaulM1985 on 2011-03-11
Here is an example I have found in the Java documentation.

[http://download.oracle.com/javase/1.5.0/docs/guide/language/enums.html](http://download.oracle.com/javase/1.5.0/docs/guide/language/enums.html)

It is the second to last code example.

Paul

---

### Post by SpinningAround on 2011-03-11
Perfect, thanks :)

---

