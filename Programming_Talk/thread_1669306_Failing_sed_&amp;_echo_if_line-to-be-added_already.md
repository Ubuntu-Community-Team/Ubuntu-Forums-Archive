---
title: "Failing sed &amp; echo if line-to-be-added already exists"
date: 2011-01-17
forum: Programming Talk
---

### Post by Intrepid Ibex on 2011-01-17
Hi,

So this is quite simple: is there a way to fail *echo* and *sed* if the line that I was about to add already existed (wihtout going with eg. *grep*)?

Didn't find anything in the manpages.

Thanks beforehand,
Det

---

### Post by geirha on 2011-01-17
I don't understand what you mean. I think you'll have to explain more what you mean by adding a line with echo and sed.

---

### Post by Intrepid Ibex on 2011-01-17
I meant just using the other one :D.

e.g. *sed 's/$/add text to the end"/g' somfile*
or: *echo text >> somefile*

However I just did this by grepping and checking whether it returned any results.

---

### Post by geirha on 2011-01-17
Well, you have to actually look in the file to see if it contains your string already.

That sed appends text to the end of each line and outputs it to stdout, the echo appends a line of text to the file.

But anyway, I assume you meant that sed to be something like ```
sed -i '$a add text to the end' somefile
```

I don't know of any way to do that with sed. I'd just do
```
grep -Fq "some text" somefile || printf '%s\n' "some text" >> somefile
```

Or you could use awk
```
awk '/some text/{found=1;exit} END{if (!found) print "some text" >> FILENAME}' somefile
```

---

