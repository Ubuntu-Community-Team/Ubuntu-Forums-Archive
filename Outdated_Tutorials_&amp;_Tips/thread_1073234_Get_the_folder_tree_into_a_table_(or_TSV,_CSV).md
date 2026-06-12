---
title: "Get the folder tree into a table (or TSV, CSV)"
date: 2009-02-18
forum: Outdated Tutorials &amp; Tips
---

### Post by robajz on 2009-02-18
If you like me are looking for the solution on web first, this might save you half an hour of your precious life! It's not the command ls as I thought.

I was trying to find duplicates of my pictures on the drive - taking the simple approach - sort them by date, time and size across all directories. Yep, simple. Now how to get the list of files in the first place?

I came up with this command line:
```

 find -printf '%TY-%Tm-%Td %TT\t%s\t%f\t%P\n' | sort > list.tsv

```

Step by step:
[LIST=1]
[*]The command '**find**' as the name suggests finds the files on your drive. Try $man find to see all the options.
[*]The argument '**-printf**' tells the command '**find**' to print a formatted information for each file found. (I wanted all files so there's no search expression)
[*]The ugly string with percent signs and backslashes, that's the format string for date, time, size, name and relative path separated by tabs
[*]Then we come with a pipe to '**sort**' command which -sorts- the output of the previous alphabetically line by line.
[*]And because I've got loads of pictures, better store the output in a file rather than letting it write to the console, so there goes the '> list.tsv'
[/LIST]

So this command takes all files in the current directory, formats some information about each of them, sorts it and saves it in the same directory as list.tsv

It's a matter of few seconds to import this file in your favourite table processor (OOo) and off you go with a formula like =IF(AND(A1=A2;B1=B2);"BINGO!";""). It takes then some scrolling or paging, thinking, viewing, considering, but it works.

Hope this helps
Cheerio, Robajz

---

