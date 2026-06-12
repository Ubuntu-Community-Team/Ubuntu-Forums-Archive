---
title: "[SOLVED] Search/replace functionality in multiple subfolders"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by wordmagic on 2008-11-15
I am looking for something like this:
[http://www.funduc.com/search_replace.htm](http://www.funduc.com/search_replace.htm)

I am mainly interested in a utility that will search many (multilingual) text-based files and present one-line results. In Search and Replace one can define a file mask for the file extension as well as the path. If one could click the line and get extra context view it would be a bonus.

[IMG]http://www.funduc.com/images/srshot.gif[/IMG]

---

### Post by amauk on 2008-11-15
regexxer

---

### Post by jminker on 2008-11-15
This is a good find. Thanks!

Jim

---

### Post by amauk on 2008-11-15
no probs

Don't know if your windows program does regular expressions or not
(can't really tell from the screenshot) but it's a designed for the just the type of stuff you're doing

if you don't know about regular expressions, read up on it


*edit*
oops, thought you were the OP

---

### Post by wordmagic on 2008-11-15
Yep, the Windows program does regular expressions.

However, as I can see from the screenshot, one has to click on the file on the left to have its search occurrence displayed? 

[IMG]http://regexxer.sourceforge.net/images/regexxer-screenshot.png[/IMG]

What I need is displaying all occurrences from all files in sequential order the one after the other as you can see in this shot (by the way this is [another Windows application]("http://www.digitalvolcano.co.uk/textcrawler.html"), which is freeware)

[IMG]http://www.digitalvolcano.co.uk/tc1.jpg[/IMG]

---

### Post by amauk on 2008-11-15
Can't think of anything off-hand

If you can't find anything suitable, you could running your windows programs in wine

you could even theme wine to reflect your desktop appearance and I doubt you'd notice it wasn't a native app

---

### Post by wordmagic on 2008-11-15
I have recently installed Virtualbox (tried to test it was not exactly intuitive  so I did not), should I install Wine instead? I have a dual boot system with Win XP.

---

### Post by amauk on 2008-11-15
They're simple apps
I should think they'd work well under wine

---

### Post by wordmagic on 2008-11-15
And I just tested regexxer. Some problems:

1. It will display Greek characters from csv files as extended ASCII [Edit: solved by going to **Preferences -> File access** and using** ISO-8859-7** as **fallback encoding**]
2. Many csv files appear unsearchable as it "sees" them as binary.

---

### Post by amauk on 2008-11-15
> **wordmagic said:**
> 2. Many csv files appear unsearchable as it "sees" them as binary.
If these files were created on Windows, then they'll have the Windows specific line endings (LF+CR) rather than the Unix line endings (LF)

this is likely to be why the file is seen as binary

pick one csv file, and make a copy

in a terminal, run this on the copy
(IMPORTANT - the ^M is not what it looks like - you need to "make" the ^M by doing a Ctrl-V Ctrl-M)

```
sed -i 's/^M$//g' ./test_file.csv
```

If this works
(Ie. the copy now "appears" to be a text file to regexxer)

then run this to change all csv files

```
find . -type f -iname '*.csv' -exec sed -i 's/^M$//g' {} \;
```

---

### Post by wordmagic on 2008-11-15
Many thanks.

I tried WINE and Search and Replace, but with this one I cannot find a way to fix the extended ASCII display of Greek as well as the inability to type in Greek (when I type in Greek the strange-shaped characters next to the search word Program appear).

---

### Post by wordmagic on 2008-11-15
Pasted some fonts from Windows and it is solved.

---

