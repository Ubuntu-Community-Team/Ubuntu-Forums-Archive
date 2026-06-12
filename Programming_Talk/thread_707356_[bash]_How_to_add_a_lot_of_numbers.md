---
title: "[bash] How to add a lot of numbers?"
date: 2008-02-25
forum: Programming Talk
---

### Post by mridkash on 2008-02-25
I'm having a problem adding numbers from a file and displaying it on the screen.

The file is like this,

121
213
2354
23
5878
546
65

Now, I want to add up these numbers and display.
I "dont" want to use "cat file | while read var" loop because it is slow and the variable created inside it isn't accessible from outside the loop.

Please suggest me ways.

Also, if you'd help me, suggest me the fastest way to read a file full of file paths (newline separated) and calculate their total file size, I've used command " cat file | xargs du " but it says the list of arguments is too large.

Thanks.

---

### Post by LaRoza on 2008-02-25
<edit>
Never mind, shell solution given.
</edit>

---

### Post by Martin Witte on 2008-02-25
> **mridkash said:**
> 
Now, I want to add up these numbers and display.
I "dont" want to use "cat file | while read var" loop because it is slow and the variable created inside it isn't accessible from outside the loop.
what about
```
martin@toshibap200:~$ cat test.txt
121
213
2354
23
5878
546
65
martin@toshibap200:~$ cat script.bash 
#!/bin/sh
value=0
while read var
do
value=`expr $value + $var`
done < test.txt
echo $value
martin@toshibap200:~$ 
martin@toshibap200:~$ ./script.bash 
9200

```

---

### Post by a9bejo on 2008-02-25
> **mridkash said:**
> 
I've used command " cat file | xargs du " but it says the list of arguments is too large.

This is a good discussion of the problem, including some possible solutions:

[http://www.linuxjournal.com/article/6060](http://www.linuxjournal.com/article/6060)

---

### Post by Zwack on 2008-02-25
Two completely different questions...

The script that you've already been given will work, and seems reasonable enough...

Given that you have that you could always read your second file of path names and add the results of du <name> to a second file and then run that through your first script... :)

Alternatively you could try...

```

#! /bin/sh

file=$1 # Add some error checking/usage stuff around this

total=0

for path in `cat ${file}`
do
  pathsize=`du -s ${path} | cut -f 1`
  total=`expr ${total} + ${pathsize}`
done

echo $total

exit 0

```
Presumably you want to get the total sizes of the directories including their subdirectories... du <dir> lists the sizes of each of the files in that directory...

I hope that this helps,

Z.

---

### Post by ghostdog74 on 2008-02-25
> **mridkash said:**
> I'm having a problem adding numbers from a file and displaying it on the screen.

The file is like this,

121
213
2354
23
5878
546
65

Now, I want to add up these numbers and display.
I "dont" want to use "cat file | while read var" loop because it is slow and the variable created inside it isn't accessible from outside the loop.


```

awk '{total+=$0}END{print total}' file

```

> 
Also, if you'd help me, suggest me the fastest way to read a file full of file paths (newline separated) and calculate their total file size, I've used command " cat file | xargs du " but it says the list of arguments is too large.
Thanks.
```

while read -r file
do 
  total=`du -s "$file"`
  echo "Total size for $file is : $total"
done < "input"

```

---

### Post by mridkash on 2008-02-25
Thanks guys. 
But one thing I dont understand is, why the "for" or "while" loop runs so slowly in bash.

Example, I was doing,
```
cat path/to/file | while read files ; do
echo -n $files | grep -v -z -e "[/][.]"  >> $backupList
done

```And then I tried,
```
grep -v -e "[/][.]" path/to/file > $backupList
```And to my surprize, the second one finished in a jiffy and the first one took like 5-10 seconds.
How?

---

### Post by ghostdog74 on 2008-02-25
> **mridkash said:**
> Thanks guys. 
But one thing I dont understand is, why the "for" or "while" loop runs so slowly in bash.

Example, I was doing,
```
cat path/to/file | while read files ; do
echo -n $files | grep -v -z -e "[/][.]"  >> $backupList
done

```

cat is not needed, if you are using the while loop. Try not to use cat unnecessarily as possible. grep's "looping" mechanism is compiled into the tool itself ( C language). Whereas you have to explicitly call while loop in bash. Imagine what happens if you could do this in bash
```

# bash -v -e "pattern" file 

```

> 
And then I tried,
```
grep -v -e "[/][.]" path/to/file > $backupList
```And to my surprize, the second one finished in a jiffy and the first one took like 5-10 seconds.
How?
as explained above.

---

### Post by Zwack on 2008-02-26
Every time a shell calls a program it has to instantiate that program (fork exec) run it and get the results...  If you are only using built-ins it's much faster or if you cut the number of programs you need to run it speeds up.

Your first example uses 

one program outside the loop but inside the loop does...

read, echo, grep

for every file...  Even if the grep was the only one that is called thats still a lot more than
 the second version which runs one command.

Z.

---

### Post by ianare on 2010-03-11
One line version of the script above (for the impatient).

```
value=0; while read var; do value=`expr $value + $var`; done < test.txt; echo $value
```

---

### Post by kaibob on 2010-03-11
Post deleted.

---

### Post by ibuclaw on 2010-03-11
This thread has had no activity for over a year, closing.

---

