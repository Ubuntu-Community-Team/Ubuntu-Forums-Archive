---
title: "regex"
date: 2008-03-06
forum: Programming Talk
---

### Post by finer recliner on 2008-03-06
is there a way in grep to match individual characters just once?

for example, i'd like to grep for the letters a, b and c in any order, but each letter should only appear once (or not at all) in the line.

can it be done?

---

### Post by a9bejo on 2008-03-06
> **finer recliner said:**
> is there a way in grep to match individual characters just once?

for example, i'd like to grep for the letters a, b and c in any order, but each letter should only appear once (or not at all) in the line.

can it be done?

for the letter 'a':
```

/^[^a]*[a]?[^a]*$/

```


all characters in one regex, I don't know

---

### Post by ghostdog74 on 2008-03-06
> **finer recliner said:**
> is there a way in grep to match individual characters just once?

for example, i'd like to grep for the letters a, b and c in any order, but each letter should only appear once (or not at all) in the line.

can it be done?

how about counting them? just an example.
```


echo "astrcingb" | awk 'BEGIN{FS=""}{
    for(i=1;i<=NF;i++) r[$i]++
   }
   END{
    for(i in r) {
      if (r[i] ==1 && i == "a" ) a=1
      if (r[i] ==1 && i == "b" ) b=1
      if (r[i] ==1 && i == "c" ) c=1           
    }
    if (a==1 && b==1 && c ==1) print "abc"
   }' 

```

---

### Post by naugiedoggie on 2008-03-06
> **finer recliner said:**
> is there a way in grep to match individual characters just once?

for example, i'd like to grep for the letters a, b and c in any order, but each letter should only appear once (or not at all) in the line.

can it be done?

Well, the short answer is probably "no."  It would be useful to know the goal in building this match.

It's trivial to match a single character, just use 

```
a{1}
```

and you'll match the single character.  

You have two challenges that I see.  You only want the single characters and you want to match in any order.  But is it your intention to extract the characters, or do you only want a boolean answer (yes they are there, no they aren't there)?  And is it true only if all three are there?

These questions are why it is hard to answer without knowing the purpose of the exercise.

Also, for all questions regex, the indispensable tool is the [regex coach]("http://weitz.de/regex-coach/").  It's free as in free speech as well as in free beer, and provides you with an interactive GUI for playing with your regex.

Thanks.

mp

---

