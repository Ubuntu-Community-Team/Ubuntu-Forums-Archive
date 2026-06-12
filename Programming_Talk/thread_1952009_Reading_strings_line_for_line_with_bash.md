---
title: "Reading strings line for line with bash"
date: 2012-04-03
forum: Programming Talk
---

### Post by Sworddragon on 2012-04-03
I want to write a script which can read comments from a file and parses them. The problem is that a for loop in bash interprets /* from beginning C-comments as directory listing. Here is an example script:

```
#!/bin/bash -e
IFS='
'
comment='/*
	C-Comment
*/'
i=1
for line in $comment
do
	echo "$i: $line"
	i=`expr $i + 1`
done
```


This is what I want to have:

```
1: /*
2: 	C-Comment
3: */
```


This is what I'm currently getting:

```
1: /bin
2: /boot
3: /dev
4: /etc
5: /home
6: /initrd.img
7: /lib
8: /lib32
9: /lib64
10: /libnss3.so
11: /lost+found
12: /media
13: /mnt
14: /opt
15: /proc
16: /root
17: /run
18: /sbin
19: /selinux
20: /srv
21: /sys
22: /tmp
23: /usr
24: /var
25: /virtualbox
26: /vmlinuz
27: /wine
28: 	C-Comment
29: deb/
30: doc/
31: src/
32: upstart/
```


Quoting $comment in the for loop doesn't help because $IFS isn't splitting anymore in this case. I'm getting then the following:

```
1: /*
	C-Comment
*/
```


Does anybody know how to solve this problem?

---

### Post by hakermania on 2012-04-03
Not sure about the solution, but I suggest
let i=i+1 instead of i=`expr $i + 1`

---

### Post by Vaphell on 2012-04-03
and i suggest (( i++ )) ;-)

besides pass stuff to while read x loop

```
echo/grep/sed/whatever ... | while read -r line; do echo $(( i++ )) "$line"; done
```
or
```
while read -r line; do echo $(( i++ )) "$line"; done < <( echo/grep/sed/whatever ... )
```

---

### Post by Sworddragon on 2012-04-03
> **hakermania said:**
> Not sure about the solution, but I suggest
let i=i+1 instead of i=`expr $i + 1`

> **Vaphell said:**
> and i suggest (( i++ )) ;-)

I want to try to keep as much dash compatibility as possible. This is why I'm using expr.


> **Vaphell said:**
> besides pass stuff to while read x loop

```
echo/grep/sed/whatever ... | while read -r line; do echo $(( i++ )) "$line"; done
```
or
```
while read -r line; do echo $(( i++ )) "$line"; done < <( echo/grep/sed/whatever ... )
```

I tried the first example and it is working, thanks :)

---

