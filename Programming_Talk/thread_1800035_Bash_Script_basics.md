---
title: "Bash Script basics"
date: 2011-07-08
forum: Programming Talk
---

### Post by hailholyghost on 2011-07-08
Hi Ubuntu Experts,

I have 14 directories that I have to do repetitive commands with, so naturally I wanted to automate the tasks.

The script "make.answers" is specific for each directory and works fine.

The script EXECUTE.sh reads:

```
#!/bin/bash

for i in `rna.caau.99 rna.caau.99X rna.caau.tor n.syn.99 n.syn.99 n.syn.tor s.anti.99 s.anti.99X s.anti.tor s.syn.99 s.syn.99X s.syn.tor lna.99 lna.caau.99X`
do
 cd /sicklestroke/home/con/$i
 ./make.answers
 cd /sicklestroke/home/con
done
```

But there is an issue about changing directories within a script.  I have heard of "sourcing" the script, but that gave the same error:

```

dave@zip:/sicklestroke/home/con$ . ./EXECUTE.sh 
rna.caau.99: command not found
```

The error makes no sense because "rna.caau" is not contained within the command!  Except perhaps within the "./"?

How does one go about changing directories within a script?  I have heard of people making aliases in ~/.bashrc, but making 14+1 = 15 different aliases for each directory change seems silly.

Thanks for your help!:)
-Dave

---

### Post by Bachstelze on 2011-07-08
Read more about what backticks (`) are used for.  It is not what you think.

---

### Post by Grenage on 2011-07-08
Why the back-ticks in the for loop?

---

### Post by hailholyghost on 2011-07-08
Thank you much Bachstelze and Grenage!  It was a silly mistake on my part.

I usually use back-ticks to get results from a shell command, usually "ls".

I appreciate your help!

---

### Post by Grenage on 2011-07-08
When you *would* use back-ticks, it's often easier to use $() instead; it can make it easier to read.  For example:

```
for i in *
do
  echo $(echo "$i" | sed 's/file/parsnip/')
done
```

---

### Post by pafoo on 2011-07-08
Like Grenage said, $() is the new way backticks are the old fashioned way. One note, if you have a list like that, put them in a flat file and do your for loop with a 

```

for item in $(cat /home/mylist)
do
echo $item
done

```

A little easier than typing everything out!

---

