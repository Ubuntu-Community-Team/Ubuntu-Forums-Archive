---
title: "sed or awk question - Remove text after colon"
date: 2013-11-24
forum: Programming Talk
---

### Post by GrouchyGaijin on 2013-11-24
Hi Guys,

I would like to remove the text after a colon on a specific line in a text file.

The file looks like this for example:
```

Stuff I want to keep : January 31, 2014
More stuff : February 2, 2014
Yet more stuff : March 10, 2014

```

How could I remove the text after the colon from line 2 so that I end up with

```

Stuff I want to keep : January 31, 2014
More stuff : 
Yet more stuff : March 10, 2014

```

I appreciate the help!

---

### Post by r-senior on 2013-11-24
There may be more elegant ways:

```
sed '2 s/:.*/:/' yourfile.txt
```

---

### Post by GrouchyGaijin on 2013-11-24
Thank you - that works perfectly...
except now I have another question.

Basically this is for a script to update a due date on a todo list.

I can append text to an item on the list easily enough.

```

read -p "Enter the task number: " tasknumber
read -p "Enter the due date: " duedate
/home/gg/scripts/todo.sh append $tasknumber Due Date: $duedate

``` 

When I try to stick the $tasknumber variable (which is a line number), the date is not removed.
If I use the actual line number instead of the variable, the date is removed.

I've tried with both single quotes and double quotes:
```

sed "$tasknumber s/:.*/:/" /home/gg/Dropbox/todo/todo.txt

```

and

```

sed '$tasknumber s/:.*/:/' /home/gg/Dropbox/todo/todo.txt

```

Any idea what the problem is?

Thanks again!

---

### Post by r-senior on 2013-11-24
The variable works OK for me with double-quotes on the sed to allow the variable substitution:

```
$ read -p 'Task: ' tasknumber
Task: 2
$ sed "$tasknumber s/:.*/:/" temp.txt
Stuff I want to keep : January 31, 2014
More stuff :
Yet more stuff : March 10, 2014

```

So it must be something to do with how you are calling that script.

---

### Post by GrouchyGaijin on 2013-11-24
I think you are right.
It works for me when I run it just in the terminal but not in the script.
I also noticed that even though I have the path to the text file, the changes don't see to actually be written.
In the terminal I'll see the truncated task, but if I run the list tasks command
```

todo.sh ls

```
I still see the unmodified task, that is with the original date.

---

### Post by steeldriver on 2013-11-24
Are you using the -i switch in your sed commands? otherwise it just writes the modified file to stdout

```

       -i[SUFFIX], --in-place[=SUFFIX]

              edit files in place (makes backup if extension supplied)

```

---

### Post by GrouchyGaijin on 2013-11-24
Dou!! ;)

---

