---
title: "Bash - if statement based on Ubuntu version"
date: 2011-07-13
forum: Programming Talk
---

### Post by Jonny87 on 2011-07-13
I looking for a  way to use the if statement based on what version of ubuntu is being used by the user.

i.e.
```
if [ "release" equal or grater than 10.04 ]; then'
    echo "This release is or is later than Ubuntu 10.04"
else
    echo "This release predates Ubuntu 10.04"
fi
```

The above is only an example to try and show the sort of out come I want to achieve.

I know how to find out the release version but am having trouble implementing it in this way.

---

### Post by Habitual on 2011-07-13
var1="10.4"
var2=`lsb_release -r | awk '{print $2}'`

if [ "var2 != "$var1" ]
do something.

---

### Post by Jonny87 on 2011-07-13
> **Habitual said:**
> var1="10.4"
var2=`lsb_release -r | awk '{print $2}'`

if [ "var2 != "$var1" ]
do something.

Not quite working,

It will run the first do something. but if I change the value of var1 to 11.10 as a test.
it still runs the first do something instead of the second (else) do something.

---

### Post by Jonny87 on 2011-07-13
This what I have so far
```

var1="10.04"
var2=`lsb_release -r | awk '{ print $2 }'`
if [ "$var2" != "$var1" ]; then
	echo "Yes this is 10.04 or above"
else
	echo "NO"
fi

```

on 10.10 or 11.04 I get "Yes this is 10.04 or above" but if I change var1 to 11.10 to test for system version lower than that stated in var1 I get "Yes this is 10.04 or above" instead of "NO"

I've also tried;
```

var1="10.04"
var2=`lsb_release -r | awk '{ print $2 }'`
if [ "$var2" -ge "$var1" ]; then
	echo "Yes this is compatable."
else
	echo "NO"
fi

```
But then I get;
```
[: 7: Illegal number: 10.10
NO
```
as the response.

---

### Post by Habitual on 2011-07-13
I don't think the comparative operator (!=) likes the ".04" in 10.04

Personally, I'd use 'lsb_release -c' ;)

---

### Post by Jonny87 on 2011-07-13
> **Habitual said:**
> I don't think the comparative operator (!=) likes the ".04" in 10.04

Personally, I'd use 'lsb_release -c' ;)

Oh ok but how can use that to decide the out put based on the version with out writing a condition for each Ubuntu code name.

is the there a way to remove the dot from the lsb_release -r output.

i.e.
```
var1="10.04"
var2=`lsb_release -r | awk '{ print $2 }'`
var3='command to change output of $var2`

echo var3
1104
```

The I could use the var3 instead. LOL does that make any sense.

---

### Post by Vaphell on 2011-07-13
directly
```
var2=$( lsb_release -r | awk '{ print $2 }' | sed 's/[.]//' )
echo $var2
1004

```

indirectly
```

var2=$( lsb_release -r | awk '{ print $2 }' )
var2=${var2/./}
echo $var2
1004
```

btw, stop using backticks and use $() instead

---

### Post by papibe on 2011-07-13
Considering that Bash doesn't do decimals very well, and comparing strings won't do it, I would separate the version in two variables.

I test this with a couple of machines and works:
```
#!/bin/bash

YEAR="10"
MONTH="04"

version=$(lsb_release -r | awk '{ print $2 }')

yrelease=$( echo "$version" | cut -d. -f1 )
mrelease=$( echo "$version" | cut -d. -f2 )

# for debug
# echo "Year: $yrelease"
# echo "Month: $mrelease"

if [ "$yrelease" -eq "$YEAR" ]; then
    if [ "$mrelease" -ge "$MONTH" ]; then
        echo "Yes, this is compatible."
    else
        echo "Not so fast."
    fi
else
    if [ "$yrelease" -gt "$YEAR" ]; then
        echo "Yes, this is compatible."
    else
        echo "Not so fast."
    fi
fi
```
Hope it helps.

---

### Post by Vaphell on 2011-07-13
no reason to play with fractions, going integer and comparing 1004 vs 1110 maintains the same relation 10.04 and 11.10 have

---

### Post by Jonny87 on 2011-07-13
> **Vaphell said:**
> directly
```
var2=$( lsb_release -r | awk '{ print $2 }' | sed 's/[.]//' )
echo $var2
1004

```

indirectly
```

var2=$( lsb_release -r | awk '{ print $2 }' )
var2=${var2/./}
echo $var2
1004
```

btw, stop using backticks and use $() instead

Thanks for your help. much appreciated. I'll go with the direct option as its already a big script so the less I lines i have to use the better.

---

