---
title: "building an array from a non-fixed string"
date: 2013-08-01
forum: Programming Talk
---

### Post by cbillson on 2013-08-01
if i had a file that contained lines such as:
[INDENT]
name=bob smith address=123 any st town=london phone=01234567890 notes=some notes about bob smith of any length containing potentially any data
[/INDENT]

I'm trying to get this data into an array, the real data contains many elements i'd like to strip out.

i've been playing around with this:
[INDENT]
```
  cat myfile | while read line
  do
   echo $line
    IFS='=' read -ra ADDR <<< "$line"
    for i in "${ADDR[@]}"; do
      echo $i
    done

```
[/INDENT]

however, it splits the data up as

$ADD[0] name
$ADD[1] bob smith address
[INDENT]
```
IFS=' =' 
```
[/INDENT]

Works a little too well :) and takes the space in every element, so i end up with an array of every single word..

Any help achieving this appreciated

---

### Post by ofnuts on 2013-08-01
Do a sed first and replace '([^ =]+=)' by '\n\1' (ie, insert a line feed before anything like  "foo="). Then each line is "foo=foo data".

---

### Post by cbillson on 2013-08-01
> **ofnuts said:**
> Do a sed first and replace '([^ =]+=)' by '\n\1' (ie, insert a line feed before anything like  "foo="). Then each line is "foo=foo data".

i'm not sure that will work for what i hope to achieve. However, thank-you very much for that command, it could come in extremely useful..

i'm thinking use SED in the way you describe to add a divider (|@: etc) then split down into an array using the code i've been playing with. this should leave me with an array of xxx=yyyy - i can work on that further from there.

thanks very much.

---

### Post by ofnuts on 2013-08-01
> **cbillson said:**
> i'm not sure that will work for what i hope to achieve. However, thank-you very much for that command, it could come in extremely useful..

i'm thinking use SED in the way you describe to add a divider (|@: etc) then split down into an array using the code i've been playing with. this should leave me with an array of xxx=yyyy - i can work on that further from there.

thanks very much.
Yes, adding a divider instead of a linefeed can do it, if you find a divider which is guaranteed to not occur in the data.

---

### Post by Vaphell on 2013-08-01
associative arrays for the win

```
$ declare -A array
$ array=()
$ while IFS='=' read -r key value; do array+=( ["$key"]="$value" ); done < <( sed -r 's/ (\w+=)/\n\1/g' in.txt )
$ for k in "${!array[@]}"; do printf "%s: %s\n" "$k" "${array[$k]}"; done
notes: some notes about bob smith of any length containing potentially any data
name: bob smith
phone: 01234567890
address: 123 any st
town: london
```

edit: seeing that you need different delimiter
```
#!/bin/bash

declare -A arr

while read -r ln
do
  arr=()
  while IFS='=' read -rd '|' key value
  do
    arr+=( ["$key"]="$value" )
  done < <( echo "$ln|" | sed -r 's/ (\w+=)/|\1/g' )
  echo "#$((++i)): ${#arr[@]} field(s)"
  for k in "${!arr[@]}"
  do
    printf "%s: %s\n" "$k" "${arr[$k]}"
  done
done < in.txt
```

```
$ ./data2arr.sh 
#1: 5 field(s)
notes: some notes about bob smith of any length containing potentially any data
name: bob smith
phone: 01234567890
address: 123 any st
town: london
#2: 5 field(s)
notes: some crap
name: jane doe
phone: 01234567890
address: 123 any st
town: prague
```

---

