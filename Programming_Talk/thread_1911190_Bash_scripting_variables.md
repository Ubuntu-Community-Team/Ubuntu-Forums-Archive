---
title: "Bash scripting variables"
date: 2012-01-18
forum: Programming Talk
---

### Post by cortman on 2012-01-18
I was wondering if I can take the output of a command such as

```
ls -l my_file | awk '{ print $6 }'
```

and assign it as a variable's value?
This would in effect set the variable as the last-modified date of my_file.
How would I do this? Or any other way to grab info about a file (its datestamp, read/write permissions, size, etc.) and assign it to a variable?

---

### Post by MG&amp;TL on 2012-01-18
```
myvar=$(ls -l my_file | awk '{ print $6 }')
echo $myvar
```

for instance. :)

---

### Post by |{urse on 2012-01-18
Or you can just create a new file for that and use it as a variable.

touch file && ls -l my_file | awk '{ print $6 }' > file

---

### Post by aromo on 2012-01-18
or use back quotes:
[FONT="Courier New"]myvar=`ls -l my_file | awk '{ print $6 }'`
echo $myvar[/FONT]

---

### Post by nothingspecial on 2012-01-18
> **aromo said:**
> or use back quotes:
[FONT="Courier New"]myvar=`ls -l my_file | awk '{ print $6 }'`
echo $myvar[/FONT]

backticks are deprecated for command substitution. See

[http://wiki.bash-hackers.org/scripting/obsolete](http://wiki.bash-hackers.org/scripting/obsolete)

---

### Post by Lars Noodén on 2012-01-18
> **aromo said:**
> or use back quotes

I learned using backticks, too, but nowadays that method is deprecated.

Here is a good explanation of why is $(...) is preferred over backticks:
[http://mywiki.wooledge.org/BashFAQ/082](http://mywiki.wooledge.org/BashFAQ/082)

---

### Post by |{urse on 2012-01-18
Yea, its too hard to discern the grave ` vs ' with a lot of fonts.

---

### Post by cortman on 2012-01-18
> **MG&TL said:**
> ```
myvar=$(ls -l my_file | awk '{ print $6 }')
echo $myvar
```

for instance. :)

This worked great. I can't believe I didn't think of it before, but oh well.
NOW my current problem is that I'd like to append the contents of the variable to a folder name. I used the mv command to 

```
mv folder folder.$my_var
```

This worked great with a standard blank file, but will not work with a folder. Mv didn't have any options that would fix it. Am I missing something really basic?

---

### Post by MG&amp;TL on 2012-01-18
It works fine, here, but without the dot. error message?

---

### Post by cortman on 2012-01-18
```
mv: target `2012-01-18' is not a directory
```


Here's my code:

```

mkdir /home/cortman/data/backup
cp /home/cortman/doug /home/cortman/data/backup
date=$(ls -l /home/cortman/data/backup | awk '{ print $6 }')
mv /home/cortman/data/backup /home/cortman/data/backup.$date

```

---

### Post by MG&amp;TL on 2012-01-18
> **cortman said:**
> ```
mv: target `2012-01-18' is not a directory
```


Here's my code:

```

mkdir /home/cortman/data/backup
cp /home/cortman/doug /home/cortman/data/backup
date=$(ls -l /home/cortman/data/backup | awk '{ print $6 }')
mv /home/cortman/data/backup /home/cortman/data/backup.$date

```

```
mkdir /home/cortman/data/backup
cp /home/cortman/doug /home/cortman/data/backup
date=$(ls -l /home/cortman/data/backup | awk '{ print $6 }')
mkdir /home/cortman/backup.$date && mv /home/cortman/data/backup
/home/cortman/data/backup.$date
```


fixed, I think.

---

### Post by Vaphell on 2012-01-18
i think he has a problem because ls -l <dir> shows dir's contents not its properties
ls -ld <dir> would do the trick

do normal ls -l and filter in awk step
```
ls -l | awk '/'"${selected}"'/{ print $6 }'
```
example:
```
$ selected=Music
$ ls -l | awk '/'"${selected}"'/{ print $6 }'
2011-11-10
```

or you can try a different approach and get the time using the stat command (it doesn't care about the object type)
```
$ stat -c '%y'  "${selected}"
2011-11-10 07:23:39.796408979 +0100
```

---

### Post by cortman on 2012-01-18
> **Vaphell said:**
> i think he has a problem because ls -l <dir> shows dir's contents not its properties
ls -ld <dir> would do the trick

do normal ls -l and filter in awk step
```
ls -l | awk '/'"${selected}"'/{ print $6 }'
```
example:
```
$ selected=Music
$ ls -l | awk '/'"${selected}"'/{ print $6 }'
2011-11-10
```

or you can try a different approach and get the time using the stat command (it doesn't care about the object type)
```
$ stat -c '%y'  "${selected}"
2011-11-10 07:23:39.796408979 +0100
```

Aha! That's the problem, I can see now.

I'll try this and MG&TL's suggestion. Thanks to both of you!

---

### Post by cortman on 2012-01-18
Changing "ls -l" to "ls -ld" did the trick.

Thanks a lot to all!!

---

