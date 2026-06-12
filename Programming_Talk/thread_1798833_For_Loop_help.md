---
title: "For Loop help"
date: 2011-07-06
forum: Programming Talk
---

### Post by mistertee on 2011-07-06
Hi there, just looking for a quick assist on writing a for loop.

So I have flat file with a list of hostnames called "list1". This is just a small number of hosts within the population on my subnet. I then have a directory that contains a file for each hostname on my subnet. What I need to do is write a little for loop that looks only at the files for those hosts in "list1" that do not contain a certain attribute. What I am having problems with is defining $HOSTNAME as the hosts in "list1" and telling grep to list files that do not include the attribute.

So something like

!#/bin/bash
for
each $HOSTNAME in list1
do
grep -l 'all that do not contain this attribute' * .c
done

Can someone give me a little help please?

Thanks!!

---

### Post by pafoo on 2011-07-06
for item in $(grep "myattribute" /home/list1 | cut or whatever else);
do echo $item(or whatever);
done

---

### Post by mistertee on 2011-07-06
ah that makes sense.  thanks!

---

### Post by pafoo on 2011-07-06
Np, if it works please mark [SOLVED]

---

