---
title: "Weird output of uniq"
date: 2010-05-17
forum: Programming Talk
---

### Post by dragos2 on 2010-05-17
I have a weird output. temp.txt contains some 'ls -l' output and the command below
instead of returning only user1 and user2 returns this:

```

cat temp.txt | awk '{ print $3}' | uniq
user1
user2
user1
user2
user1
user2

```

Any idea why ?

Solved: I was appending to temp.txt every time I was executing another piece of code.
```

if [[ -f temp.txt ]]; then
 rm -f temp.txt
fi 
touch temp.txt

```

---

### Post by Tony Flury on 2010-05-17
uniq works by omitting sequential identical lines from the output : 
```

man uniq

```

This should work
```

cat temp.txt | awk '{ print $3}' | sort | uniq

```

---

### Post by amauk on 2010-05-17
You can skip using uniq altogether, and just use
```
sort -u
```

uniq is good when you're piping in known sorted data (Ie. from a DB query)

---

