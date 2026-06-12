---
title: "why am I getting error when trying to multiply by 2"
date: 2012-11-05
forum: Programming Talk
---

### Post by Mia_tech on 2012-11-05
I'm getting errors when trying to multiply by 2.

```
#!/bin/bash
#passing and returning arrays from functions

#calculating total sum
times_two() {
	local oarray=(`echo $@`)
	local newarray=(`echo $@`)
	for i in $@
	do
		newarray[$i]=$[ ${oarray[$i]} * 2 ]
	done
	echo ${newarray[@]}
}

array=(2 3 5 10 50)
total=(`times_two ${array[@]}`)

echo "The total times 2 is: ${total[@]}"
```

---

### Post by sisco311 on 2012-11-05
Because oarray[5], oarray[10] and oarray[50] are unset ;). 

```
for i in [COLOR="Red"]$@[/COLOR]
```

Instead of `command` you should use the POSIX form $(command). See BashFAQ 082.

$[ ... ] is an obsolate and deprecated syntax. Don't use it. Use $((...)) instead. See: [http://mywiki.wooledge.org/ArithmeticExpression](http://mywiki.wooledge.org/ArithmeticExpression)

---

### Post by Mia_tech on 2012-11-05
> **sisco311 said:**
> Because oarray[5], oarray[10] and oarray[50] are unset ;). 

```
for i in [COLOR="Red"]$@[/COLOR]
```

Instead of `command` you should use the POSIX form $(command). See BashFAQ 082.

$[ ... ] is an obsolate and deprecated syntax. Don't use it. Use $((...)) instead. See: [http://mywiki.wooledge.org/ArithmeticExpression](http://mywiki.wooledge.org/ArithmeticExpression)

yeah, the index in my array was wrong!... I changed it to this and worked
```
times_two() {
	local oarray=($(echo $@))
	local newarray=($(echo $@))
	i=0
	while [ $i -lt $# ]
	do
		newarray[$i]=$((${oarray[$i]} * 2))
		i=$((i + 1))
	done
	echo ${newarray[@]}
}
```

but I wanted to make it worked with a for loop... how would you do it with a for loop?

---

