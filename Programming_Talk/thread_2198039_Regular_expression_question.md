---
title: "Regular expression question"
date: 2014-01-06
forum: Programming Talk
---

### Post by sha1sum on 2014-01-06
Hello guys, I need help with regular expressions.

Quick recap: we know that with advanced regular expressions, you can put something in parenteses to save a part of a regular expression. For example, the regular expression **[FONT=courier new]^(.)(.)\2\1$[/FONT]** will match the words like **noon** and **deed**. However, it wil also match a string like '**aaaa**' . I don't want that. Is there a way to specify that \1 and \2 _cannot_ be the same?

Additional info: the example is a simplification of the actual problem. A workaround with egrep -v won't work.

---

### Post by sha1sum on 2014-01-06
Okay, I´ve searched a lot on the internet and in various reference books, but I really couldn´t find a way to do this. Then I took a break, and ingested a copious amount of caffeine and sugar, and I came up with a solution for my own problem.

I´m going to try to write a script that counts the unique characters in a string. For a word like **deed** that would be 2, but for **aaaa** it would be only 1. Then I can filter based on that. That should also work for my bigger problem.

---

### Post by ofnuts on 2014-01-06
> **sha1sum said:**
> For example, the regular expression **[FONT=courier new]^(.)(.)\2\1$[/FONT]** will match the words like **noon** and **deed**..

It also, surprisingly, matches "boob", and I don't know why that word crossed my mind... :)

---

### Post by sha1sum on 2014-01-06
> **ofnuts said:**
> It also, surprisingly, matches "boob", and I don't know why that word crossed my mind... :)

lol it did for me too. The original example I wanted to write was: "I need a regular expression that matches **book**, but not **boob**". But then I realized; who in their right mind would prefer books over boob-s? So I changed it. :p

---

### Post by ofnuts on 2014-01-06
That explains how you came up with the **[FONT=lucida console]'(.)(.)'[/FONT]** syntax :)

---

### Post by steeldriver on 2014-01-06
Apparently you can do it with negative lookahead --> [http://stackoverflow.com/a/8057827](http://stackoverflow.com/a/8057827)

Based on that answer,

```

cat file
noon
book
deed
boob
aaaa

```

```

$ grep -Po '(.)((?!\1).)\2\1' file
noon
deed
boob

```

---

### Post by sha1sum on 2014-01-07
steeldriver you are awesome.

---

### Post by sha1sum on 2014-01-07
> **ofnuts said:**
> That explains how you came up with the **[FONT=lucida console]'(.)(.)'[/FONT]** syntax :smile:
ROFL! Never thought that regular expressions could get so... Freudian. LOL

---

### Post by kurum! on 2014-01-07
> **sha1sum said:**
> 
I´m going to try to write a script that counts the unique characters in a string. For a word like **deed** that would be 2, but for **aaaa** it would be only 1. Then I can filter based on that. That should also work for my bigger problem.

```

# echo "deed" | ruby -e 'puts gets.chomp.split("").uniq.size'
2
# echo "aaaa" | ruby -e 'puts gets.chomp.split("").uniq.size'
1




```

---

### Post by sha1sum on 2014-01-07
I made the following awk script:

```

# charcount: an awk script that filters based on the number of unique characters in a line

BEGIN{ FS="" }                   # Make every individual character a field
{ b=0; delete a                  # delete variable b and array a from the previous line
for(i=1;i<=NF;i++) a[$i]++       # Make an array entry for every character in the line
for (i in a) b++ }               # count the number of array entries: ie the number of unique characters
b==2                             # print the line if the number of characters equals 2

```

So then the command looks like this:

```

cat list.txt | egrep '^(.)(.)\2\1$' | awk -f charcount

```

This line will print words like **deed**, **noon** and **boob**, but not words like **book**, **blob**, and **bbbb**.

With that I was able to determine that the only four letter palindromes in the english language are the following:

> boob
deed
kook
noon
peep
poop
sees
toot

I don't know what "kook" is, but it was listed in /usr/share/dict/american-english

---

### Post by ofnuts on 2014-01-07
> **sha1sum said:**
> 
I don't know what "kook" is, but it was listed in /usr/share/dict/american-english

[http://en.wiktionary.org/wiki/kook](http://en.wiktionary.org/wiki/kook)

---

