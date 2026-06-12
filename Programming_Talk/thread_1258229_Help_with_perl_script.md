---
title: "Help with perl script"
date: 2009-09-04
forum: Programming Talk
---

### Post by hanlin on 2009-09-04
I have a line of text, something like:

<td><bla>word1</td><td><bla>word2</td><td><bla>word3</td>

I would like to extract out word1, word2, and word3. The blas are different texts.
This is what I have:
($d1) = <end.of.bla>(\b.+\b)<\/td>/;

The problem with this is that it produces:

word1</td><td><bla>word2</td><td><bla>word3

So it searches to the last occurrence of </td>. How can I extract just the words? Thanks.

---

### Post by ghostdog74 on 2009-09-04
not Perl but gawk
```

# echo "<td><bla>word1</td><td><bla>word2</td><td><bla>word3</td>" | awk -F"</" '{for(i=1;i<=NF;i++){gsub(/.*>/,"",$i)}}1'
word1 word2 word3


```

---

### Post by unutbu on 2009-09-04
And in perl:
```
echo "<td><bla>word1</td><td><bla>word2</td><td><bla>word3</td>" | perl -F"</" -ape '$_=join(" ", map {s/.*>//; $_} @F)'
```

---

### Post by slavik on 2009-09-04
why not the following:

```

echo "<td><bla>word1</td><td><bla>word2</td><td><bla>word3</td>" | perl -pe 's/<.*?>/ /g'

```

---

