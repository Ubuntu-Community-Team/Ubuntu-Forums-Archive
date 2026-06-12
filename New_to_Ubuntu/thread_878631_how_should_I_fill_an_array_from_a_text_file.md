---
title: "how should I fill an array from a text file"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by just_linux on 2008-08-03
how should I fill an array from a text file?:popcorn:
OK I have a text file like here
[HTML]
1321
1231
21231
21321
2132
1
21321
21
2121
dr
wertwe
wertwer
wertwer
wert
wert
wert21
321wert
wer
[/HTML] :confused:
and I want to write a shell program that open the file and put all of them in an array fo I could use it during the program running: like here:
a[0]= 1321
a[1]= 1231
a[2]= 21231
...
...
...:lolflag:

Please help 
Thanks:guitar:

---

### Post by kaibob on 2008-08-03
Deleted by kaibob

---

### Post by sisco311 on 2008-08-03
```
i=0
for element in $(cat filename);
do
  arrayname[i]=$element
  let i+=1
done
let i-=1

for j in `seq 0 $i`; 
do
  echo ${arrayname[$j]
done
  
```

---

