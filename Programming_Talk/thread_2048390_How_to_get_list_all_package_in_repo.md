---
title: "How to get list all package in repo"
date: 2012-08-26
forum: Programming Talk
---

### Post by tienlbhoc on 2012-08-26
I can get list by:
apt-get install <tab><tab>
and 
```
tienlbhoc@tienlbhoc-K40IJ:~/Desktop$ apt-get install 
Display all 38385 possibilities? (y or n)

```
I want to get list of all 38385 package to make 38385 file with content hello (content i will change later)
How to code this with shell ?

---

### Post by Vaphell on 2012-08-26
possible ways to get the list
```
apt-cache pkgnames
apt-cache dumpavail | awk '/Package:/{ print $2 }'
```
these two give different number of results on my system though

to create <package-name>.txt and put Hello in it for all results
```
while read pkg; do echo "Hello" > $pkg.txt; done < <( apt-cache pkgnames )
```

---

