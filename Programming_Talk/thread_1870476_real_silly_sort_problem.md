---
title: "real silly sort problem"
date: 2011-10-27
forum: Programming Talk
---

### Post by crownedzero on 2011-10-27
trying to sort a file that contains monetary value in the 3rd field using a script but begins with a $:

sort -b (blank spaces) -n (numeric) -r (reverse) -k 3,2 (from field,letter) is sorting correcting except six figures beginning with 1 are placed at the bottom under 2 for example. I know it's something simple, where'd I trip up?

---

### Post by Arndt on 2011-10-27
> **crownedzero said:**
> trying to sort a file that contains monetary value in the 3rd field using a script but begins with a $:

sort -b (blank spaces) -n (numeric) -r (reverse) -k 3,2 (from field,letter) is sorting correcting except six figures beginning with 1 are placed at the bottom under 2 for example. I know it's something simple, where'd I trip up?

Some example data, maybe?

---

### Post by crownedzero on 2011-10-27
Simple shell script
```
#!/bin/bash/

echo Hello $LOGNAME

echo -e "\n"
more employee.txt

echo -e "\n"
echo -n Total number of employees:
sed -n '$=' employee.txt

echo -e "\n"

awk -F";" '{print $4, " ", $2, " " $1}' employee.txt | sort -nr
```

Column in question
```
$93100
$82001
$75600
$68500
$66050
$56500
$56500
$56000
$56000
$56000
$55508
$54500
$46000
$45210
$38000
$33930
$156003
$116400
```

---

### Post by emiller12345 on 2011-10-27
or you could just use a one-liner
```
cat temp.txt | sed 's/^\$//' | sort -n | awk '{print "$"$1}'
```

---

### Post by Arndt on 2011-10-27
> **crownedzero said:**
> trying to sort a file that contains monetary value in the 3rd field using a script but begins with a $:

sort -b (blank spaces) -n (numeric) -r (reverse) -k 3,2 (from field,letter) is sorting correcting except six figures beginning with 1 are placed at the bottom under 2 for example. I know it's something simple, where'd I trip up?

It is -k 3.2 that you want.

---

### Post by crownedzero on 2011-10-27
> **Arndt said:**
> It is -k 3.2 that you want.

Damn these old eyes ... thanks!

---

