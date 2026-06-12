---
title: "How can I loop for specific i values in JAVA2;;"
date: 2008-06-19
forum: Programming Talk
---

### Post by theodorekon on 2008-06-19
I want to build a for-loop but I want to run the loop for specific values of i. For example if I was using a script language I would create a list with the values I wanted and then I would use the command:

```
for (i in list) do
```
Is there something similar in Java??

---

### Post by jespdj on 2008-06-19
I don't know what you mean with "run the loop for specific values of i". Ofcourse Java supports for-loops:
```
List<Integer> numbers = ...; // wherever you get this from

for (int i : numbers) {
    System.out.println(i);
}
```

---

### Post by theodorekon on 2008-06-19
That's what I wanted, thanks!!

---

