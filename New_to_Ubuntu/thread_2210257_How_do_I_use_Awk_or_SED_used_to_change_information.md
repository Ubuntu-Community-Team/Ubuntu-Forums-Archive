---
title: "How do I use Awk or SED used to change information in a text file?"
date: 2014-03-09
forum: New to Ubuntu
---

### Post by Herbon on 2014-03-09
Greeting

I recently downloaded software to export text from a ".PDF" file to a ".txt" file
When viewed the .txt file shows the following

```

Billing address: 1234 W4                 Case: 1011111
New York NYC 10011-1014


```

I would like to change it to........  

```

Case: 1011111
Billing address: 1234 W4                 
New York NYC 10011-1014


```

Checked a few sited, but was only to found a couple of commands to got close.

```

# Remove space and/or tab characters at the end of line
sed -i 's/[ \t]*$//' file

```

 /\ from commandlinefu.com

Thanks

---

### Post by Vaphell on 2014-03-09
assuming it's about 2 last 'words' in the 'Billing' line
```
awk '/Billing/{ print $(NF-1), $NF; NF-=2; }; 1'
```

---

### Post by Herbon on 2014-03-09
> **Vaphell said:**
> assuming it's about 2 last 'words' in the 'Billing' line
```
awk '/Billing/{ print $(NF-1), $NF; NF-=2; }; 1'
```


Ok it did this

```

Billing address: 1234 W4Case: 1011111 
New York NYC 10011-1014

```

So it appears the "Billing" and "Case" in on the same line. Is it possible to move "Case" to a new line or delete it??

PS the date in the file never changed just what I seen in the CLI changed, what give??

---

### Post by Vaphell on 2014-03-09
i get this in terminal
```
$ echo "Billing address: 1234 W4                 Case: 1011111
New York NYC 10011-1014" | awk '/Billing/ { print $(NF-1), $NF; NF-=2; }; 1'
Case: 1011111
Billing address: 1234 W4
New York NYC 10011-1014
```

awk doesn't make changes in place, you need to go with *awk '...' original.file > modified.file*  and then rename modified.file to original.file.


so maybe this
```
sed -r '/^Billing/ s/(.*[^ \t])\s*(Case:.*)$/\2\n\1/'
```

```
$ echo "Billing address: 1234 W4                 Case: 1011111
New York NYC 10011-1014" | sed -r '/^Billing/ s/(.*[^ \t])\s*(Case:.*)$/\2\n\1/'
Case: 1011111
Billing address: 1234 W4
New York NYC 10011-1014
```

additional -i switch should modify the file in place

---

### Post by Herbon on 2014-03-09
> **Vaphell said:**
> i get this in terminal
```
$ echo "Billing address: 1234 W4                 Case: 1011111
New York NYC 10011-1014" | awk '/Billing/ { print $(NF-1), $NF; NF-=2; }; 1'
Case: 1011111
Billing address: 1234 W4
New York NYC 10011-1014
```

awk doesn't make changes in place, you need to go with *awk '...' original.file > modified.file*  and then rename modified.file to original.file.


so maybe this
```
sed -r '/^Billing/ s/(.*[^ \t])\s*(Case:.*)$/\2\n\1/'
```

```
$ echo "Billing address: 1234 W4                 Case: 1011111
New York NYC 10011-1014" | sed -r '/^Billing/ s/(.*[^ \t])\s*(Case:.*)$/\2\n\1/'
Case: 1011111
Billing address: 1234 W4
New York NYC 10011-1014
```

additional -i switch should modify the file in place

Cool both worked, but I brain dumped something

I wanted it to be...

```

Case: 1011111

Billing address: 1234 W4 New York NYC 10011-1014
```

And viewing the information you post helped make sense out of the following site

[http://www.vectorsite.net/tsawk_2.html#m2](http://www.vectorsite.net/tsawk_2.html#m2)

---

### Post by Vaphell on 2014-03-10
```
awk '/^Billing/ { print $(NF-1), $NF, "\n"; NF-=2; r=$0; getline; print r, $0; }'

sed -r '/^Billing/ { N; s/(.*[^ \t])\s*(Case:.*)\n(.*)/\2\n\n\1 \3/; }'
```

---

