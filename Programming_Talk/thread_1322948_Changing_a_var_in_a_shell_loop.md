---
title: "Changing a var in a shell loop"
date: 2009-11-11
forum: Programming Talk
---

### Post by CatharsisJelly on 2009-11-11
Can someone explain to me why $text is blank after exiting the loop?

```

#!/bin/bash
BOX='my.box'
THRESHOLD=10
MAILADDRESS='foo.bar@foo.com'
text=''
df -H | grep -vE '^Filesystem|tmpfs|cdrom' | awk '{ print $5 " " $1 }' | while read output;
do
    usep=$(echo $output | awk '{ print $1}' | cut -d'%' -f1  )
    partition=$(echo $output | awk '{ print $2 }' )
    if [ $usep -ge $THRESHOLD ]; then
        text="${text}Running out of space \"$partition ($usep%)\" on $(hostname) as on $(date)\n"
    fi
    echo ${#text}
done
echo $text

```

---

### Post by 0cton on 2009-11-11
It could be because the text inside the loop is a local variable.

---

### Post by CatharsisJelly on 2009-11-11
Okay so how do I get it to change the var that I assigned outside of the loop, or access this var outside of the loop?

---

### Post by ghostdog74 on 2009-11-11
you can see [this]("http://ghostdog74.livejournal.com/3027.html") similar example

---

### Post by kaibob on 2009-11-11
I'm a bit out of my depth in this thread, but you may want to look at the following:

[http://mywiki.wooledge.org/BashFAQ/024](http://mywiki.wooledge.org/BashFAQ/024)

---

### Post by Penguin Guy on 2009-11-11
> **0cton said:**
> It could be because the text inside the loop is a local variable.
I'm pretty sure it's nothing like that, I think it's because you're while statement is odd:
```

df -H | grep -vE '^Filesystem|tmpfs|cdrom' | awk '{ print $5 " " $1 }' | while read output;

```


This seems to work for me:
**[BASH]**
[PHP]
#!/bin/bash
THRESHOLD=10
text=''
OLD_IFS=${IFS}
IFS='
'
for output in `df -H | grep -vE '^Filesystem|tmpfs|cdrom' | awk '{print $5 " " $1}'`
do
	size=`echo ${output} | awk '{ print $1}' | cut -d'%' -f1`
	partition=$(echo ${output} | awk '{ print $2 }' )
	if [ ${size} -ge ${THRESHOLD} ]
	then
		text="${text}Running out of space on \"${partition}\" (${size}% full).\n"
	fi
done
IFS=${OLD_IFS}
text="${text}\t-- `hostname`: `date`\n"
echo -ne ${text}
[/PHP]
*(we change the IFS so that the for loop runs line-by-line rather than word-by-word)*

---

### Post by CatharsisJelly on 2009-11-11
Thanks for all the help people, I almost had kittens at the explanation of the while loop running a subshell, never knew that and think its a bit mad.  Both the awk and shell response work nicely, thanks

---

