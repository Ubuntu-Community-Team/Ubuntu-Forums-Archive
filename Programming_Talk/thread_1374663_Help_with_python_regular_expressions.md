---
title: "Help with python regular expressions"
date: 2010-01-07
forum: Programming Talk
---

### Post by aquavitae on 2010-01-07
I need to write a script in python (2.5) to read text files with fixed width columns.  Since the number of columns and there widths are not necessarily known in advance, I need to write it to interpret the column widths.  The way I want to do it is to read through each line looking for where the word breaks are, and use the most common breaks to calculate the column widths.  The problem I'm having is that I can't figure out how to write a regular expression to find the positions of the word breaks. Since some of the columns might be right-aligned, I want to find the position of the start and end of each word.  I'm having a bit of trouble with the regex itself, but I also can't seem to get it to find each occurence - It only finds the first.  If I use re.findall it only returns a list of matches, not their positions.  Can anyone give me some advice on this?

---

### Post by wmcbrine on 2010-01-07
If there are no spaces or tabs within columns, and each column is separated from the next by at least one space or tab, then the simplest thing would be to use .split() on each line.

But if you want to make a list of all spaces in a line:

```
spaces = [index for index in xrange(len(line)) if line[index] == ' ']
```

---

### Post by aquavitae on 2010-01-07
Thanks. I've actually just figured out the regex I need: '\b\S+'. And I need to use re.finditer to scan for all matches.  The problem is that some cells in the data may be empty.  I was using split() until I realised that the data was getting jumbled because of missing fields.

---

