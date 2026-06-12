---
title: "Bash: grabbing the first part of a line"
date: 2009-02-02
forum: Programming Talk
---

### Post by madflyguy on 2009-02-02
I have a script right now that is grabbing IPs from a text file using;```
head -c 16
```of course not all IPs are 16 characters long, and sometimes the IPs are short enough that my head -c 16 grabs text from the rest of the line. To stop this, how do I simply grab text from a line until it hits white space? I know this is pretty simple but I haven't figured it out yet.

To be more specific, the files I'm pulling from look like;
```
a.a.a.a     b.b.b.b     c.c.c.c
x.x.x.x     y.y.y.y    z.z.z.z
```
I only want a.a.a.a and x.x.x.x which can be 8 - 16 characters long.

---

### Post by johnl on 2009-02-02
You can use awk:

```

cat myfile.txt | awk ' { print $1 } '

```

Will print only the first column in the file.

Hope this helps!

---

### Post by madflyguy on 2009-02-02
Awesome that was what I was looking for, tyvm
:KS

Hmmm although the text file is a variable in my script that I run in a for loop, so;
```

IPs=~/file
for IP in ` < "$IPs" `; do
ping -c 5 $IP

```

Can I put the awk part in the variable, like;```
IPs=awk ' { print $1 } ' ~/file
```
Or maybe in the for loop expression?  o_0

---

### Post by slavik on 2009-02-02
please take a look at the awk manpage.

---

### Post by ghostdog74 on 2009-02-02
> **johnl said:**
> You can use awk:

```

cat myfile.txt | awk ' { print $1 } '

```

Will print only the first column in the file.

Hope this helps!

don't need the cat.
```

awk '{print $1}' file

```

---

### Post by ghostdog74 on 2009-02-02
> **madflyguy said:**
> Awesome that was what I was looking for, tyvm
:KS

Hmmm although the text file is a variable in my script that I run in a for loop, so;
```

IPs=~/file
for IP in ` < "$IPs" `; do
ping -c 5 $IP

```

Can I put the awk part in the variable, like;```
IPs=awk ' { print $1 } ' ~/file
```
Or maybe in the for loop expression?  o_0

if you want to parse a small file in bash , use the while read loop
```

while read line
do
 ping -c 5 "$line"
done < "file"


```

---

### Post by Cheesehead on 2009-02-02
'cut' is useful too
For example: cut -d ' ' -f1 input_source
See 'man cut'

---

### Post by madflyguy on 2009-02-03
I gave up using awk in the for loop. I cat all the contents (IP, subnet, gateway) to one file, awk that file to another, then mv the 2nd to the first. Ghetto I know but I haven't been able to get awk to behave nicely in my for loop.

---

### Post by johnl on 2009-02-03
Sorry, just came back to this post.  It should be easy to use awk in the way you described:

```

#!/bin/bash
IP_FILE="myfile.txt"

for IP in $(awk ' { print $1 } ' $IP_FILE); do
    ping -c 5 $IP
done

```

Hope this helps.

---

### Post by madflyguy on 2009-02-03
thanks I'll try that. I really don't know bash well enough on my own  :S

---

### Post by stroyan on 2009-02-03
It is pretty simple to do this with just bash.
The bash 'read' command will read words separated by the IFS characters.
Any extra words are added to the last variable used for 'read'.
So this code will read the first IP in each line into "IP" and the rest into "remainder".
```

IPs=~/file
while read IP remainder
do
  ping -c 5 $IP
done < $IPs

```

---

