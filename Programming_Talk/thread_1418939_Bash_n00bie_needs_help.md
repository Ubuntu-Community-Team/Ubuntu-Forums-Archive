---
title: "Bash n00bie needs help"
date: 2010-03-01
forum: Programming Talk
---

### Post by junke1990 on 2010-03-01
Hey guys I'm having a little trouble of getting output... Hope the script speaks for itself.

just in case:
1. select adapter
2. set adaptername to $int1
3. set HWaddr, mac address to a $, no idea how...

```
intlist=ifconfig |grep HWaddr
ELM=${#intlist[@]}

# select inet adapter
echo "Select your inet conn. [#]"
for ((i=0;i<$ELM;i++)); do
  echo $i. ${intlist[${i}]}
done
read item
int1=${intlist[${item}]}

```

---

### Post by junke1990 on 2010-03-01
I know there are specific commands for the regular expressions but which one do I need? any clue/hint?

---

### Post by schauerlich on 2010-03-01
The first line should read 
```
intlist=`ifconfig | grep HWaddr`
```
The grave accents (`) mean "execute this and put its output here"

---

### Post by laceration on 2010-03-01
for ((i=0;i<$ELM;i++))
should be
for ((i=0;i<ELM;i++))

---

