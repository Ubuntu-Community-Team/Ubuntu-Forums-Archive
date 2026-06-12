---
title: "AWK - Print array - Pipe to sort - Print another line.  Not working."
date: 2017-08-02
forum: Programming Talk
---

### Post by joebeasley on 2017-08-02
I'm trying to print the contents of an array, followed by another line.  If I use the "|" for sort, the 'print Hello' line prints before the array.  If I add another 'print' below the hello, it prints that as well, then prints the array. 

I want to print the Array, then print "Hello".

```
#!/bin/sh

awk ' 
{ 

apple["bob"] = 34;
apple["tom"] = 89;
apple["bill"] = 89;
apple["suzan"] = 89;
apple["ashton"] = 89;

for (c in apple)
print c,apple[c] | "sort -n -k2" ;

print "Hello\n";
}'
```

---

### Post by joebeasley on 2017-08-02
Solution found.  

Add ...

close ("sort -n -k2");

after the print statement.

---

### Post by steeldriver on 2017-08-03
With GNU awk > 4.0 you can avoid the external sort process altogether by using PROCINFO to control the array traversal order directly:

```

gawk '
BEGIN {
apple["bob"] = 34;
apple["tom"] = 89;
apple["bill"] = 89;
apple["suzan"] = 89;
apple["ashton"] = 89;

PROCINFO["sorted_in"] = "@val_num_asc";
for (c in apple)
print c,apple[c];

print "Hello\n";
}'
bob 34
tom 89
ashton 89
bill 89
suzan 89
Hello


```

---

### Post by joebeasley on 2017-08-08
> **steeldriver said:**
> With GNU awk > 4.0 you can avoid the external sort process altogether by using PROCINFO to control the array traversal order directly:

```

gawk '
BEGIN {
apple["bob"] = 34;
apple["tom"] = 89;
apple["bill"] = 89;
apple["suzan"] = 89;
apple["ashton"] = 89;

PROCINFO["sorted_in"] = "@val_num_asc";
for (c in apple)
print c,apple[c];

print "Hello\n";
}'
bob 34
tom 89
ashton 89
bill 89
suzan 89
Hello


```

Yes, this does work as expected.  Thank you.

---

