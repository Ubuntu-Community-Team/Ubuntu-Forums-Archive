---
title: "shell script- use arithmetic with case"
date: 2006-10-18
forum: Programming Talk
---

### Post by voltronguy on 2006-10-18
Hi All,
I'm learning how to write very basic shell scripts.  I understand the architecture of using case.  What I can't figure out is how use arithmetic arguments like you can use with if/then.

Here is what I am trying to do:
```
echo -n "How old are you? "
read age
case $age in
	26) echo "Same age" ; sleep 3s ;;
	**[<26]**) echo "Younger than me" ; sleep 3s ;;
	**[>26]**) echo "Older than me" ; sleep 3s ;;
	*) echo "no" ; sleep 3s ;;
esac
clear
```

Notice the bolded arguments.  How can I do something like that?  Or am I stuck with a straight equals or doesn't equal value?

Thanks for any help.

---

### Post by Arndt on 2006-10-18
> **voltronguy said:**
> Hi All,
I'm learning how to write very basic shell scripts.  I understand the architecture of using case.  What I can't figure out is how use arithmetic arguments like you can use with if/then.

Here is what I am trying to do:
```
echo -n "How old are you? "
read age
case $age in
	26) echo "Same age" ; sleep 3s ;;
	**[<26]**) echo "Younger than me" ; sleep 3s ;;
	**[>26]**) echo "Older than me" ; sleep 3s ;;
	*) echo "no" ; sleep 3s ;;
esac
clear
```

Notice the bolded arguments.  How can I do something like that?  Or am I stuck with a straight equals or doesn't equal value?

Thanks for any help.

With 'case', you can use matching expressions using '?' and '*', as in filename expansion, but that doesn't help with your arithmetic.

The command 'expr' can be used to compare values:

```
age=23
$ expr $age '<' 21
0
$ expr $age '<' 26
1
```

And so can the command 'test', which has a special syntax in the shell:

```
if [ $age '<' 26 ]; then
	echo less
elif [ $age '>' 26 ]; then
	echo more
else
	echo equal
fi
```

---

### Post by ghostdog74 on 2006-10-18
> **voltronguy said:**
> Hi All,
I'm learning how to write very basic shell scripts.  I understand the architecture of using case.  What I can't figure out is how use arithmetic arguments like you can use with if/then.

Here is what I am trying to do:
```
echo -n "How old are you? "
read age
case $age in
	26) echo "Same age" ; sleep 3s ;;
	**[<26]**) echo "Younger than me" ; sleep 3s ;;
	**[>26]**) echo "Older than me" ; sleep 3s ;;
	*) echo "no" ; sleep 3s ;;
esac
clear
```

Notice the bolded arguments.  How can I do something like that?  Or am I stuck with a straight equals or doesn't equal value?

Thanks for any help.

if you use if/then construct, you can check greater than using -gt or less than -lt ...

---

### Post by hillbilly on 2006-10-18
I dont thnk you can set a condition in the patterns of the case statement. You can only use wild cards. (e.g. "*6" and so on.)
If you need to set  something like less than or greater than, then you are better off using if-elif.

Or if you are still particular about using case, you could first capture the return value of the expression $age==26 and then use that return value as an argument to case. But then thats a round about way ;)

---

### Post by voltronguy on 2006-10-18
Thank you all for the replies.  The problem with the if/then was that I couldn't get it to handle non-numerical input.

```
echo -n "How old are you? "
	read age
	if [ "$age" = 26 ]; 
	then echo "We are the same age!" ; sleep 3s
		elif
***(Line 17)***	 [ "$age" -lt 26 ]; 
		then echo "You are younger than me." ; sleep 3s
***(Line 19)***			elif [ "$age" -gt 26 ];
			 then echo "You are older than me." ; sleep 3s
				else echo "You aren't human!" ; sleep 3s
        fi
```

The script works fine until you give it a letter as an input.  While it does give the correct output (echo "You aren't human"), it tosses out errors for the =,<,>26 tests where it was expecting a number.

```
./age: line 17: [: x: integer expression expected
./age: line 19: [: x: integer expression expected
You aren't human!
```



That's why I was hoping to use case, since the * could handle non-numerical input.

---

### Post by hillbilly on 2006-10-18
When you do numeric comparisions, you should use -eq for equal, -le for less than, -ge for greater than and so on. I dont recollect all the codes for comparision operators, but you could check out "man test" and you should be able to find it. 

==, <, > all work only for string comparisions.

NOTE: ghostdog74 had mentioned this in his post.


PLEASE disregard this post :( , was dreaming when i wrote this I guess !!

---

### Post by Arndt on 2006-10-18
> **voltronguy said:**
> 
The script works fine until you give it a letter as an input.  While it does give the correct output (echo "You aren't human"), it tosses out errors for the =,<,>26 tests where it was expecting a number.

```
./age: line 17: [: x: integer expression expected
./age: line 19: [: x: integer expression expected
You aren't human!
```

That's why I was hoping to use case, since the * could handle non-numerical input.

Use 'expr match' to first reject non-numbers:

```
$ expr match twenty '[0-9]*$'
0
$ expr match 26 '[0-9]*$'
2

```

---

### Post by voltronguy on 2006-10-18
Thanks for the suggestion.  I couldn't follow the syntax you were using, but I poked around till I got something to work.  First I have the script check for how many letters are in the age variable


```
echo -n "What is your age? "
read age
lettercheck=`expr $age : [[:alpha:]]*$`
```

Then if there are any letters I have the routine start over

```
if [ $lettercheck -gt 0 ]; then
	clear ; echo "Please enter a number only" ;
```

Now I just need to get a similar check for a blank entry and the script will be in good shape.

---

### Post by morgan_greywolf on 2006-10-18
You can also do this if you want something more case like.  This combines the arithmetic expression evaluation capabilities of bash/ksh with the if/elif/fi:

```
#!/bin/bash
echo -n "Enter your age: "
read age
if (( age <= 0 )); then
        echo "You are not human!"
elif (( age > 26 )); then
        echo "You are older than me!"
elif (( age < 26 )); then
        echo "You are younger than me!"
elif (( age == 26 )); then
        echo "Hey!  We're the same age!"
fi
```

---

### Post by Arndt on 2006-10-19
> **voltronguy said:**
> Thanks for the suggestion.  I couldn't follow the syntax you were using, but I poked around till I got something to work.  First I have the script check for how many letters are in the age variable


```
echo -n "What is your age? "
read age
lettercheck=`expr $age : [[:alpha:]]*$`
```

Then if there are any letters I have the routine start over

```
if [ $lettercheck -gt 0 ]; then
	clear ; echo "Please enter a number only" ;
```



I think your 'expr' call doesn't do what you want:

```
$ expr abc : [[:alpha:]]*$
3
$ expr abc6 : [[:alpha:]]*$
0
$ expr 66 : [[:alpha:]]*$
0
```

---

### Post by hillbilly on 2006-10-19
> **voltronguy said:**
> 
.
.
.
```
echo -n "What is your age? "
read age
lettercheck=`expr $age : [[:alpha:]]*$`
```

Then if there are any letters I have the routine start over

```
if [ $lettercheck -gt 0 ]; then
	clear ; echo "Please enter a number only" ;
```

Now I just need to get a similar check for a blank entry and the script will be in good shape.

Just a suggestion:
```
echo $age | grep [a-zA-Z]
echo $? ## Return code of the above command

```
would tell whether there are alphabets in your variable.

---

