---
title: "[AWK] compare two files"
date: 2011-12-01
forum: Programming Talk
---

### Post by llz80 on 2011-12-01
I have two files
file1:
query times attributes
q1 345 a1,a2
q2 547 a1,a4,a5
q5 967 a1

file2:
solution q1 q2 q3 q4 q5
s1 3425 1346 758 2245 928
s2 145 243 2983 1890 899
s3 333 209 1779 230 902

desire output:
query solution attributes
q1 s2 a1,a2
q2 s3 a1,a4,a5
q5 s2 a1

I want to select the solution with the least cost for each query in file1

Thanks for any help on this

---

### Post by Vaphell on 2011-12-01
```
#!/bin/bash

awk '
BEGIN {
  row=1
  while ( getline < "file2.txt" > 0 )
  {
    if( row==1 )      { col_id=$1; for( i=2; i<=NF; i++ ) q_id[i]=$i }
    else if( row==2 )
      for( i=2; i<=NF; i++ ) { s[q_id[i]]=$i; s_id[q_id[i]]=$1 }
    else
      for( i=2; i<=NF; i++ )
        if( $i<s[q_id[i]] ) { s_id[q_id[i]]=$1; s[q_id[i]]=$i }
    row++           
  }
}
{  print $1, (NR>1 ? s_id[$1] : col_id) , $3 } ' file1.txt
```
output
```
$ ./awk_qry.sh 
query solution attributes
q1 s2 a1,a2
q2 s3 a1,a4,a5
q5 s2 a1

```

---

### Post by llz80 on 2011-12-01
thank you so much,vaphell
but I can not understand what your code is doing in the while loop, can you please give me some comments on that?

---

### Post by sisco311 on 2011-12-02
Is this your homework?

---

### Post by llz80 on 2011-12-02
> **sisco311 said:**
> Is this your homework?

no, I am a database developer but my boss asked me to do some shell scripting work.

---

### Post by llz80 on 2011-12-02
Thanks all, I understand now

---

