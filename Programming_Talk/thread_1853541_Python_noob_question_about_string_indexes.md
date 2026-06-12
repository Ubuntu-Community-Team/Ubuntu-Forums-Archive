---
title: "Python: noob question about string indexes"
date: 2011-10-02
forum: Programming Talk
---

### Post by NoJobyDesert on 2011-10-02
Is putting a variable in for the index of a string legal?

that is, if ```
my_str = "Hello World"
``` then ```
print my_str[1] 
``` return 'e'.

but if I try this:
```
index = 1
print my_str[index]
```

I get this error:
```
IndexError: string index out of range
```

Is there some other way of using a variable for a given string index?

---

### Post by Arndt on 2011-10-02
> **NoJobyDesert said:**
> Is putting a variable in for the index of a string legal?

that is, if ```
my_str = "Hello World"
``` then ```
print my_str[1] 
``` return 'e'.

but if I try this:
```
index = 1
print my_str[index]
```

I get this error:
```
IndexError: string index out of range
```

Is there some other way of using a variable for a given string index?

Using variables as indices works perfectly well, so your original idea is correct. I can't say why you get an error - can you post a complete program that does this?

---

### Post by KdotJ on 2011-10-02
Using the code you posted above, works perfectly well... In your program, tha variable must at some point become greater than the length of the string before you use it as an index... Or, the string changes to something else (eg, to a single character assuming the code you posted)

---

### Post by simeon87 on 2011-10-02
That error will only occur when my_str has one or less characters.

---

### Post by NoJobyDesert on 2011-10-02
Thanks all for the help.

Yes, this code was part of a loop, and the variable did in fact become higher than the length of the string at some point.

---

