---
title: "Compiling as a .deb?"
date: 2011-08-22
forum: Packaging and Compiling Programs
---

### Post by ThePerson on 2011-08-22
See the edit message for why this is empty.

---

### Post by Bachstelze on 2011-08-22
```
 25                 char input[7];
 26 
 27                 scanf( "%s",input );
```

Nice buffer overflow. :)

---

### Post by ThePerson on 2011-08-22
Well, it does only need to get 7 characters in. I could make it so you cannot have more than 7 or it says to many?

---

### Post by ThePerson on 2011-08-22
When compiled on my Ubuntu system it just ignores it, unless there is something I am midding?

---

### Post by cgroza on 2011-08-22
> **ThePerson said:**
> When compiled on my Ubuntu system it just ignores it, unless there is something I am midding?
Use fgets to avoid the possible overflow.

---

