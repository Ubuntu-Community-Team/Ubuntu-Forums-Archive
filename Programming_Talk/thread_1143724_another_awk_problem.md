---
title: "another awk problem"
date: 2009-04-30
forum: Programming Talk
---

### Post by abraxas334 on 2009-04-30
So assuming i have 100 files named test.*.dat and * is between 1-100 and i want to extract $1 out of each of these files and put them into files called newTest.*.dat again with 1-100 for the star. I.e. that:

[PHP]
awk BEGIN'{print $1}' test.1.dat > newTest.1.dat 
[/PHP]

how can i automate that for 100 files?
Thanks for any help!

---

### Post by autopapa on 2009-04-30
Hi,

You can automate that in a for loop in your unix/linux shell.

Probably man sh (big manual page...)
for i in 1..100 do
awk BEGIN'{print $1}' test.$i.dat > newTest.$i.dat 
done

---

### Post by ghostdog74 on 2009-04-30
```

awk '{print $1}' test*dat > newfile

```

---

### Post by abraxas334 on 2009-04-30
> **ghostdog74 said:**
> ```

awk '{print $1}' test*dat > newfile

```

This will only copy them into 1 file unfortunately i have already tried that.

---

### Post by abraxas334 on 2009-04-30
> **autopapa said:**
> Hi,

You can automate that in a for loop in your unix/linux shell.

Probably man sh (big manual page...)
for i in 1..100 do
awk BEGIN'{print $1}' test.$i.dat > newTest.$i.dat 
done

mmm i tried that it doesn't seem to like me running in the for loop. I had a look at the manual and i don't really understand it...its very confusing this shell scripting!

---

### Post by ghostdog74 on 2009-04-30
```
awk '{gsub(/[a-zA-Z.]+/,"",FILENAME);print $1 > "newtest"FILENAME".dat"}' test*dat

```

---

### Post by abraxas334 on 2009-04-30
> **ghostdog74 said:**
> ```
awk '{gsub(/[a-zA-Z.]+/,"",FILENAME);print $1 > "newtest"FILENAME".dat"}' test*dat

```

Thanks so much that worked brilliantly and didn't take long at all on my huge files! :)

---

### Post by Arndt on 2009-04-30
> **ghostdog74 said:**
> ```

awk '{print $1}' test*dat > newfile

```

It's possible that the command line becomes too long if there are very many files, but if so, one can use 'find' and 'xargs'.

---

