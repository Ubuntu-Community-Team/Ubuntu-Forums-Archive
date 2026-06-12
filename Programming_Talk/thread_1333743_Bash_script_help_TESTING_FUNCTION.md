---
title: "Bash script help TESTING FUNCTION"
date: 2009-11-21
forum: Programming Talk
---

### Post by Purell86 on 2009-11-21
Hey need your guys help.. Newbie at bash script here...... i need to develop a small script that will check if a variable contains a single letter and if so to echo an output.  i figured i would use the test function however i'm not sure if it can do a range.

for example i know this will not work
```

if [ $var = [A-Za-z] ]
then 
echo "your variable contains a letter"
else 
echo "your variable cantains a number"
fi


```

any hints on how i can get this to work

thanks in advanced

---

### Post by ghostdog74 on 2009-11-21
use case/esac
```

case $var in
 ? ) echo "one letter";;
esac

```

---

### Post by kaibob on 2009-11-21
When you say "a single letter" do you mean one and only one letter or do you mean one or more letters. If the latter, the following works with your script:

```
if [[ $var =~ [A-Za-z] ]]
```

BTW, ghostdog74's programming knowledge is infinitely superior to mine, so I'm sure his suggestion is the one to use.

---

### Post by Arndt on 2009-11-22
> **kaibob said:**
> When you say "a single letter" do you mean one and only one letter or do you mean one or more letters. If the latter, the following works with your script:

```
if [[ $var =~ [A-Za-z] ]]
```

BTW, ghostdog74's programming knowledge is infinitely superior to mine, so I'm sure his suggestion is the one to use.

But his suggestion matches all single characters, not just letters.

---

### Post by kaibob on 2009-11-22
Deleted by kaibob

---

### Post by slakkie on 2009-11-22
```

var=test

echo "$var" | grep e 

```

This will return output if 'e' is found in $var. Otherwise it will output nothing.

---

### Post by ghostdog74 on 2009-11-22
> **Arndt said:**
> But his suggestion matches all single characters, not just letters.

that could be fixed. but i will leave it to the OP. Its just the same as what he did. he should get it by now.

---

### Post by apmcd47 on 2009-11-24
[PHP]expr "$var" : '[a-z][A-Z]$'[/PHP]
It would match exactly one letter.

Andrew

---

