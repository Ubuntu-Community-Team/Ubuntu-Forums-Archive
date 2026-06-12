---
title: "[ C++ ] char have no memory address ?"
date: 2010-03-03
forum: Programming Talk
---

### Post by [Re] Smile on 2010-03-03
```
Object #1 ( char ):        A&#65533;&#65533;7]&#65533;&#388;&#65533;&#65533;&#65533;
Object #2 ( string ):      0xbfebc458
Object #3 ( integer ):     0xbfebc454

```What I'm missing here ?

---

### Post by dwhitney67 on 2010-03-03
> **'[Re] Smile said:**
> 
What I'm missing here ?

The code that you used to display that data?

---

### Post by [Re] Smile on 2010-03-03
```
char object1 = 'A';
cout << "Object #1 ( char ): " << &object1 << endl;

string object2 = "A";
cout << "Object #2 ( string ): " << &object2 << endl;

int object3 = 0;
cout << "Object #3 ( integer ): " << &object3 << endl;

```

---

### Post by MadCow108 on 2010-03-03
cout << "Object #1 ( char ): " << &object1 << endl;\
here you pass a char* to the stream
the stream thinks its a cstring and tries to print it as it would a regular null terminated cstring
that fails as it has no null byte (-> it prints garbage after the char)

cast it to void* to get the pointer value

---

