---
title: "RegEx in sed"
date: 2013-08-28
forum: Programming Talk
---

### Post by pqwoerituytrueiwoq on 2013-08-28
In Javascript i would do it like this
```
'model name    : AMD Phenom(tm) II X4 965 Processor'.replace(/(^.*: | [Pp]rocessor|\([Tt][Mm]\))/g,'')
```
but sed's RegEx does not work the same, so i have been doing it with separate RegEx like this
```
cat /proc/cpuinfo |grep 'model name'|head -1|sed 's/^.*: //g;s/ [Pp]rocessor//;s/(\([Tt][Mm]\))//'
```
is there a more efficient way to write the sed part like i did in Javascript?

---

### Post by Vaphell on 2013-08-28
```
$ sed -rn '/model name/ { s/^.*:\s*|\([tT][mM]\)|\s*[pP]rocessor//gp; q}' /proc/cpuinfo
AMD Phenom II X4 955 
```

---

### Post by pqwoerituytrueiwoq on 2013-08-28
thanks

---

