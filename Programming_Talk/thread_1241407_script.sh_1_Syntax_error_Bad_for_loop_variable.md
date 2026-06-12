---
title: "script.sh: 1: Syntax error: Bad for loop variable"
date: 2009-08-15
forum: Programming Talk
---

### Post by colau on 2009-08-15
```
for (( i = 0; i <= 4; i++ ))
do
	echo $i
done

```

---

### Post by unutbu on 2009-08-15
/bin/sh is a symlink to dash, not bash.

```
(( ... )) 
```

is a bash-ism, not recognized by dash.

So try either 
[PHP]#!/bin/bash
for (( i = 0; i <= 4; i++ ))
do
	echo $i
done
[/PHP]

or[PHP]
#!/bin/sh

for i in $(seq 0 4)
do 
    echo $i
done
[/PHP]

---

### Post by ghostdog74 on 2009-08-15
```

for i in {0..4}
do
  echo $i
done

```

---

### Post by colau on 2009-08-15
[PHP]#!/bin/bash
for (( i = 0; i <= 4; i++ ))
do
	echo $i
done
[/PHP]
[PHP]
script.sh: 2: Syntax error: Bad for loop variable
[/PHP]

---

### Post by colau on 2009-08-15
> **ghostdog74 said:**
> ```

for i in {0..4}
do
  echo $i
done

```
Not trying to use "for i in" syntex ,but the "for (( ))" syntex.

---

### Post by colau on 2009-08-16
> **colau said:**
> [PHP]#!/bin/bash
for (( i = 0; i <= 4; i++ ))
do
	echo $i
done
[/PHP]
[PHP]
script.sh: 2: Syntax error: Bad for loop variable
[/PHP]
After ./script.sh 
```

0
1
2
3
4

```
After sh script.sh
[PHP]
script.sh: 2: Syntax error: Bad for loop variable
[/PHP]

---

### Post by colau on 2009-08-16
> **unutbu said:**
> /bin/sh is a symlink to dash, not bash.

```
(( ... )) 
```

is a bash-ism, not recognized by dash.

So try either 
[PHP]#!/bin/bash
for (( i = 0; i <= 4; i++ ))
do
	echo $i
done
[/PHP]

or[PHP]
#!/bin/sh

for i in $(seq 0 4)
do 
    echo $i
done
[/PHP]

Thank you.

---

