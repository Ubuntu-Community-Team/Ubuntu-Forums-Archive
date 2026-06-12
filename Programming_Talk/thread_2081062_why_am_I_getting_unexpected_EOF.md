---
title: "why am I getting unexpected EOF"
date: 2012-11-05
forum: Programming Talk
---

### Post by Mia_tech on 2012-11-05
I'm getting unexpected eof, but I don't see the error
```
#!/bin/bash
#passing and returning arrays from functions

#calculating total sum
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

#sort array
sort_array() {
	local arr=($(echo $@))
	local size=$(($# - 1))
	i=0
	while [ $i -lt $size ]
	do
		j=1
		while [ $j -lt $# ]
		do
			local temp=0			
			if [ ${arr[$i]} -gt ${arr[j] ]; then
				temp=${arr[$i]}
				arr[$i]=${arr[$j]}
				arr[$j]=$temp
			fi
			j=$(($j + 1))
		done
		i=$(($i + 1))
	done
	echo ${arr[@]}
}				

array=(2 3 5 10 50)
total=($(times_two ${array[@]}))

array2=($(sort_array ${array[@]}))

echo "The total times 2 is: ${total[@]}"
echo "The array sorted: ${arra2[@]}"

```

---

### Post by drmrgd on 2012-11-05
Have a look at this line here:

```
if [ ${arr[$i]} -gt ${arr[j] ]; then
```

I think you're missing a closing brace:

```
if [ ${arr[$i]} -gt ${arr[j]} ]; then
```

EDIT: also noticed another problem.  You've got a typo in the last line of the script.  I think it should be:

```
echo "The array sorted: ${array[@]}"
```

---

