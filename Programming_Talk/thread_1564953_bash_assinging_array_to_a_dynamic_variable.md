---
title: "bash: assinging array to a dynamic variable"
date: 2010-08-31
forum: Programming Talk
---

### Post by PryGuy on 2010-08-31
Good day, everyone!

I have an array I want to assign to a dynamic variable. If I want to do it for a string - I do:```
#!/bin/bash

getVar() {
  eval $1="'$2'"
}

getVar FOO "bar"
echo $FOO
exit 0
```But it doesn't work out with arrays... Please help me! Thanks in advance!

---

### Post by amauk on 2010-08-31
you'll probably have to loop through all array items in $2, and assign each item to $1

---

### Post by PryGuy on 2010-08-31
Well, I have this idea also, but how do I call $1 in such case?
The constructs like```

&#1089;=0
for i in $2; do
  eval ${1[$c]}="'$i'"
  ((c++))
done
```
do not work... :(

---

### Post by PryGuy on 2010-08-31
Wow! This worked!
```

getVar() {
  c=0
  for i in $2; do
    eval $1[$c]="'$i'"
    ((c++))
  done
}

getVar FOO "1 2 3 4 5"
echo ${FOO[1]}
exit 0
```

---

### Post by ghostdog74 on 2010-08-31
```

declare -a FOO=(1 2 3 4 5)

```

---

