---
title: "shell scripting"
date: 2012-02-23
forum: Programming Talk
---

### Post by .vogue on 2012-02-23
I am a newbie in shell scripting. I want to know if I have a file which is full of this kind of pattern 
file start:   [{'name': 'american pie'}, {'name': 'national geographic'}, {'name':'football'},{'name': 'and_so_on'},redundant}] file end

how do I parse the file to get 
a) 
name: american pie
name: national geographic
name: football
name: and_so_on

AND ALSO

b) 
american pie
national geographic 
football
and_so_on

---

### Post by ofnuts on 2012-02-23
You can use sed to remove the punctuation you don't need:

```

sed -e "s/': *'/:/g" -e "s/'}, *{'/\n/g" -e "s/^\[{'//" -e "s/'},[^:]*}\]/\n/" <file

```

---

### Post by .vogue on 2012-02-23
Thank you ofnuts! But, how do I parse the 'name' from it?

---

### Post by Vaphell on 2012-02-23
you can use another sed

```
... | sed -r 's/^(.*):(.*)$/col1=\1 col2=\2/'

col1=name col2=american pie
col1=name col2=national geographic
col1=name col2=football
col1=name col2=and_so_on

```

you can use awk

```
... | awk -F: 'NF==2 {print "col1 =", $1, "col2 =", $2 }'

col1 = name col2 = american pie
col1 = name col2 = national geographic
col1 = name col2 = football
col1 = name col2 = and_so_on
```

you can read the output in while loop
```
... | while IFS=: read c1 c2; do echo "col1=$c1 col2=$c2"; done
 
col1=name col2=american pie
col1=name col2=national geographic
col1=name col2=football
col1=name col2=and_so_on
col1= col2=
```

---

### Post by .vogue on 2012-02-23
Now, I, somehow, got the idea! Thanks Vaphell!

---

