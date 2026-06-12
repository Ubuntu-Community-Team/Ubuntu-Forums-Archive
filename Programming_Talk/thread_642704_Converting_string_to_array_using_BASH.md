---
title: "Converting string to array using BASH?"
date: 2007-12-16
forum: Programming Talk
---

### Post by heavensCatacomb on 2007-12-16
I was wondering is there was any way to turn a string into an array such that the first letter would be array[0] etc using BASH?

---

### Post by maleficent on 2007-12-17
You can convert to an array:
```

s="foobar"
e=$(echo $s | sed 's/\(.\)/\1 /g')
a=($e)

echo "e = \"$e\""
echo "a[*] = \"${a[*]}\""
for i in $(seq 0 $((${#a[*]} - 1))); do
	echo "a[$i] = \"${a[$i]}\""
done

```
prints:
```

e = "f o o b a r "
a[*] = "f o o b a r"
a[0] = "f"
a[1] = "o"
a[2] = "o"
a[3] = "b"
a[4] = "a"
a[5] = "r"

```

or simply use single characters from the string:
```

s="foobar"

for i in $(seq 0 $((${#s} - 1))); do
	echo "s[$i] = \"${s:$i:1}\""
done

```
prints:
```

s[0] = "f"
s[1] = "o"
s[2] = "o"
s[3] = "b"
s[4] = "a"
s[5] = "r"

```

---

### Post by ghostdog74 on 2007-12-17
> **heavensCatacomb said:**
> I was wondering is there was any way to turn a string into an array such that the first letter would be array[0] etc using BASH?
if you just want to use the first letter, you can do substrings
```

# s="astring"
# echo ${s:0:1}
a

```

---

### Post by heavensCatacomb on 2007-12-17
> **maleficent said:**
> You can convert to an array:
```

s="foobar"
e=$(echo $s | sed 's/\(.\)/\1 /g')
a=($e)

echo "e = \"$e\""
echo "a[*] = \"${a[*]}\""
for i in $(seq 0 $((${#a[*]} - 1))); do
	echo "a[$i] = \"${a[$i]}\""
done

```


This should do nicely thank you.

As I am fairly new to shell scripting, could you possibly give me a quick rundown on what each part of the script does? Most specifically this part:

```
for i in $(seq 0 $((${#a[*]} - 1))); do
	echo "a[$i] = \"${a[$i]}\""
done

```

---

### Post by maleficent on 2007-12-20
${a[*]} refers to all elements in the array, ${#a[*]} is the count of all elements in the array, which, here, is 6, $((6 - 1)) is of course 5, and $(seq 0 5) outputs "0 1 2 3 4 5", then for each of these numbers as $i, the array element ${a[$i]} is echoed.

I think it's easier to use substrings, as both ghostdog and I mentioned though, ${variable:start:count} syntax. :)

edit: it's the 'a=($e)' line that actually creates the array. A static example without the string expansion would be:
```

a=(f o o b a r)

```

---

### Post by DouglasAWh on 2008-01-03
is there a substring like command for words (aka broken by spaces...though that could lead to problems I'll have to deal with...) rather than characters?

THANKS!

----------------------------------------------------------
**EDIT**: 
nevermind, I took another look at the static example and realized that was exactly what I was looking for....now, I just have to find a way to present that data in a webpage...

and before anybody says it, yes that is easier to do in PHP and I've already done it in PHP, I just want to learn bash by repeating it in bash.  My string is coming from a MySQL query, for anybody curious.

---

### Post by DouglasAWh on 2008-01-05
```
for i in $(seq 0 $((${#a[*]} - 1))); do
	echo "a[$i] = \"${a[$i]}\""
done

```

I can't seem to get the syntax right for an if statement after a for.  I do have a semicolon after the for statement.

---

### Post by Troula on 2009-06-01
> **maleficent said:**
> You can convert to an array:
```

s="foobar"
e=$(echo $s | sed 's/\(.\)/\1 /g')
a=($e)
 
echo "e = \"$e\""
echo "a
[*] = \"${a
[*]}\""
for i in $(seq 0 $((${#a
[*]} - 1))); do
    echo "a[$i] = \"${a[$i]}\""
done

```
prints:
```

e = "f o o b a r "
a
[*] = "f o o b a r"
a[0] = "f"
a[1] = "o"
a[2] = "o"
a[3] = "b"
a[4] = "a"
a[5] = "r"

```

 
Hi, I am new to linux and ubuntu. And I need some help.
Searching the web for an answer I found this forum. It really is helpful. But I have a problem.
I need to put a string to an array for a homework that I have, but I can not.
I tried this exactly as given, but it does not give me the same result.
It prints:
```

e = "f o o b a r "
a
[*] = "f o o b a r"
a[0] = "f o o b a r"

```
 
Please I really need help.. I don't understant what I do wrong.

---

### Post by grahamandchenine on 2011-02-07
This is a solution without using any external programs:

You get the length from ${#STRING} and access the characters using ${STRING:$COUNT:1} where $COUNT is your loop counter

for ((COUNT=0; COUNT<${#STRING}; COUNT++))
do
    RECORD[$COUNT]=${STRING:$COUNT:1}
done

echo $STRING
one two three

echo ${RECORD[0]}
o
echo ${RECORD[1]}
n
 . . .

---

### Post by Some Penguin on 2011-02-07
Why are you digging up a ~1.5-year-old thread?

---

### Post by hrimhari on 2011-10-27
Because he's proposing an alternate solution that may please other people with the same problem.

What about you? What are you contributing with your complaint?

---

