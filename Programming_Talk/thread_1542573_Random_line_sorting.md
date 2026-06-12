---
title: "Random line sorting"
date: 2010-07-30
forum: Programming Talk
---

### Post by AstroLlama on 2010-07-30
I have a text file with an alphabetical list of 100+ entries. I'd like to sort it into a random order but the only tools I can find via scripts or CLI only give non-random options. Anyone have leads on how to do this?

Thanks in advance.

---

### Post by ghostdog74 on 2010-07-30
see [here]("http://ghostdog74.livejournal.com/6163.html") for an example.

---

### Post by ju2wheels on 2010-07-31
```

sort -R file.txt > random_sorted_file.txt

```

---

### Post by AstroLlama on 2010-07-31
I tried using sort -R but for it seems that that method grouped like terms together, so it was a random sort in alphabetical blocks, ie: dddd, ff ,hhh, e, rrr, aaaa, mm.

Also, discovered the "shuf" command, which was a one-liner (shuf < input_file > output_file) and worked great.

Ghostdog74, your script worked like a charm, and I also got a lesson in how to use awk. thanks for the responses!

---

### Post by ghostdog74 on 2010-07-31
> **AstroLlama said:**
> 
Also, discovered the "shuf" command, which was a one-liner (shuf < input_file > output_file) and worked great.

yes, shuf is another command you can use. take note that it is always available in every distribution.

---

