---
title: "What's the best program for string/text analysis?"
date: 2012-07-22
forum: Programming Talk
---

### Post by J-E-N-O-V-A on 2012-07-22
I want to analyse text documents finding things such as the most occuring characters and words and any other repetitions. Do you know any good programs for this?

---

### Post by trent.josephsen on 2012-07-22
Perl

---

### Post by woostopalypse on 2012-07-22
I recommend bash for counting words. I found an example from [stackoverflow]("http://stackoverflow.com/a/4495357")

```

sort name_of_file|sort|uniq -c|sort -r|head -10

```

This will order the most occurring words from the first 10 lines of the file (starting at the beginning of the file). Copy and paste that into the command line and replace "name_of_file" with the text file you wish to use.

If you need to do more complex filtering of text, use regular expressions. Perl is a good choice. Python, ruby, and java support regular expressions too.

---

### Post by trent.josephsen on 2012-07-22
> **woostopalypse said:**
> I recommend bash for counting words. I found an example from [stackoverflow]("http://stackoverflow.com/a/4495357")

```

sort name_of_file|sort|uniq -c|sort -r|head -10

```

This will order the most occurring words from the first 10 lines of the file (starting at the beginning of the file).

No, that lists the 10 most common *lines* found in the file in descending order. You need more fancy stuff to operate on words instead of lines.

Also, while I've seen many a useless `cat`, this is the first time I've seen a useless `sort`. ;) Granted, sorting the same thing twice probably doesn't affect performance much.

---

### Post by Vaphell on 2012-07-22
> You need more fancy stuff to operate on words instead of lines.

nothing *tr* or *sed* won't solve
```
tr '[:space:]' '\n' | sort ...
sed -r 's/\s+/\n/g' | sort ... 
```

---

### Post by trent.josephsen on 2012-07-23
I didn't say it couldn't be done, I just said it would be more fancy. :)

---

### Post by Vaphell on 2012-07-23
i am not sure if 'replace whitespace with newline' meets the fanciness criteria ;-)

---

### Post by trent.josephsen on 2012-07-23
I'd say tr and sed are generally fancier (more complex) than sort, uniq, or head.

---

### Post by steeldriver on 2012-07-23
> **trent.josephsen said:**
> Also, while I've seen many a useless `cat`, this is the first time I've seen a useless `sort`. ;) Granted, sorting the same thing twice probably doesn't affect performance much.

I believe the first one is sorting the *lines*... the second one is sorting the *counts *from uniq -c... so not useless (I have done the same thing to search for repeated messages in a log file)

---

### Post by spjackson on 2012-07-23
> **steeldriver said:**
> I believe the first one is sorting the *lines*... the second one is sorting the *counts *from uniq -c... so not useless (I have done the same thing to search for repeated messages in a log file)
That would be the third one, and would make more sense as 'sort -nr' rather than 'sort -r'. The second one is useless no matter how you look at it.

---

### Post by steeldriver on 2012-07-23
doh! I didn't even see the first one!

/hangs head in shame

---

### Post by Some Penguin on 2012-07-29
Of publicly-available, free stuff, I'd have to suggest taking a look at the [Stanford University NLP suites]("http://nlp.stanford.edu/software/index.shtml").

Defining a "word" is actually not that easy, if we're talking about parsing full text.  For instance, if we take the following text:

> 
"3... 2... 1..." chanted the audience, hoping to become famous on NBC's "Good Morning Today".  Some were dancing to N.W.A. tunes for no apparent reason other than, perhaps, a lack of anything better to do.

``Oh bother,'' said the aliens' commander as he hoisted his Mega-Laserium 5K and disintegrated Mr. Christopher Robin's perpetually-depressed donkey -- moments before he destroyed the rest of the Hundred Acre Wood and ordered the flotilla to proceed to a famous address on Pennsylvania Ave. in Washington, DC.


Would 'N.W.A.' be considered a single word, or broken apart?  Is "Mega-Laserium" a single word?  'Perpetually-depressed'?  Should it be "aliens'", or would the apostrophe be dropped?  Likewise, is "Robin's" a single word/token?  Do we retain the periods in Mr. and Ave.?

If you want to be that precise, you should probably look into what's well-supported with relevant libraries.  NLP isn't a new field, so there's been a lot of relevant code.  The aforementioned Stanford code is pretty decent at this area.

---

### Post by codemaniac on 2012-07-29
> **J-E-N-O-V-A said:**
> I want to analyse text documents finding things such as the most occuring characters and words and any other repetitions. Do you know any good programs for this?

Back in the early days of UNIX, the folks messing around with this new operating system quickly found a niche to fill;
People at universities needed a decent text processing environment. Because of the processing speed and amount of memory in computers those days, programs had to be small and, relatively, simple. This led to UNIX's famous design philosophy: "a suite of tools working together to get a job done." By combining several small, but powerful, text processing tools through UNIX pipes, text can be transformed and manipulated in a myriad of ways.

For day to day text processing jobs you will find the below utilities handy .
awk ,perl, grep , sed , sort , cat , tr , find , and many more ..

---

