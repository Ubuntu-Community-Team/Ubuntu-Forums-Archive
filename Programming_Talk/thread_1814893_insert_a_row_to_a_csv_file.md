---
title: "insert a row to a csv file"
date: 2011-07-30
forum: Programming Talk
---

### Post by naarkhoo on 2011-07-30
I have list, and would like to insert it as the last row, in a csv file.

> w=csv.writer(open('mycsvfile','a'),dialect='excel')
w.writerows(mylist)

and getting the following error,
> _csv.Error: Sequence expected,

apparently my csv is destroyed by csv.write:( !

---

### Post by Arndt on 2011-07-30
> **naarkhoo said:**
> I have list, and would like to insert it as the last row, in a csv file.



and getting the following error,


apparently my csv is destroyed by csv.write:( !

I don't know the rest of this interface, but when I tried it out just now, I drew the conclusion that writerows wants a list of lists, not one single list, which is logical considering the word "rows", not "row".

It may be useful to state that the language is python, also.

---

### Post by hakermania on 2011-07-30
> **Arndt said:**
> I don't know the rest of this interface, but when I tried it out just now, I drew the conclusion that writerows wants a list of lists, not one single list, which is logical considering the word "rows", not "row".

It may be useful to state that the language is python, also.

That's why we should support this also [Programming Talk Suggestion]("http://ubuntuforums.org/showthread.php?p=11091119#post11091119")

---

### Post by Bachstelze on 2011-07-30
[http://docs.python.org/library/csv.html#writer-objects](http://docs.python.org/library/csv.html#writer-objects)

The argument to writerows() must be a list, but it can be a list of a lot of things.

---

