---
title: "Parsing characters' problem in Python"
date: 2009-10-04
forum: Programming Talk
---

### Post by sauronnikko on 2009-10-04
Hi. I'm trying to parse a file which has words with accent. For this, I use codecs.open ('nameoffile', 'r', 'utf-8'). Then, for every line in the open document, I do a re.search () to find if the current line matches some pattern. If that's so, I print the line, and I add the line to a list L, using L.append (line).

The problem is that when I print the lines inside the loop all the words are printed just fine, with their accents. After I quit the loop and try to print the contents of line L, every single character having an accent is printed the wrong way. I don't understand this, for before everything was fine and this just happens when I print the strings corresponding to the list.

Any thoughts. Thanks!

---

### Post by Arndt on 2009-10-05
> **sauronnikko said:**
> Hi. I'm trying to parse a file which has words with accent. For this, I use codecs.open ('nameoffile', 'r', 'utf-8'). Then, for every line in the open document, I do a re.search () to find if the current line matches some pattern. If that's so, I print the line, and I add the line to a list L, using L.append (line).

The problem is that when I print the lines inside the loop all the words are printed just fine, with their accents. After I quit the loop and try to print the contents of line L, every single character having an accent is printed the wrong way. I don't understand this, for before everything was fine and this just happens when I print the strings corresponding to the list.

Any thoughts. Thanks!

Can you show some concrete code that exhibits this behaviour?

---

