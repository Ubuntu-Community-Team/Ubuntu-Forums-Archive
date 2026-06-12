---
title: "Read field by field between field separator"
date: 2013-06-03
forum: Programming Talk
---

### Post by punticci on 2013-06-03
Hi, is there a way to read the fields between the field separator? I mean, for example, i have a file structured in this way:
```
#@;field1#@;field2#@;field3#@;field4#@;field5#@;field6
```
ok, now i want to make something like this : 
```
temp=${ENDROW##*#@;}          field1=`printf '"%s"\n' "${temp%%#@;*}"
```
where ENDROW is because i made a while condition before: ```
ENDROW=""
while read ENDROW;
do
temp=${ENDROW##*#@;}          field1=`printf '"%s"\n' "${temp%%#@;*}"
```
So i have to read the first field and find that between the first #@; and the second #@; there is the filed1 and go on in this way. The solution i posted doesn't go and the fields are empty :( any suggestion?Thanks

---

### Post by steeldriver on 2013-06-03
Not sure what you're asking exactly? you can read into an array something like

```
IFS=";" read -a array < fieldfile
```

Then strip the #@ substrings with ${field//#@/}

```
$ for field in ${array[@]}; do echo "${field//#@/}"; done

field1
field2
field3
field4
field5
field6

```

Or you could try

```
**IFS="#@;"** read -a array < fieldfile
```

then you don't need to strip anything (and also don't get the empty 0th field)

```

$ for field in ${array[@]}; do echo "$field"; done
field1
field2
field3
field4
field5
field6

```

---

