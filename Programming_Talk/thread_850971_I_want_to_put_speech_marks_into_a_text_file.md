---
title: "I want to put speech marks into a text file"
date: 2008-07-06
forum: Programming Talk
---

### Post by J05HYYY on 2008-07-06
```


I want to be able to save speech marks into a file using the echo command:

[CODE]
#!/bin/sh
echo "This speech mark: " and this speech mark: " doesn't go into MyFile!" >> $MyFile
```

At the moment the text in "MyFile" reads:
```
This speech mark:  and this speech mark:  doesn't go into MyFile!
```

Instead ... i want it to read:
```
This speech mark: " and this speech mark: " does go into MyFile!
```

... hopefully you get the idea ... any help would be great :confused:

---

### Post by lisati on 2008-07-06
Try:```

echo This speech mark: \" and this speech mark: \" doesn't go into MyFile!" >> $MyFile
```

---

### Post by J05HYYY on 2008-07-06
Cheers for the immediate response! Worked a charm - guess I should read things up a little more before asking next time :P

---

### Post by wrtpeeps on 2008-07-06
> **J05HYYY said:**
> Cheers for the immediate response! Worked a charm - guess I should read things up a little more before asking next time :P

Yep. If you want to actually print " you escape them with a \.

---

### Post by lisati on 2008-07-06
I'm glad that it worked.

I had a hunch based on something I'd read on the forums some time ago, checked it on my machine, saw that it looked promising, and then posted the response.....


Feel free to ask questions! Someone might remember seeing something and point you in a useful direction.

---

### Post by J05HYYY on 2008-07-19
Is there a way to do the same within a search?

e.g.

```
expr index "\""
```

When I load a file, I want to be able to search for the position of a single quotation mark ... is this possible? I'm confused at the moment. :confused:

---

### Post by mssever on 2008-07-19
> **J05HYYY said:**
> Is there a way to do the same within a search?

e.g.

```
expr index "\""
```When I load a file, I want to be able to search for the position of a single quotation mark ... is this possible? I'm confused at the moment. :confused:
Your question is vague. What are you using to load a file? the method of searching varies by program.

Your code example results in a syntax error. ```
expr '"'
``` prints a double quote character, but I don't see how expr is relevant to your question in the first place or what you're hoping to accomplish using it.

---

### Post by J05HYYY on 2008-07-19
Whoops, sorry I see your point. The code I gave was a little weird

basically I know how to put speech marks into a file now. just I don't know how to take them out again.

I assume your correct in saying it varies from program to program. I guess the question I should be asking is "how do I search for speech marks in a file?" but I got it now anyway after reading the manpage and a little frustration due to my bad programming :)

```
expr index 'abc"abc' '"'
```

---

### Post by nanotube on 2008-07-20
aren't these " things usually called "quotes" ? :)

---

### Post by J05HYYY on 2008-07-20
speech marks/quotes/quotation marks ... it's all gravy.:lolflag:

---

