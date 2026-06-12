---
title: "Can this bash script be faster (and how to benchmark it)?"
date: 2007-09-11
forum: Programming Talk
---

### Post by Krijk on 2007-09-11
I parse the following to single lines:

**Example** 

something
1 else
2 other
3 first

otherthing
1 apple
2 coconut
3 pear

to output

something else
something other
something first
otherthing apple
otherthing coconut
otherthing pear

I created the following script to achieve this. First I modify the file with sed to insert an identifier so the script knows where to start.

```
read_file()
{
	cd $workdir/tmp
	cat modified.file | 
	while read tmpfile; do
	    identifier_to_var
	done
}

identifier_to_var()
{
	if echo $tmpfile | grep -e '~IDENTIFIER~'  
	then 
		id_var_tmp=$tmpfile
		id_var=$(echo $id_var_tmp | sed 's/~IDENTIFIER~//')
	else
		sublines_to_identifier
	fi
}

sublines_to_identifier()
{
        field1=$(echo $tmpfile | awk ' { print $3 }')
        field2=$(echo $tmpfile | awk ' { print $2 }')
        echo "$id_var ; $field1 ; $field2 ;" >> $workdir/output.csv
}

```

I'm pretty new at programming and I want to start with bash first to learn the basics before I go to Python, Perl or other languages. The script works fine,  but it takes a long time to finish on large files. 

*How can make the script faster? 

*How can I benchmark bash scripts?

---

### Post by CptPicard on 2007-09-11
I honestly think you're plenty competent to move on to programming languages considering you're doing a good job at writing a fairly complex bash script :) Doing this in Python or any other programming language by that matter would simplify your solution and give it a more consistent feel (I for one would never even bother trying this in bash unless I knew more advanced scripting languages weren't available).

Dunno about making it faster, but look at the "time" command for benchmarking :)

---

### Post by ghostdog74 on 2007-09-11
> **Krijk said:**
> 
```
read_file()
{
	cd $workdir/tmp
	cat modified.file | 
	while read tmpfile; do
	    identifier_to_var
	done
}

```

Useless use of cat. Remove the cat and use the while loop instead
eg
```

while read tmpfile;do
...
done < modified.file

```

> 
```

identifier_to_var()
{
	if echo $tmpfile | grep -e '~IDENTIFIER~'  
	then 
		id_var_tmp=$tmpfile
		id_var=$(echo $id_var_tmp | sed 's/~IDENTIFIER~//')
	else
		sublines_to_identifier
	fi
}

```

redundant checking. Just use sed. If sed finds IDENTIFIER, it will do something, else, it won't. So there's no need to do extra checks using if else. eg
```

sed 's/blah//' $tmpfile

```

> 
```

sublines_to_identifier()
{
        field1=$(echo $tmpfile | awk ' { print $3 }')
        field2=$(echo $tmpfile | awk ' { print $2 }')
        echo "$id_var ; $field1 ; $field2 ;" >> $workdir/output.csv
}

```

redundant steps. 
```

awk '{print $3" "$2}' $tmpfile > $workdir/output.csv

```

---

### Post by Krijk on 2007-09-12
> **CptPicard said:**
> I honestly think you're plenty competent to move on to programming languages considering you're doing a good job at writing a fairly complex bash script :) Doing this in Python or any other programming language by that matter would simplify your solution and give it a more consistent feel 
:redface: Thanks for the compliments, but I'm still struggling with variables and loops a lot.


> **ghostdog74 said:**
> Useless use of cat. Remove the cat and use the while loop instead
eg
```

while read tmpfile;do
...
done < modified.file

```
I've tried this and it is indeed faster, but not that much. The script ran against the same file for aprox 1h45m and it's less then a minut faster.  It's cleaner though and I store it my example-files.

> **ghostdog74 said:**
> 
redundant checking. Just use sed. If sed finds IDENTIFIER, it will do something, else, it won't. So there's no need to do extra checks using if else. eg
```

sed 's/blah//' $tmpfile

```
[/code]
This sed removes the identifier to get the original value back.

> **ghostdog74 said:**
> 
redundant steps. 
```

awk '{print $3" "$2}' $tmpfile > $workdir/output.csv

```
I'm not sure how to get the id_var in the right position with this.

---

### Post by digitalbenji on 2007-09-12
Wow, I would have a far easier time writing this in any other language then a Bash script.  Sed and Awk give me nightmares.

---

### Post by ghostdog74 on 2007-09-12
@OP:
here's how it looks like in my version. I use your sample input file. 
```

awk '!/[0-9]/{ header=$0;next} { print header "$2}' "file"

```
output:
```

# awk '!/[0-9]/{ header=$0;next} { print header" "$2}' "file"
something else
something other
something first
otherthing apple
otherthing coconut
otherthing pear

```
that's what you want right?

---

### Post by bashologist on 2007-09-12
code:
```
while read line; do
	if [[ "$line" =~ ^[0-9] ]]; then
		echo "$word ${line#* }"
	else
		word=$line
	fi
done < test.txt

```
output:
```
foo@bar:~$ ./test.sh
something else
something other
something first
otherthing apple
otherthing coconut
otherthing pear
```
That's how it's done in bash. n_n

---

### Post by ghostdog74 on 2007-09-12
> **bashologist said:**
> code:
```
while read line; do
	if [[ "$line" =~ ^[0-9] ]]; then
		echo "$word ${line#* }"
	else
		word=$line
	fi
done < test.txt

```
output:
```
foo@bar:~$ ./test.sh
something else
something other
something first
otherthing apple
otherthing coconut
otherthing pear
```
That's how it's done in bash. n_n
my version of bash leaves out the last line.  any ideas?
```

# more file
something
1 else
2 other
3 first

otherthing
1 apple
2 coconut
3 pear
# more testnew.sh
#!/bin/sh

while read line; do
        if [[ "$line" =~ ^[0-9] ]]; then
                echo "$word ${line#* }"
        else
                word=$line
        fi
done < file

# ./testnew.sh
something else
something other
something first
otherthing apple
otherthing coconut
# awk '!/[0-9]/{ header=$0;next} { print header" "$2}' "file"
something else
something other
something first
otherthing apple
otherthing coconut
otherthing pear


```

---

### Post by bashologist on 2007-09-12
The file need to end with a newline probably.

---

### Post by Krijk on 2007-09-12
> **bashologist said:**
> code:
```
while read line; do
	if [[ "$line" =~ ^[0-9] ]]; then
		echo "$word ${line#* }"
	else
		word=$line
	fi
done < test.txt

```


I went for this and modified it a little. It sure helped speeding it up! The modified script ran **41% faster** than the previous one.  Getting rid of sed sure helped a lot.

```

read_file()
{
	cd $workdir/tmp
	while read tmpfile; do
	       if [[ "$tmpfile" =~ ^[.] ]]; then
			id_var=$tmpfile
	        else
			sublines_to_identifier
	        fi
	done <$inputfile
}

sublines_to_identifier()
{
field1=$(echo $tmpfile | awk ' { print $12 }')
field2=$(echo $tmpfile | awk ' { print $17 }')
field3=$(echo $tmpfile | awk ' { print $7 }')
echo "$id_var ; $field1 ; $field2 ; $field3 ;" >>$outputfile
}
```

Thanks everyone for the input. I've learned at lot again :)

---

### Post by ghostdog74 on 2007-09-12
> **Krijk said:**
> I went for this and modified it a little. It sure helped speeding it up! The modified script ran **41% faster** than the previous one.  Getting rid of sed sure helped a lot.

```

read_file()
{
	cd $workdir/tmp
	while read tmpfile; do
	       if [[ "$tmpfile" =~ ^[.] ]]; then
			id_var=$tmpfile
	        else
			sublines_to_identifier
	        fi
	done <$inputfile
}

sublines_to_identifier()
{
field1=$(echo $tmpfile | awk ' { print $12 }')
field2=$(echo $tmpfile | awk ' { print $17 }')
field3=$(echo $tmpfile | awk ' { print $7 }')
echo "$id_var ; $field1 ; $field2 ; $field3 ;" >>$outputfile
}
```

Thanks everyone for the input. I've learned at lot again :)
you could have gotten rid of sublines_to_identifier routine as well. maybe next time.

---

