---
title: "reading a file and taking each line as a new variable"
date: 2014-04-04
forum: Programming Talk
---

### Post by cbillson on 2014-04-04
I have a file, its format is fixed as follows:

```

data1 = 12345
data2 = 54321
data3 = 98765
data4 = 56789

```

(note there are spaces in the file either side of the = ) 

I'd like to be able to cat this from a shell script and be able to:

echo $data1

and get the output: 12345

I could use something like the code below, but it doesnt do quite what i need this time, as i'm not sure how to amend it to use the data left of the equal sign to be the variable name..

```

  cat myfile | while read line
  do
   echo $line
    IFS='=' read -ra ADDR <<< "$line"
    for i in "${ADDR[@]}"; do
      echo $i
    done

```

---

### Post by Vaphell on 2014-04-04
you can hack it using *source*

```
$ cat vars.txt
data1 = 12345
data2 = 54321
data3 = 98765
data4 = 56789
$ echo $data1 $data2 $data3 $data4

$ source <( sed 's/\s//g' vars.txt )
$ echo $data1 $data2 $data3 $data4
12345 54321 98765 56789
```

turn the file into shell compatible format with sed
load it as legit shell code
???
profit

another way
```
$ echo $data1 $data2 $data3 $data4

$ while IFS=' =' read k v; do declare $k=$v; done < vars.txt
$ echo $data1 $data2 $data3 $data4
12345 54321 98765 56789
```

---

### Post by steeldriver on 2014-04-04
... or possibly using eval (not sure whether that's more or less hackish?!)

```

$ while IFS="$IFS=" read -r name val; do eval "$name"="$val"; done < vars.txt
$ echo $data1 $data2 $data3 $data4
12345 54321 98765 56789

```

---

### Post by cbillson on 2014-04-04
> **Vaphell said:**
> you can hack it using *source*

```
$ cat vars.txt
data1 = 12345
data2 = 54321
data3 = 98765
data4 = 56789
$ echo $data1 $data2 $data3 $data4

$ source <( sed 's/\s//g' vars.txt )
$ echo $data1 $data2 $data3 $data4
12345 54321 98765 56789
```

turn the file into shell compatible format with sed
load it as legit shell code
???
profit

another way
```
$ echo $data1 $data2 $data3 $data4

$ while IFS=' =' read k v; do declare $k=$v; done < vars.txt
$ echo $data1 $data2 $data3 $data4
12345 54321 98765 56789
```

Cheers, the source option works spot on, though I'm concerned about the next commend "hackish"

> **steeldriver said:**
> ... or possibly using eval (not sure whether that's more or less hackish?!)

```

$ while IFS="$IFS=" read -r name val; do eval "$name"="$val"; done < vars.txt
$ echo $data1 $data2 $data3 $data4
12345 54321 98765 56789

```

This option works, however it fails if the data has spaces.

ie 

```

data1 = 123 456

```

---

### Post by Vaphell on 2014-04-04
> ... or possibly using eval (not sure whether that's more or less hackish?!)

no idea, but *declare $name=$val* should solve the dilemma ;-)


OP, describe your scenario with more details, eg the formats of values because that's what can make or break the approach.
sed+source becomes trickier if there are spaces allowed.
```
source <( sed -r 's/\s*=\s*(.*)/="\1"/' vars.txt )
```

this still works
```
while IFS="$IFS=" read n v; do declare "$n"="$v"; done < vars.txt
```
i'd stick with the loop.

Are your variables in sequence of name##? Wouldn't it be better to use array?

---

### Post by dragonfly41 on 2014-04-06
I have an similar need to read values from a config.ini file and I found ConfigObj to run in a python+sed script.

[http://www.voidspace.org.uk/python/articles/configobj.shtml](http://www.voidspace.org.uk/python/articles/configobj.shtml)

ConfigObj can run with a validation file.

---

### Post by cbillson on 2014-04-07
> **Vaphell said:**
> no idea, but *declare $name=$val* should solve the dilemma ;-)


OP, describe your scenario with more details, eg the formats of values because that's what can make or break the approach.
sed+source becomes trickier if there are spaces allowed.
```
source <( sed -r 's/\s*=\s*(.*)/="\1"/' vars.txt )
```

this still works
```
while IFS="$IFS=" read n v; do declare "$n"="$v"; done < vars.txt
```
i'd stick with the loop.

Are your variables in sequence of name##? Wouldn't it be better to use array?


Sorry, at the time of creating the post i was trying to keep the question simple, the data is more like this:


```

Name = bob
address = 123 any st
address1 = anytone
postcode = ab123cd
phone1 = 01234567890
phone2 = 07234567890

```



to be honest the only line with spaces is the address, and this isnt really the line i need, my main concern was the 'hackable' comment - and i assume this is because if someone managed to modify data.txt to be a shell script it could be ran unintentionally ?

Cheers
Chris

---

### Post by Vaphell on 2014-04-07
yes, that is the main reason to call it hackish. The content of the file becomes a bash compliant piece of code and is executed as if it was inlined in your script, which means in theory it can do anything bash can do. The defensive measures against exploits are on you.

to be honest the only way to be 100% safe is to never trust the user input and to never generate first-class variables this way. No matter how you slice it, at the end of the day you are still *eval*-ing text in some way.

Personally i'd go with safe associative array (key->value), should be convenient enough to use and would clearly indicate the origin of the data.

```
#!/bin/bash

declare -A cfg=()

while IFS="$IFS=" read -r k v
do
    cfg[$k]=$v
done < <( grep -P '^\s*\w+\s*=' vars.txt ) # filter out crap

echo "* configuration *"
for k in "${!cfg[@]}"
do
    printf "cfg[%s] = '%s'\n" "$k" "${cfg[$k]}" 
done
echo
echo "The dude's name is ${cfg[name]} and he lives at ${cfg[address]}, ${cfg[address1]}"


```

```
$ cat vars.txt
# this is config
   name = bob
  address = 123 any st
        address1 = anytone
postcode = ab123cd
# home
phone1= 01234567890
# work
phone2=07234567890

#data1 = 123 45
#data2 = 54321
#data3=98765
#data4 = 56789
$ ./cfg.sh 
* configuration *
cfg[phone1] = '01234567890'
cfg[phone2] = '07234567890'
cfg[address1] = 'anytone'
cfg[name] = 'bob'
cfg[address] = '123 any st'
cfg[postcode] = 'ab123cd'

The dude's name is bob and he lives at 123 any st, anytone
```

---

### Post by SeijiSensei on 2014-04-07
The problem with spaces in the targets can be avoided if you split the strings with awk using 
```
-F ' = '
``` rather than splitting on just the space character.

---

