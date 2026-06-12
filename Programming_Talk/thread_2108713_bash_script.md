---
title: "bash script"
date: 2013-01-25
forum: Programming Talk
---

### Post by singedwings on 2013-01-25
Please be gentle with me as this is my first try at this. I am trying to make a  script that will output a mythtv cutlist in the correct format to drop into mkvmerge.

Using this command ```
mythutil --getcutlist -q --chanid 11000 --starttime 20130101000000 | sed 's/Cutlist: 0-//g' | sed 's/-[^-]*$//' | sed 's/-/x/g' | sed 's/,/-/g' | sed 's/x/,/g'
```I get the cutlist in the correct format,```
5989-38425,40537-67861,69925-110833,112945-153061
``` but need to multiply each number by 2. I tried to script it```
#!/bin/bash

# Script to output mythtv cutlist in correct format for mkvtoolnix


CUT=$(mythutil --getcutlist -q --chanid 11000 --starttime 20130101000000 | sed 's/Cutlist: 0-//g' | sed 's/-[^-]*$//' | sed 's/-/x/g' | sed 's/,/-/g' | sed 's/x/,/g')

echo $(($CUT*2))
``` but it just gives me the result of the last number multiplied```
-193177
```Please could someone point me in the right direction to get each number multiplied by 2, thank you.

---

### Post by steeldriver on 2013-01-25
what does the 

```
mythutil --getcutlist -q --chanid 11000 --starttime 20130101000000
```

output look like? I would think a nice little awk expression would be easier than all those seds - and you could do the arithmetic natively in awk

---

### Post by singedwings on 2013-01-25
Without all the sed I get```
Cutlist: 0-5989,38425-40537,67861-69925,110833-112945,153061-164928
```

---

### Post by steeldriver on 2013-01-25
so maybe something like

```
awk -F"[:-,]" '{for (i=2; i<=NF;i++) printf "%d ", $i*2; printf "\n"}'
``````
echo "Cutlist: 0-5989,38425-40537,67861-69925,110833-112945,153061-164928" | awk -F"[:-,]" '{for (i=2; i<=NF;i++) printf "%d ", $i*2; printf "\n"}'
0 11978 76850 81074 135722 139850 221666 225890 306122 329856
```

---

### Post by singedwings on 2013-01-26
Thank you. I spent quite a while last night trying to get to grips with a few awk guides. I found it most inpenetrable and had to go look for a puncture repair kit for my head in the end! Would you mind explaining what the different bits of the code do please.

---

### Post by steeldriver on 2013-01-26
Hmm.. well TBH I only know just about enough awk to be dangerous but I will try:

awk basically splits text into records consisting of fields separated by delimiters (or 'field separators') and then allows you to perform actions according to certain rules. The default (I think) is to treat each line as a record with the fields separated by any whitespace ; however we can specify particular input field separator(s) using the -F parameter e.g.

```
awk -F "[:-,]" '*expression*'
```tells it to treat any character from the set *colon,hyphen,comma* as a delimiter. There's an alternative way to specify that using a 'begin rule' which is perhaps neater in an an actual script

```
awk 'BEGIN {FS="[:-,]"} ; *expression*'
```awk conveniently numbers the fields $1, $2, ... , $NF where NF is the total **n**umber of **f**ields it finds in the record. There is a special value $0 which represents the whole record. So in your case, with the [:-,] delimiter set,

```
$0 = Cutlist: 0-5989,38425-40537,67861-69925,110833-112945,153061-164928
$1 = Cutlist
$2 =  0
$3 = 5989
```and so on. Then it's straightforward to write an action that just uses a C-style for-loop and printf to loop over the numeric records (i=$2 to $NF) and print their doubles:

```
{for (i=2; i<=NF;i++) printf "%d ", $i*2; printf "\n"}
```ASIDE: awk also allows you to specify rules under which the action should be performed e.g. we could specify that we only want to perform the above action if the first field matches 'Cutlist', e.g.

```
awk 'BEGIN {FS="[:-,]"}; **$1 ~ /Cutlist/** {for (i=2; i<=NF;i++) printf "%d ", $i*2; printf "\n"}'
```which would be useful if we were reading a file that contained other stuff as well as the desired 'Cutlist:' line.

Hope this helps

---

### Post by singedwings on 2013-02-02
Wow, thank you! :p

---

