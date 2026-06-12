---
title: "line 4: [ too many arguments"
date: 2019-06-16
forum: Programming Talk
---

### Post by sathvik1 on 2019-06-16
Hi,
Below is my program which is giving me an error "line 4: [ too many arguments "
Can you please help me with this?

```
a=0

while [ $a =lt 10 ]
do
    echo $a
    a='expr $a + 1'
done
```

---

### Post by again? on 2019-06-16
```
a=0

while [ "$a" -le "10" ]
do
	echo $a
	a=$(( $a + 1 ))
	sleep 0.5
done
```
I put in half a second sleep command so you can see it looping.
[http://tldp.org/LDP/abs/html/comparison-ops.html](http://tldp.org/LDP/abs/html/comparison-ops.html)

---

### Post by sathvik1 on 2019-06-16
Thanks it worked. Link was helpful.

---

