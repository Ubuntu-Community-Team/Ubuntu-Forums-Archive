---
title: "awk NR returning one less"
date: 2011-11-26
forum: Programming Talk
---

### Post by crownedzero on 2011-11-26
I'm building a script that accesses a file. I've currently put 8 records into the test data but when I try to list with line numbers I get 7 rather than 8...

```

	while read line; do
		echo -e "$(awk '{print NR, $1, $2, $3, $4}')"
		counter="$(wc -l motorcycles.txt )"
		done < motorcycles.txt
	echo -e "\n"

```

---

### Post by Vaphell on 2011-11-26
i'd like to know how on earth that awk line works at all with no explicit input? o.O

your script doesn't make much sense, you read file line by line yet you try to count lines with awk? besides wc -l inside loop is excessive

```

echo wc -l: $(wc -l test.txt )
echo awk:
awk 'BEGIN { c=0; e=0; };
           { printf( "NR=%d NF=%d : %s\n", NR, NF, $0 ); if (NF>0) c++; else e++; };
     END   { printf("records: %d\nempty lines: %d\n", c, e ); }' test.txt
```

```
$ ./awk.sh 
wc -l: 7 test.txt
awk:
NR=1 NF=2 : TEST	0195225779
NR=2 NF=2 : TEST	0195225780
NR=3 NF=0 : 
NR=4 NF=2 : TEST	0195225782
NR=5 NF=2 : TEST	0195225783
NR=6 NF=0 : 
NR=7 NF=2 : TEST	0195225784
records: 5
empty lines: 2

```
if all you want to do is to count valid records the middle part can be replaced with simpler
```
NF>0 { c++ }
```

---

### Post by crownedzero on 2011-11-26
i just threw the wc in there, i ended up with

```

	while read line; do
			#echo -e "$(awk -F':' '{print NR, $1, $2, $3, $4}')"
			let count++
			echo $count $line
	done < <(awk -F':' '{print $1, $2, $3, $4 }' motorcycles.txt)


```

I guess this is why we call it learning lol

---

### Post by Vaphell on 2011-11-26
your approach will fail if by any chance there are empty lines, for example endline at the end of file is not unheard of :-)

---

### Post by crownedzero on 2011-11-26
Assuming a user doesn't tweak the file itself there won't be any blank lines. The script takes information and stores it in a delimited file, and won't accept blank input so hopefully I'm covered =)

Then again I guess at some point I could add an if to the statement not to count blank lines.

I'm awking the file line by line to a screen with the number choice in front of it, the user selects the line they'd like to edit and then I'm hoping to modify the different fields contents. Idk we'll see how it goes =)

---

### Post by sisco311 on 2011-11-27
Check out BashFAQ 001 (link in my signature) and [http://wiki.bash-hackers.org/howto/edit-ed](http://wiki.bash-hackers.org/howto/edit-ed)

---

