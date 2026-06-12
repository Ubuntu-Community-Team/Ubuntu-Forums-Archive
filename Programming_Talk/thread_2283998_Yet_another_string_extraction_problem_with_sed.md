---
title: "Yet another string extraction problem with sed"
date: 2015-06-26
forum: Programming Talk
---

### Post by texpat on 2015-06-26
This kind of question has been asked and answered quite a lot, but I just cant wrap my head around it, so please bear with me.

I have this chunk of text (html source code) I want to sift through and extract the text that sits at a certain position. The position is delimited by a forward slash ( / ) at the beginning and a double quote mark ( " ) at the end. I know that the relevant forward slash ist the 13th occurrence of that character in the text:

[FONT=Courier New]foo/foo/...13th slash follows**/**THIS IS THE STRING I WANT**"** bar[/FONT]

Doesn't have to be sed, of course. I suppose grep or some other tool would also do the job.

Thanks for reading and I appreciate any pointers.
Tx

---

### Post by Lars Noodén on 2015-06-26
Maybe awk could do it?

```

awk -F '/' '{ print $13 }'

```

That assumes that the slash is the only delimiter.

---

### Post by texpat on 2015-06-26
Good start :-) but the string I want ends with " and not /.
Your solution gets me the bit from the 13th slash - which is what I want - till the next slash - which gets me too much

---

### Post by texpat on 2015-06-26
oops, duplicate post.. sorry

---

### Post by Lars Noodén on 2015-06-26
You could then just delete the quote and everything that follows from that field:

```

awk -F '/' '{ sub( /".*$/, "", $13 ); print $13 }'

```

I expect that there is probably a more elegant way to do it.

---

### Post by steeldriver on 2015-06-26
If you really want to use sed ...

```

sed -E 's|(([^/]*/){13})([^"]*)".*|\3|'

```

but grep with PCRE might be neater

```

grep -Po '([^/]*/){13}\K.*(?=")'

```

---

### Post by texpat on 2015-06-26
> awk -F '/' '{ sub( /".*$/, "", $13 ); print $13 }'
Awesome, Lars! That does the job. Thanks!

---

### Post by texpat on 2015-06-26
> **steeldriver said:**
> If you really want to use sed ...

```

sed -E 's|(([^/]*/){13})([^"]*)".*|\3|'

```

Good! This also works. Thanks a ton!

> 
but grep with PCRE might be neater

```

grep -Po '([^/]*/){13}\K.*(?=")'

```
For some reason this doesn't stop at the quotation mark, but gets me the rest of the string, too.

---

### Post by steeldriver on 2015-06-26
Hmm... try making it non-greedy maybe?

```

grep -Po '([^/]*/){13}\K.*[COLOR=#0000ff]**?**[/COLOR](?=")'

```

---

### Post by texpat on 2015-06-29
> **steeldriver said:**
> Hmm... try making it non-greedy maybe?

```

grep -Po '([^/]*/){13}\K.*[COLOR=#0000ff]**?**[/COLOR](?=")'

```

Yep, that nailed it! Thanks! So now I have three solutions to my problem... decisions ;-)

---

