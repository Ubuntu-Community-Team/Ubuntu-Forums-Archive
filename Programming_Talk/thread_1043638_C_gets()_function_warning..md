---
title: "C: gets() function warning."
date: 2009-01-18
forum: Programming Talk
---

### Post by kapok on 2009-01-18
whats dangerous about the gets() function?

---

### Post by jimi_hendrix on 2009-01-18
buffer overflow...use fgets() instead

---

### Post by kapok on 2009-01-18
fgets() works the same way?

---

### Post by jimi_hendrix on 2009-01-18
```

myString = fgets(myString, sizeof(string), stdin);
/*takes a string, how many chars to read, and the file (in this case stdin for cli input) to read returns the value of the string you pass so i think what i have up  there is redundent*/

```

---

### Post by module0000 on 2009-01-18
Can ram as many characters into gets() input as you want, eventually writing to memory you have no business writing to.

---

