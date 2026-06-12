---
title: "problem with script"
date: 2012-04-16
forum: Programming Talk
---

### Post by Blackbug on 2012-04-16
hello i want an script which calculates number of lines from a file, and calculates in how many multiples of 128 lines are present.
Then for each set of 128 lines it writes output to a different file.

I have to do this because of the limitation of PS command in AIX. ps command in AIX displays only 128 resultset.

The code is not working and just a rough idea.

```

line=`wc -l $filename`
count=`expr $line / 128`
echo $count
num=0
while [ $count > 0 ]
do
i=1


num=`expr $i * 128`

head -$num $filename >$outputfile.$i
tail +$num+1 $filename > $outputfile.$i+1

i=`expr $i + 1`
count=`expr $count - 1`
done

```

I hope anyone can help on this.

---

### Post by CynicRus on 2012-04-16
```

for i in $(seq $line); do
  [ $(($i%128)) -eq 0 ] && echo -n "multiples 128"

```

---

### Post by CaptainMark on 2012-04-16
have you tried the split command, check out man split for info

---

### Post by codemaniac on 2012-04-16
Could be achieved by a simple awk one liner .
The below would count lines that are multiple of 128 .
```
awk 'NR%128 == 0{print}' input_data_file | wc -l
```

---

