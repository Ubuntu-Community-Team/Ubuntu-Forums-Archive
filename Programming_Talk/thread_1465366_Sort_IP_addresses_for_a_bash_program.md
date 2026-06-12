---
title: "Sort IP addresses for a bash program"
date: 2010-04-29
forum: Programming Talk
---

### Post by xbaez on 2010-04-29
Hello 
I have for example the following IP addresses:

24.172.220.218
41.239.36.19
63.215.202.234
66.176.124.22
78.110.50.139
79.143.179.98
83.4.136.214
84.111.37.26
163.24.136.10
187.40.64.252
187.41.94.232
24.172.220.218
187.45.225.192
189.10.91.21
190.77.158.128
193.34.144.193

How can I sort those IP addresses?
I want to sort them using the first 3 numbers

I also want to count the number of times that address is repeated

This is a batch program

Thanks a lot

---

### Post by gmargo on 2010-04-29
```

sort -n /tmp/ips.txt | uniq -c

```

---

### Post by stylishpants on 2010-04-29
The above solution sorts on only the first field of the dotted quad.  If you want the output sub-sorted on the other fields too, then you'll need to be fancier with sort, like so:

sort -n -t . -k 1,1 -k 2,2 -k 3,3 -k 4,4 

eg.
```
bob@cob:~$ sort -n /tmp/data1
1.2.3.4
1.22.3.4
1.9.3.4

bob@cob:~$ sort -n -t . -k 1,1 -k 2,2 -k 3,3 -k 4,4  /tmp/data1
1.2.3.4
1.9.3.4
1.22.3.4

```

The uniq -c part remains the same though.

---

