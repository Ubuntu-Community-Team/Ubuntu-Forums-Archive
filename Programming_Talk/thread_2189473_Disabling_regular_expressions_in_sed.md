---
title: "Disabling regular expressions in sed"
date: 2013-11-22
forum: Programming Talk
---

### Post by sha1sum on 2013-11-22
TL;DR:
Is it possible to run 'sed' without regular expressions, ie so that all characters are interpreted as literals? (Similar to the grep -F option)
-------
What I want to do looks like this:

```
for i in $(cat lines.txt); do
        sed 's/'$i'/'$count'/g' file.txt
        ((count++))
done

```

I tried to replace $i with a number, for a series of $i. But $i also contains metacharacters, which I want to be interpreted as literals, without having to backslash escape each one of them.

---

### Post by Lars Noodén on 2013-11-22
sed will work with a regular string of characters.  Maybe you were thinking something more like this:

```

sed -e "s/$i/$count/g" file.txt

```

But that will also match partial words too, not just whole words.

As for dividers, instead of / you can use other symbols. 

s///
s###
s@@@
s:::

---

### Post by Lars Noodén on 2013-11-22
I'm not sure of a way to do word boundaries in sed but you can in perl.

```

perl -pi.orig -e "s/\b$i\b/$count/g" file.txt

```

\b matches the 0-character boundary at the beginning or end of a word.

---

### Post by Vaphell on 2013-11-22
> **sha1sum said:**
> ```
[COLOR="#FF0000"]for i in $(cat lines.txt)[/COLOR]; do
        sed 's/'$i'/'$count'/g' file.txt
        ((count++))
done

```

```
while read -r ln; do ...; done < lines.txt
```
use *for* only when you can enumerate stuff in advance and when split-on-whitespace is not a potential problem, *while read* otherwise


as for the main question, maybe something like this?
```
while read -r rgx
do
  sed "s/$rgx/$count/g" file.txt 
  ((count++))
done < <( sed 's/./[&]/g' lines.txt )
```

or something like this
```
sed -f <( awk '{ gsub(".","[&]"); print "s/" $0 "/" NR "/g"; }' lines.txt ) file.txt
```

---

### Post by steeldriver on 2013-11-22
I think what sha1sum is asking about is having a shell variable that is expanded to a pattern containing characters that are special in sed, but should be treated as literal when matching e.g. (silly example)

```

$ i=".txt"
$ 
$ echo "mytxt.txt" | sed "s/$i/.csv/g"
m.csv.csv

```

i.e. it matches "any character followed by txt" instead of "literal period followed by txt". Again though perl seems to be the answer - in particular the Q modifier

```

$ echo "mytxt.txt" | perl -pe "s/**\\Q**$i/.csv/g"
mytxt.csv

```

Stolen from --> [http://stackoverflow.com/questions/7970702/simple-search-and-replace-without-regex](http://stackoverflow.com/questions/7970702/simple-search-and-replace-without-regex)

---

### Post by sha1sum on 2013-11-22
@ steeldriver ;-) that's exactly the problem I encountered.

I'm learning programming and I was wondering if it was possible. I realize that the problem can likely be solved with awk or perl, but I was trying to do it with a tool I'm familiar with: sed. In the future I want to learn awk and perl also. For now I've used a workaround: I've made a sed filter that backslash escapes all meta characters in the input file, then the problem is also solved.

Thanks you all. I'm learning programming and all your replies and general suggestions are very helpful. (Lars' suggestion of changing the single quote to a double quote I immediately implemented. Also Vaphell's advice of changing the for loop to a while-read loop I'm going to heed.) Things like that  help me expand my knowledge of scripting/programming. Cheers.

---

