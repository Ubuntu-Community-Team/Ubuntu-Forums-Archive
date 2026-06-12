---
title: "Parse XML into PIPE"
date: 2010-12-15
forum: Programming Talk
---

### Post by CrusaderAD on 2010-12-15
Does anyone know if it is possible to parse an XML feed into a PIPE delimited feed? Or maybe some info on parsing XML?

---

### Post by Arndt on 2010-12-15
> **CerealCypher said:**
> Does anyone know if it is possible to parse an XML feed into a PIPE delimited feed? Or maybe some info on parsing XML?

What do you mean by "PIPE delimited"?

What language do you want to use? Most have at least one interface for parsing XML.

For transforming XML into something else (or into some other XML form), you can use the program xsltproc. Then you don't do any parsing yourself (maybe some would say you do, but at least not the elementary syntactic XML parsing), but write actions to be performed for the various elements.

---

### Post by CrusaderAD on 2010-12-16
Hm, I'm not sure if xsltproc would work. By PIPE delimited I mean having an end result like this saved as a txt or csv file:

```
field1|field2|field3|field4
value1|value2|value3|value4
value1|value2|value3|value4
value1|value2|value3|value4
```

---

### Post by Arndt on 2010-12-16
> **CerealCypher said:**
> Hm, I'm not sure if xsltproc would work. By PIPE delimited I mean having an end result like this saved as a txt or csv file:

```
field1|field2|field3|field4
value1|value2|value3|value4
value1|value2|value3|value4
value1|value2|value3|value4
```

In that context, I usually call the character "vertical bar". "Pipe" is just a function it has in the shell. And csv means "comma-separated".

Anyway, it seems this is just what xsltproc is for. Have you tried?

---

### Post by CrusaderAD on 2010-12-16
I read the MAN page for it. I'll have to play with it some more, maybe I'm missing something. Thanks for the info! If there are any other suggestions, I would be interested!

---

