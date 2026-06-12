---
title: "Python - Remove Lines if Substring Exists"
date: 2009-02-10
forum: Programming Talk
---

### Post by glj12 on 2009-02-10
Quick Python question (hopefully),

I wish to remove any given line from a text file if it contains the substring I specify. Assume that there is a line that states: [http://news.google.com/nwshp?hl=en&tab=wn](http://news.google.com/nwshp?hl=en&tab=wn) and my substring to search for is 'google'. Therefore, I wish for it to remove the entire line where [http://news.google.com/nwshp?hl=en&tab=wn](http://news.google.com/nwshp?hl=en&tab=wn) resides.

How might I go about this?

---

### Post by Wybiral on 2009-02-10
You can test if a string is a substring of another with the 'in' operator:

```

print 'larger' in 'some larger string'

```

You can figure out the rest (this sounds like possible homework and your question is too vague)

---

### Post by glj12 on 2009-02-10
Contrary to popular belief, "simple" questions don't always infer homework problems. I am new to python, and wanted a quick way to sort my data that I have collected for one of my projects.

Regards

Edit:

I figured it out:

newFile = open("rawr.txt", 'w')

for line in open("traverse.txt"):
	if not "word" in line:
		print >>newFile, line[:-1]
		
# Thar be dragons here

---

### Post by scooper on 2009-02-19
> **glj12 said:**
> print >>newFile, line[:-1]

One minor point.  Rather than assume the last character is a newline, I might do this instead.

```
newFile.write(line)
```

---

