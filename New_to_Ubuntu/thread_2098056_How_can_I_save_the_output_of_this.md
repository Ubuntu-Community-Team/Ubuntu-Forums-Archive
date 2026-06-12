---
title: "How can I save the output of this?"
date: 2012-12-25
forum: New to Ubuntu
---

### Post by cosmoshell on 2012-12-25
how can I save the output of 

cat somefile.txt | while read line; do x=`echo $line | awk '{print $1}'`; y=`echo $line | awk '{print $2}'`; echo `wc -l $x` $y ; done

I want everything I see from this or the first words into a text file and >>1.txt doesent work at the end.

---

### Post by sandyd on 2012-12-25
> **cosmoshell said:**
> how can I save the output of 

cat somefile.txt | while read line; do x=`echo $line | awk '{print $1}'`; y=`echo $line | awk '{print $2}'`; echo `wc -l $x` $y ; done

I want everything I see from this or the first words into a text file and >>1.txt doesent work at the end.

try
```

cat somefile.txt | while read line; do x=`echo $line | awk '{print $1}'`; y=`echo $line | awk '{print $2}'`; echo `wc -l $x` $y >> 1.txt ; done

```

---

### Post by cosmoshell on 2012-12-25
> **sandyd said:**
> try
```

cat somefile.txt | while read line; do x=`echo $line | awk '{print $1}'`; y=`echo $line | awk '{print $2}'`; echo `wc -l $x` $y >> 1.txt ; done

```

doesent work

this works but i want it doesent save to the same file withought it creating a tmp file. useing cp and rm.
cat somefile.txt | awk '{print $1}' >>  somefile.txt1

been at this for a hour...

---

