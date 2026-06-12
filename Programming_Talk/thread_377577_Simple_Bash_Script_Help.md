---
title: "Simple Bash Script Help"
date: 2007-03-06
forum: Programming Talk
---

### Post by k_smolka on 2007-03-06
Hi All

I am currently trying to write a quick and dirty script to run a number of files and record the output but I am having problems with the bash syntax.


```


index=0

echo "Running Test File 6"
./a.out < data/6
a=`./a.out < data/6`

if (($a == "TestPassed"))
then
        echo Yes
        $index=($index + 1)
fi

```

The problems seems to be with updating the integer if the if statement is true. I have copied a number of example off the next but non seem to help.

I just get an error saying Test no found.

Regards 

Karl

---

### Post by k_smolka on 2007-03-06
Hi All

I am currently trying to write a quick and dirty script to run a number of files and record the output but I am having problems with the bash syntax.


```


index=0

echo "Running Test File 6"
./a.out < data/6
a=`./a.out < data/6`

if (($a == "TestPassed"))
then
        echo Yes
        $index=($index + 1)
fi

```

The problems seems to be with updating the integer if the if statement is true. I have copied a number of example off the next but non seem to help.

I just get an error saying Test no found.

Regards 

Karl

---

### Post by k_smolka on 2007-03-06
Hi All

I am currently trying to write a quick and dirty script to run a number of files and record the output but I am having problems with the bash syntax.


```


index=0

echo "Running Test File 6"
./a.out < data/6
a=`./a.out < data/6`

if (($a == "TestPassed"))
then
        echo Yes
        $index=($index + 1)
fi

```

The problems seems to be with updating the integer if the if statement is true. I have copied a number of example off the next but non seem to help.

I just get an error saying Test no found.

Regards 

Karl

---

### Post by LotsOfPhil on 2007-03-06
index=$(($index+1))

---

### Post by k_smolka on 2007-03-06
```

# Find out how many tests passed
X="Test Passed"
index=0

if [ "$a" -eq "$X" ]; then
        index=$(($index+1))
        echo $index
fi

# Print out the info

echo $a
echo $index

```

Give the output: testHarness.sh: syntax error at line 41: `index=$' unexpected

Would running this on a solaris machine make any difference ? 

Kind regards 

Karl

---

### Post by LotsOfPhil on 2007-03-06
Hmm. When I ran this little snippet I got this error: "./help: line 28: [: Phil: integer expression expected"

You need two brackets:

```

#!/bin/bash
index=0
index=$(($index+1))
echo $index
 
index=0
a="Phil"
X="Phil"
 
if [[ "$a" -eq "$X" ]]; then
        index=$(($index+1))
        echo $index
fi

```

I don't think Solaris should make any difference. Bash is bash, I think. I'm testing on Red Hat.

---

### Post by Ramses de Norre on 2007-03-06
You just made me notice something strange, when you do this in bash:
```
index=1
index+=1
```
The contents of index is 11??
Why isn't it 2 like in any other programming or scripting language?

---

### Post by s1ightcrazed on 2007-03-06
Because bash treats everything as a string, unless you specifically tell it to do arithmetic. 

[http://tldp.org/LDP/abs/html/arithexp.html]("http://tldp.org/LDP/abs/html/arithexp.html")

Just for reference...

---

### Post by LotsOfPhil on 2007-03-06
It is 2 if you do it this way:
```

index=1
echo $index
let index+=1
echo $index
let index++
echo $index

```
1
2
3

---

### Post by Mr. C. on 2007-03-06
> **LotsOfPhil said:**
> index=$(($index+1))

Almost.  Its an odd syntax, but it is:

(( index += 1 )) 

to increment by one, or:

(( index = index + 1))

MrC

---

