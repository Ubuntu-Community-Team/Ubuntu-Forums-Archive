---
title: "Modifying lines in a text file"
date: 2009-08-01
forum: Programming Talk
---

### Post by Volt9000 on 2009-08-01
Ok, so I've got a .csv file which was generated from an Excel document. It looks like this:

```

"field1"," field2 "," field3 "

```

Now, unfortunately this is not exactly the format I want it in. The second and third fields seem to have a leading and trailing space, on ALMOST every line, which I want to remove. In addition, I want to add a number as the first field. So, the corrected line will look like this:

```

1,"field1","field2","field3"
2,"field1a","field2a","field3a"
etc.

```

Now I know there's probably a million and one ways to do this. I was trying to fix this up in a hurry so I just whipped together a quick and (very!!) dirty C program to do it for me. I'm not too proud of it, but it was the best I could do at the time.

I tried looking up documentation on tr, awk and sed, but alas I don't have nearly enough experience with either one (read: none) to be able to do anything with them.

I'm trying to get better with shell scripting, so I was hoping someone could give me a hand on how to do this with pure bash scripting, (i.e. no Python, Ruby, or any other languages, please.)

---

### Post by croto on 2009-08-01
maybe there's a cleaner solution, but I think this works:
```

cat inputfile | sed -e 's/"[[:space:]]*\([^[:space:]"]*\)[[:space:]]*"/"\1"/g' | awk '//{printf("%d,%s\n",NR,$0)}'

```

EDIT: there may be problems if there's a field that looks like 
'" field with spaces between words "'

---

### Post by MadCow108 on 2009-08-01
should also work but even messier :)
```
#!/bin/bash
#!/bin/bash
c=0
while read line
do c=$(($c+1));
	IFS=$','
	trim_str=""
	for tok in $line;
	do
		tok=`echo $tok | sed -e "s/[ \n\t]*\"[ \t\n]*\(.*\)\"/\1/" | sed -e "s/[ \t\n]*$//"`
		if [ -z "$trim_str" ]; then
			trim_str="\"$tok\""
		else
			trim_str="$trim_str,\"$tok\""
		fi
	done;
	echo "$c, $trim_str";
	IFS=$'\n'
done < "$1" #input file

```

---

### Post by croto on 2009-08-01
This solution seems to not have the problem my previous solution had
```

cat lala | sed -e 's/"[[:space:]]*/"/g' -e 's/[[:space:]]*"/"/g' | awk '//{printf("%d,%s\n",NR,$0)}'

```

EDIT:
even better:
```

cat lala | sed -e 's/[[:space:]]*"[[:space:]]*/"/g' | awk '//{printf("%d,%s\n",NR,$0)}'

```

---

### Post by Dill on 2009-08-01
A simple awk script can do the job:

```
awk '{gsub(" ",""); print FNR " " $0}' file
```

Cheers,
Dill

---

### Post by kaibob on 2009-08-01
Deleted by Kaibob

---

### Post by kaibob on 2009-08-01
I'm just learning, but it works:

```
nl -s "," -w 1 file | sed 's/ "/"/g;s/" /"/g'
```

---

### Post by ghostdog74 on 2009-08-01
```

# more file
"field1"," field2 "," field3 "
"field1"," fie ld2 "," fie ld3 "
# awk -F"," '{for(i=1;i<=NF;i++){gsub(/^\" | \"/,"\"",$i)}{print NR,$0}}' OFS="," file
1,"field1","field2","field3"
2,"field1","fie ld2","fie ld3"



```

---

### Post by ahmatti on 2009-08-02
Very nice solutions Dill and ghostdog! Show why awk is my favourite for this kind of things :) **@Volt9000** note that none of the examples above is "pure bash", in fact awk is as much of a programming language as python or perl. Awk is generally present in *nix systems so it doesn't really make a difference. However, you can't really do much just bash (try installing just bash on win, even "ls" won't work), but you need to call the system commands. See the bash tutorial in ghostdogs signature for more info.

---

### Post by Volt9000 on 2009-08-02
Wow, talk about more than one way to skin a cat... :D
Thanks, guys!

> 
```

nl -s "," -w 1 file | sed 's/ "/"/g;s/" /"/g'

```


Wow that's awesome, I didn't even know about that nl utility!

> 
note that none of the examples above is "pure bash", in fact awk is as much of a programming language as python or perl.


Yes I suppose you're right...
Although these solutions are much shorter (albeit more complex) than my little C program.

Ok, I just realized something else: sometimes field3 will have embedded into it the following text:

```

&#xxx

```

where xxx is a 3-digit number. This may appear any number of times (including none) in field 3. I need to add a semicolon after this. So

```

hello&#xxxworld&#yyyfoo

```

will become

```

hello&#xxx;world&#yyy;foo

```

I'm not sure how to do this because it's not just a straightforward replacement, since I have to search for the pound sign, and add the semicolon 3 characters after it's found.

---

### Post by croto on 2009-08-02
It is a simple replacement,after all.
```

sed -e 's/[[:space:]]*"[[:space:]]*/"/g' -e 's/\(&#...\)/\1;/g' file | awk '//{printf("%d,%s\n",NR,$0)}'

```

---

### Post by Volt9000 on 2009-08-03
Amazing! Thanks! :D

---

