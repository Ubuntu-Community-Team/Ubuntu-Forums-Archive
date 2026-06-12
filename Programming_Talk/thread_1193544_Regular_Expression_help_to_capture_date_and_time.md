---
title: "Regular Expression help to capture date and time"
date: 2009-06-21
forum: Programming Talk
---

### Post by WinterWeaver on 2009-06-21
I'm quite bad at regular expressions, but find that i need one for a project that I'm working on at this point, and I'm hoping someone can assist me.

The regular expression needs to try and extract date and time from text. Thing is, the format for the date and time is not consistant.
For example, one piece of text may read, "6pm on 21 June", whilst the next piece would read "21/06/2009 18:00"

In other words, I need to try and capture different formats of date and time, from a large piece of text.

Would anyone be up to the challenge to assist me?

oh, and btw... I have to use python for this, so please dont tell me to use perl regex:common :P

---

### Post by .Maleficus. on 2009-06-21
You might like [this page]("http://www.regular-expressions.info/dates.html").  Multiple regex's to match valid dates.  I can't help much with the other format though, I'm just starting with regex myself.

---

### Post by WinterWeaver on 2009-06-21
Thanks, I have found that page before. I tried to write expressions for other formats... but after about 1 min my eyes goes a little fuzzy O.o

---

### Post by smartbei on 2009-06-21
Well, there is a regex module for python - import re.
This actually sounds like more of a language processing problem than a regex problem. The hard part seems to be figuring out the format, and not extracting the data. Does the file contain only several different formats? Or are there many, many different ones?

Also, is this a homework problem (sounds a bit like it) - if so, we can still provide support but to a lesser extent.

---

### Post by WinterWeaver on 2009-06-21
> **smartbei said:**
> Well, there is a regex module for python - import re.
This actually sounds like more of a language processing problem than a regex problem. The hard part seems to be figuring out the format, and not extracting the data. Does the file contain only several different formats? Or are there many, many different ones?

Also, is this a homework problem (sounds a bit like it) - if so, we can still provide support but to a lesser extent.

Nope, not homework. I'm writing a script for a client that needs to parse RSS feeds from various sources. The feed contains Event information. The thing is that many of the feeds dont have date fields, and the date and time is written along with the rest of the description.

---

### Post by smartbei on 2009-06-21
Well, if it is consistent for a particular feed, then I would use time.strptime() to convert from a string to the time, and save the necessary format for each feed. Otherwise, I see two options:
[LIST=1]
[*] You could try either using really complex processing that tries to extract the time from the text using heuristics, or...
[*] You could just support a bunch of different time formats, and search for all of them in the text.
[/LIST]
The second options seems to me like a good choice, since it is far less work, assuming a finite (and relatively small) number of formats. Writing formats for strptime is quite simple - For example, to convert the string "21/06/2009 18:00" to time:
```

import time
string = "21/06/2009 18:00"
time_obj = time.strptime(string, "%d/%m/%Y %H:%M")

```
Supporting more formats could be as easy as making a list and looping... Again, depending on how it looks in the actual data.

---

### Post by WinterWeaver on 2009-06-21
Yes, your second solution does seem like the better one at this point. I am using strptime to for some of the feeds that actually have a date field. Unfortunately the majority of them dont.

Thanks, I'll see what I can come up with.

---

