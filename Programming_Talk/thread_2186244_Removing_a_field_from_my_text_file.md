---
title: "Removing a field from my text file"
date: 2013-11-06
forum: Programming Talk
---

### Post by CaptainMark on 2013-11-06
I have a text file of all of my Google contacts and I'm trying to remove the 26th field from every line of the text file excluding the first one using a comma as a field separator.

I'm fairly certain that awk is the correct tool to use, perhaps by recreating the file minus the 26th field, but I've never used it and I've no idea where to start.

If anyone could help me it would be much appreciated.

Many thanks
Mark

---

### Post by sudodus on 2013-11-06
You could do it in a visual way by importing the file into a spreadsheet program, LibreOffice Calc or gnumeric, and use the commas as separators and then removing the 26th column.

You could do it with the shell command cut. Use something like this

```
cut -d , -f 26 --complement
```

Read ```
man cut
``` for more details

---

### Post by Lars Noodén on 2013-11-06
Here's one way to do it in awk, too:

```

awk 'BEGIN { FS=","; OFS="," } { $26=""; sub( /,,/, "," ); print $0}' 

```

Edit: it assumes no empty fields elsewhere

---

### Post by CaptainMark on 2013-11-07
Unfortunately there are empty fields, the cut tool worked fine and I normally prefer cli tools for this sort of work but importing it into a spreadsheet gave me much more fine control in a much shorter time so thanks for that suggestion, I didn't know you could do that with these files

Many Thanks

---

### Post by sudodus on 2013-11-07
You are welcome :-)

---

### Post by Lars Noodén on 2013-11-07
LOL  We should have thought of a spreadsheet, too.

---

