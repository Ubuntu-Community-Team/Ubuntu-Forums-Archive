---
title: "bash question"
date: 2009-10-15
forum: Programming Talk
---

### Post by epicoder on 2009-10-15
How do I loop COMMANDS X times in bash?

---

### Post by NoaHall on 2009-10-15
while [ a != x ]
do
let a=a+1
done

for x in numbers
do
done

---

### Post by roccivic on 2009-10-15
This command gets the job done every time:
```
man bash > bash-help.txt; gedit ./bash-help.txt; rm ./bash-help.txt
```

But for your specific query, try this:
```
#!/bin/bash
for (( i=0 ; $i<10 ; i++ )); do
  echo $i
done
```

Peace

---

