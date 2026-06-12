---
title: "awk/paste column output"
date: 2015-05-25
forum: Programming Talk
---

### Post by achuthpnr on 2015-05-25
I have many text files with varying number of columns, but same number of lines. What I am trying to do is combine all the second column to another file. So, for N files, I should have N columns with data coming from the second column of each file.  Here is what I have so far

```
 find ./ -type f  -name 'text-N*.txt' -exec awk '{print $2}' {} \; | paste -d , > test.txt
```

search for the file, pipe the second column using awk to paste...

However, what I get is a long single column file. Where am I going wrong?

PS: the delimiter dosnt matter: it could be either tab or comma

---

### Post by steeldriver on 2015-05-25
The issue is that paste sees only a single stream, I think - it has no idea what elements come from which file

If you don't have *too *many matching files, you might be able to get away with something like

```

find ./ -type f  -name 'text-N*.txt' awk '{a[FNR] = (!a[FNR]? $2 : a[FNR]","$2)}; END{for (nr in a) print a[nr]}' {} +

```

otherwise you will need to exec paste for each found file and ping-pong between a couple of temporary files, I think

---

### Post by SeijiSensei on 2015-05-25
How about
```

for f in text-N*.txt
do
    awk '{print $2}' < $f >> output.txt
done

```

---

### Post by aromo2 on 2015-05-25
Definitely not a one-liner.  This worked for me (data files named F1.txt, F2.txt, F3.txt, ...) :
```

LINES=`cat F1.txt|wc -l`
LINE_COUNT=1
while [ $LINE_COUNT -le $LINES ]; do
        for i in F*.txt; do
                head -$LINE_COUNT $i|tail -1|awk '{printf "%s ",$2}'
        done
        LINE_COUNT=$[ $LINE_COUNT + 1 ]
        echo ""
done

```
Hope it helps.

---

### Post by aromo2 on 2015-05-25
The corrected line:
```

find . -type f  -name 'F*.txt' -exec awk '{a[FNR] = (!a[FNR]? $2 : a[FNR]","$2)}; END{for (nr in a) print a[nr]}' {} +

```
Worked but the resulting columns were not in the same order as the files in my test case.

---

### Post by steeldriver on 2015-05-25
The order that the columns appear in will be whatever order 'find' finds the files - I'm not sure there's any way to control that (it will depend where they are in the inode table, I think). You would need to add a separate 'sort' operation.

OTOH shell globs should give a predictable order (although it may not be the order you expect - depending on your system's locale) so if the files are all at a single directory level then you could just do something like

```

awk '{a[FNR] = (!a[FNR]? $2 : a[FNR]","$2)}; END{for (nr in a) print a[nr]}' F*.txt

```

---

### Post by aromo2 on 2015-05-25
> **steeldriver said:**
> The order that the columns appear in will be whatever order 'find' finds the files - I'm not sure there's any way to control that (it will depend where they are in the inode table, I think). You would need to add a separate 'sort' operation.

OTOH shell globs should give a predictable order (although it may not be the order you expect - depending on your system's locale) so if the files are all at a single directory level then you could just do something like

```

awk '{a[FNR] = (!a[FNR]? $2 : a[FNR]","$2)}; END{for (nr in a) print a[nr]}' F*.txt

```

Yeah, that worked with columns in the same order as the files.

---

### Post by achuthpnr on 2015-05-26
Thanks steeldriver and aromo2.

the following ones worked 
```


find . -type f  -name 'File*.txt' -exec awk '{a[FNR] = (!a[FNR]? $2 : a[FNR]"\t"$2)}; END{for (nr in a) print a[nr]}' {} + >output.txt

```
```

awk '{a[FNR] = (!a[FNR]? $2 : a[FNR]"\t"$2)}; END{for (nr in a) print a[nr]}' File*.txt >output.txt


```

SeijiSensei, your script gives a single column, which I already had in the beginning. 
aromo2, I couldnt use your script directly, since the files were not sequentially numbered.

In general, if there is a column header, this fails. How can I get around ? 
I´ve found the option NR>1 , but not sure were to include that in the script. Im trying to figure that out.

Cheers

---

### Post by achuthpnr on 2015-05-26
Hello again.

The two scripts above seems to work for smaller files, but fails for bigger ones. The rows are mixed up and I cant figure out where the problem is. 
Test files are attached for clarity.

---

### Post by steeldriver on 2015-05-26
Oops my bad - you didn't do anything wrong, I was forgetting that awk doesn't necessarily preserve the order. I can think of a few approaches to fix that- however I don't have time right now: in the meantime you may find something that works for you in this recent U&L thread --> [http://unix.stackexchange.com/questions/205642/combining-large-amount-of-files](http://unix.stackexchange.com/questions/205642/combining-large-amount-of-files)

---

### Post by Lars Noodén on 2015-05-26
You can use [process substitution](http://tldp.org/LDP/abs/html/process-sub.html) to include output from awk as if it were input from a file.  That should save a step or two when using [paste](http://manpages.ubuntu.com/manpages/trusty/en/man1/paste.1.html).

```

paste <(awk '{print $2}' f1.txt) output.txt > temp.txt

```

Or are you referring to the order in which the files are read?  As in F1.txt, F2.txt and so on?

---

### Post by achuthpnr on 2015-05-26
For the moment, I dont care about the sequence in which the files are read. 
I will try the paste command and report later
In the mean time; I wrote a small C program to do the merging.

Is coding in C better than learning to use awk to do the same thing? For me; I would say yes for the moment.

---

### Post by Lars Noodén on 2015-05-26
It's not so much awk as bash:

```

#!/bin/bash

temp=$( mktemp );

for file in *.txt; do

 paste output.text <( awk '{print $2}' "$file" ) > $temp;
 mv $temp output.text;

done;

```

The crux is the process substitution which is a bashism.  But C is useful if you can do it that way.

---

### Post by Vaphell on 2015-05-26
maybe something like this (assuming the files have the same 2 column format)

```
paste **/text-N*.txt | awk '{ for(i=1; i<NF; i+=2); $i=""; print }'
```

** is for recursive mode and assumes bash with globstar enabled (shopt -s globstar)

long winded version with *find* could look like this (bash):

```
# empty array
files=()
# append files from find
while IFS= read -rd $'\0' f; do files+=( "$f" ); done < <( find -name 'text-N*.txt' -print0 )
# paste files stored in array
paste "${files[@]}" | awk '{ for(i=1; i<NF; i+=2) $i=""; print; }'
```

if you want to force awk to rebuild the record in order to get rid of superfluous spacing , add *$0=$0; $1=$1;* before *print;*


Imo learning some higher level language is beneficial in general, be it awk, python or what have you. Micromanaging stuff in C is more hassle than it's worth 99 times out of 100.

---

### Post by Lars Noodén on 2015-05-26
Should that have some braces for the 'for' statement?

```
paste **/text-N*.txt | awk '{ for(i=1; i<NF; i+=2) { $i=""; } print }'
```

---

### Post by Vaphell on 2015-05-26
not really, the loop consumes the entity following it (or does nothing if it's followed by ; )
```
$ echo a b c d e f | awk '{ [COLOR="#0000FF"]for(i=1; i<NF; i+=2) $i="";[/COLOR] print; }'
 b  d  f
```

It's the same behavior that can be seen in C, where loops and ifs work perfectly fine with single expressions without using blocks, but there be bug dragons so the practice is avoided and always using {} is advised instead.

 ```
 for( int i=0; i<3; i++ )
       printf("for1\n");  // this belongs to the loop
       printf("for2\n");  // this doesn't
       
   for( int i=0; i<3; i++ );
       printf("for1\n");  // nope
       printf("for2\n");  // nope
```

---

### Post by achuthpnr on 2015-05-28
Thanks Vaphell for the detailed explanation. Its good now.

---

