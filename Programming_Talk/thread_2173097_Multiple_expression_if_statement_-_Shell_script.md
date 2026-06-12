---
title: "Multiple expression if statement - Shell script"
date: 2013-09-08
forum: Programming Talk
---

### Post by sathappan2 on 2013-09-08
Dear All,
       I Have value for the below 6 variables.

s1=${oparray['0']};
    s2=${oparray['1']};
    s3=${oparray['2']};
    s4=${oparray['3']};
    s5=${oparray['4']};
    s6=${oparray['5']};

I want to check the below condition, but i am getting the error message like **missing '] , binary operator expected, unexpected token `]' and [: too many arguments**

if [ [ "$s1" -eq "X" -and "$s2" -eq "$s1" -and "$s3" -eq "$s1" ] -or [ "$s4" -eq "X" -and "$s5" -eq "$s4" -and "$s6" -eq "$s4" ] ]
    then
        return 1
    else
        return 0
    fi

---

### Post by sisco311 on 2013-09-08
Hi and welcome to the forums!

Please check out BashFAQ 017 an d BashPitfalls 006 and 011 (links in my signature).

---

### Post by sathappan2 on 2013-09-08
unable to find solution for this. kindly suggest

---

### Post by sisco311 on 2013-09-08
What shell are you using? Are you trying to compare strings or integers?

BTW, you can learn more about the if statement here: [http://mywiki.wooledge.org/BashGuide/TestsAndConditionals#Conditional_Blocks_.28if.2C_test_and_.5B.5B.29](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals#Conditional_Blocks_.28if.2C_test_and_.5B.5B.29)

EDIT:

Thread moved to **Programming Talk**.

---

### Post by Vaphell on 2013-09-08
methinks you misunderstand the meaning of brackets. They are not a weird flavor of infinitely stackable parentheses that can be used to create something like [[[[]][[]][]]].
There is [ ] as one construct, and then there is [[ ]] which is kind of like an improved version of [ ] with more convenience features
In other words **[[ ... ] -or [ ... ]]** mixes both and thus doesn't make sense = syntax error

go with [  ... ] || [ ... ]
or [[ ... ]] || [[ ... ]],
or [ ... ] || [[ ... ]],
or [[ ... ]] || [ ... ]

---

### Post by prodigy_ on 2013-09-08
Also you need to use parentheses to combine expressions, not square brackets:
```
if ([ "$s1" -eq X ] && [ "$s2" -eq "$s1" ] && [ "$s3" -eq "$s1" ]) || \
   ([ "$s4" -eq Y ] && [ "$s5" -eq "$s4" ] && [ "$s6" -eq "$s1" ]); then
	return 1
else
	return 0
fi
```

---

### Post by bluefrog on 2013-09-08
wondering if the following is correct. (it works on my computer, doesn't mean it's well written)

**corrections made after reading next reply by prodigy...**

```
#!/bin/bash

# find out if the first 3 values, or the last 3 values, of array1
# are equal to the value of input

echo -n "Enter the array values: "; read array1
array1=($array1)

echo -n "Enter the value to compare: "; read input
array2=($input $input $input)

for i in {0..2}
	do
		array3+=(${array1[$i]})
	done
	
if [[ ${array3[*]} == ${array2[*]} ]]; then
	return 0
else
	unset array3
	for i in {3..5}
		do
			array3+=(${array1[$i]})
		done

	if [[ ${array3[*]} == ${array2[*]} ]]; then
		return 0
	else
		return 1
	fi
fi
}

testarray
echo "returned value = $?"

```

---

### Post by prodigy_ on 2013-09-08
If it works, it's correct but if you're going to use it in an actual script, using variable names like $a is a bad idea. And constructs like **c[${#c[*]}]** are simply unreadable.

There's an old joke about Perl: *You write some code that works and nobody but you can understand how it works. In 6 months you don't get it either.* I'd say you achieved the same effect with bash. :)

---

