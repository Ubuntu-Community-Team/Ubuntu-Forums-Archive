---
title: "[SOLVED] Non-Global Append Sed"
date: 2007-12-02
forum: Programming Talk
---

### Post by darksizzle on 2007-12-02
I am working on a bash script that at one point uses sed to work on an XML file.  I need to add a large chunk of text after a tag (or whatever it's called, I dunno much about XML) that occurs multiple times.  So when I try to append I end up with my block of text after every time this tag is found.  What can I do to make sed only append after the first match?  I could just do a substitute and be easy on myself but I'd like to know the a correct way to do this.

Example: sed '/occurrence/aappended'
I want to append after this occurrence
appended
But not this occurrence
Or this occurrence 

Instead of:
I want to append after this occurrence
appended
But not this occurrence
appended
Or this occurrence
appended

Current Command: (Actual XML tag, fictional Variables, but I am using variable's hence the double quotes)

sed "/<\/RDF:Description>/a$VARIABLE" $FILE

Thanks in advance!!!

---

### Post by Trumpen on 2007-12-03
> **darksizzle said:**
>  What can I do to make sed only append after the first match?  I could just do a substitute and be easy on myself but I'd like to know the a correct way to do this.
```
sed "/<\/RDF:Description>/a$VARIABLE" $FILE
```


Have you already tried this:

```
sed "0,/<VRDF:Description>/a$VARIABLE" $FILE"
```

It should make sed to act only on those lines between number 0 and the first one containing the occurrence of your pattern.

Hope it helps.

---

### Post by darksizzle on 2007-12-03
...I really should have thought of that *shame* haha I've read way to much about sed to not think of that. thanks very much Trumpen!

---

### Post by darksizzle on 2007-12-05
Hehe actually I didn't try that command before I considered it good.  I read it again and realized you were talking about something different.  Luckily after talking to one of my friends, whom is much more competent with sed than I am, helped me with the answer that I'd like to share (since I put this as solved).

To have sed append to the first occurrence of an address and quit, apply this syntax.

sed -e '/address/ayouraddition' -e '/address(same one)/q' file

The -e tells sed that your trailing syntax is going to be a script.  If you don't apply -e twice sed is going to try to open /address/q as the file to open.  You have to remember that sed works line by line, reading a line, applying your commands to the line, and repeating to the next line.  So with that in mind you must realize that sed is going to read the first half of this syntax, then the other half.  So the first line it finds to append your addition to, it's also going to quit with the second half.  Hope someone finds this useful!

---

