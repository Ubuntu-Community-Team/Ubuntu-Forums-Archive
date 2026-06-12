---
title: "Grep or Sed or else?"
date: 2014-01-27
forum: Programming Talk
---

### Post by Dominic--- on 2014-01-27
Hi,

I want to extract a specific set of lines within a huge configuration file.

!
interface FastEthernet6/48
 description test
 switchport trunk allowed vlan 100-250
 switchport private-vlan trunk native vlan 101
 switchport private-vlan trunk allowed vlan 100-250
 switchport private-vlan association trunk 100
 switchport private-vlan association trunk 101
 switchport mode private-vlan trunk
 [lots of info cut out]
!

Let's say I want to extract the description line and some of the switchport lines.
But in this config file there are some differences, for example, one interface hasn't got an description and the other hasn't got a specific switchport line I am interested in.

Which command do I need to grep a specific set of lines, with the '!' as separator for an specific area I want to grep?

---

### Post by justleen on 2014-01-27
basicly, you want the whole block between the exclamation marks, and then grep for description/switchport ?

---

### Post by Dominic--- on 2014-01-27
That is correct, and if possible, exclude the grep for that section if the correct switchport lines aren't available in that section.

---

### Post by steeldriver on 2014-01-27
It's not exactly clear what your file structure is, but I'd try something like

```

awk 'BEGIN{RS="!\n";FS="\n";OFS=FS} $3 ~ /^switchport/ {print}' *conffile*

```

to print the whole record or

```

'BEGIN{FS="\n"; RS="!\n"; OFS=FS} $3 ~ /^switchport/ {print $2, $3, $5}' *conffile*

```

to print the description + 1st and 3rd switchport lines for example

---

### Post by justleen on 2014-01-27
I'd go with above awk :)
The problem is that you're not sure what the output will be, and just matching to the next ! will not work with sed/grep.

You can use "grep -A 10 ! file.txt"  to get the next 10 lines after the match and then pipe it into another  grep to match  port/description. But that would only prove usefull if you know your search string is in the first 10 lines AND a block between !'s.
Awk is much better suited for tasks like this ...


```
 grep -A 10 '!' file.txt | grep -E "description|switchport" 
``` would grep description or  switchport in the 10 lines after the match on !

---

### Post by Dominic--- on 2014-01-27
Thanks guys, I am already much further. 

How can I use grep to start grepping from line two, respectively of the word I choose.
What I am searching for is a reverse grep of grep -A 10,

Instead of looking within the first 10 lines, now I want to start grepping from the 3th line.

---

### Post by steeldriver on 2014-01-27
you can use -B2 (for context **B**efore the match)

---

### Post by Dominic--- on 2014-01-27
Well just one step away from implementen my solution...

I grept it out to almost this point where I want to.

How do I erase 1 or more description lines when those are double? For example:
I want to make the statement that if a description line is found, and on the next line another one is found, the first find(s) are deleted, and the description line at the latter is shown.

 description 1234gA 6782 409123  << must leave
 description 1234BA 8111 409123  << must leave
 description 1234AB 9002 409543  << must stay
switchport etcetc
switchport etcetc
 description 2222DG 9002 409543 << must stay
switchport etc etc

---

### Post by justleen on 2014-01-28
Hm, not sure since they are not exactly the same. Guess my approach would be to split it per column and pass it trough uniq to get rid of duplicates\

Edit: Perhaps someone with more awk knowledge can awk-efy it?

---

### Post by steeldriver on 2014-01-28
You could use an associative array i.e. store successive values of "description" against a named key and then print the value at the end of processing each block

```
awk '$1=="description" {a[description]=$0}; END {print a[description]}'
```

---

