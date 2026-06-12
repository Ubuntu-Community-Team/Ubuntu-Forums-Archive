---
title: "the horrors of regular expressions (please help with some string editing)"
date: 2010-06-16
forum: Programming Talk
---

### Post by negativ on 2010-06-16
I've spent a stupidly large amount of time failing to know what the hell I'm doing, here.

I have a text file that looks like this:

```
04 08: some random text here: blahblah1234blahblahblah
15 16: some other text here: blahblah1234blahblahblah
32 42: yet more text here: blahblah1234blahblahblah
04 08: text of unpredictable length here: blahblah1234blahblahblah
15 16: text here: blahblah1234blahblahblah

```{etc}


I want to delete everything UP TO and INCLUDING the first colon and the space behind it.

The result of that would look like this:

```
some random text here: blahblah1234blahblahblah
some other text here: blahblah1234blahblahblah
yet more text here: blahblah1234blahblahblah
text of unpredictable length here: blahblah1234blahblahblah
text here: blahblah1234blahblahblah
```

I'm trying to do this in a shell script, if that matters. Switching to perl or python or assembler or turbo pascal or esperanto is not really an option.

My sed/awk mojo is weak, and at this point I'm pretty much just killing braincells with google instead of learning anything.  I have actually learned a lot of things that I'm not trying to do, however.

halp!

---

### Post by DanielWaterworth on 2010-06-16
The regular expression is:

'^[0-9]{2} [0-9]{2}: '

You need to replace that with an empty string.

---

### Post by Bachstelze on 2010-06-16
```
firas@tsukino ~ % echo "04 08: some random text here: blahblah1234blahblahblah
firas@tsukino ~ dquote> 15 16: some other text here: blahblah1234blahblahblah
firas@tsukino ~ dquote> 32 42: yet more text here: blahblah1234blahblahblah
firas@tsukino ~ dquote> 04 08: text of unpredictable length here: blahblah1234blahblahblah
firas@tsukino ~ dquote> 15 16: text here: blahblah1234blahblahblah" | sed 's/^[^:]*:\ //g'
some random text here: blahblah1234blahblahblah
some other text here: blahblah1234blahblahblah
yet more text here: blahblah1234blahblahblah
text of unpredictable length here: blahblah1234blahblahblah
text here: blahblah1234blahblahblah

```

---

### Post by ju2wheels on 2010-06-18
```

#!/bin/bash

while read curLine; do
   echo ${curLine#*: };
done < inputFile.txt

```

or directly on a command line without saving:

```
 
while read curLine; do echo ${curLine#*: }; done < inputFile.txt

```

---

### Post by ghostdog74 on 2010-07-23
```

$ sed 's/^.[^:]*: //' file
some random text here: blahblah1234blahblahblah
some other text here: blahblah1234blahblahblah
yet more text here: blahblah1234blahblahblah
text of unpredictable length here: blahblah1234blahblahblah
text here: blahblah1234blahblahblah

$ awk '{sub(/^.[^:]*: /,"")}1' file
some random text here: blahblah1234blahblahblah
some other text here: blahblah1234blahblahblah
yet more text here: blahblah1234blahblahblah
text of unpredictable length here: blahblah1234blahblahblah
text here: blahblah1234blahblahblah


```

---

