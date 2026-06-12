---
title: "Question about BASH"
date: 2009-02-25
forum: Programming Talk
---

### Post by Tek-E on 2009-02-25
In the c programming you can compare numbers on wether they are equal to
== or not equal to != each other.

How exactley can you do this in BASH?

Would it still be !=  ???

for instance
```

x=$(wc -l < $FILE)
pos=1
while [ $pos != $x ]
do
    .......
done

```

Would that be in-correct??
Any help is much appreciated. Thank you!

---

### Post by geirha on 2009-02-25
```
man [
```
Read the man-page of the [ command. In particular, look at -eq and -ne
```

[ 1 -eq 1 ] && echo yes || echo no
[ 1 -eq 2 ] && echo yes || echo no
[ 1 -ne 1 ] && echo yes || echo no
[ 1 -ne 2 ] && echo yes || echo no

```

Note that both dash and bash has a built in version of [, but the syntax explained in ['s man-page should still apply.

---

### Post by Tek-E on 2009-02-25
Nevermind.  I figured it out! =)

---

### Post by Tek-E on 2009-02-25
I do have another Question though.......
I am helping My sys admin convert some XHTML files for the new website he is putting up and I am working towards writing a script that will speed up the process but at the moment I am testing a few simple script but I am havnig troubles.. Could you guys look at this test script I wrote and tell me what it is I am doing wrong?

```

#!/bin/bash
cd Desktop
f_len=$(wc -l < sbp1105.xhtml)
f_pos=1
while [ $f_pos != $f_len ]
do
	mkdir con_temp
	line=$(head -n $f_pos sbp1105.xhtml | tail -n 1 > con_temp/1.txt)
	find_div=$(grep 'div' con_temp/1.txt)
	_bnk=""
	if [ $find_div = $_bnk ] ; then
		echo "Line $f_pos : DIV not found."
		f_pos=$(expr $f_pos + 1)
	else
		#Just for Debugging Purposes
		printf "\nDiv ID Found!\n"
	fi
done

```

---

### Post by geirha on 2009-02-25
> **Tek-E said:**
> 
```

	if [ $find_div = $_bnk ] ; then

```

since $_bnk is "", that will not work. If $find_div is "<div>something", then the [ command in that if is equivalent to
```
$ [ "<div>something" = ]
-bash: [: <div>something: unary operator expected

```
Always quote strings when you compare them with [.
```

$ _bnk="" find_div="<div>something"
$ [ "$find_div" = "$_bnk" ] && echo yes || echo no
no

```

BTW, consider
```
grep -n 'div' sbp1105.xhtml
```
EDIT:
or ```
awk '/div/{print NR}' sbp1105.xhtml
```

---

### Post by ghostdog74 on 2009-02-25
> **Tek-E said:**
>  Could you guys look at this test script I wrote and tell me what it is I am doing wrong?

```

#!/bin/bash
cd Desktop
f_len=$(wc -l < sbp1105.xhtml)
f_pos=1
while [ $f_pos != $f_len ]
do
	mkdir con_temp
	line=$(head -n $f_pos sbp1105.xhtml | tail -n 1 > con_temp/1.txt)
	find_div=$(grep 'div' con_temp/1.txt)
	_bnk=""
	if [ $find_div = $_bnk ] ; then
		echo "Line $f_pos : DIV not found."
		f_pos=$(expr $f_pos + 1)
	else
		#Just for Debugging Purposes
		printf "\nDiv ID Found!\n"
	fi
done

```

there are some flaws in your logic.
1) while [ $f_pos != $f_len ] :->> basically you just want to iterate the file, therefore a while read loop is enough.

2) why do you need to "mkdir con_temp" everytime you go through the while loop?

3) I see that you just need to find the word "div" is that correct? if so, the whole code above just can be replaced by simple grep.
```

grep -i "div" file 

```

if you want to process each line that grep finds a "div", use while read loop
```

grep -i "div" file | while read line
do
  echo "do something with $line"
done

```

---

