---
title: "CSV write python"
date: 2007-08-07
forum: Programming Talk
---

### Post by in_flu_ence on 2007-08-07
Hi,

I have the following code that I would like to write the result in the CSV format.

e.g
outcount=0
outresult=0

for i in range (1,11,1):
     outcount=outcount+1
     outresult=outresult*3+5

     outcount.append(outcount)
     outresult.append(outresult)

............................................................
Now I have these data in a list but I want these values not to be written in the csv format so that i can export it to excel for further processing. Any chance?

many thnks

---

### Post by pmasiar on 2007-08-07
```
nn = [1, 2, "hi", 3, "there"]
# repr()  adds quotes for strings
print ",".join(repr(x) for x in nn) 


```

---

