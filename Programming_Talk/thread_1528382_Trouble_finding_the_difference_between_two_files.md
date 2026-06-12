---
title: "Trouble finding the difference between two files"
date: 2010-07-10
forum: Programming Talk
---

### Post by shnuggles on 2010-07-10
I've been working with two files that contain lines of data, each line is numbered, and they are of different length. What I need to do is find the lines that are contained in file one but are not in file two, and get the line number from each file. Here is an example:
File 1
1 a
2 b
3 c
4 d
5 e

File 2
1 a
2 b
3 d

output
3 c
5 e

Essentially the number from File 2 are irrelevant; I only care about the data matching up. I've tried using diff but can't get what I'm looking for. I realize that awk could do it, but I'm not familiar with the syntax needed to make awk do what I want it to, so please, whatever the solution, explain how your solution works so that I can learn from it. Thanks everyone!

---

### Post by Some Penguin on 2010-07-10
Looks like an assignment designed to teach you about hash tables.

---

### Post by soltanis on 2010-07-10
It also looks almost exactly like a problem that came up about a week ago and was solved with awk. I would search for "awk" and "difference" in the forums and that will probably lead you to it.

---

### Post by shnuggles on 2010-07-11
Thanks for the reply. I found the post you referenced, and I think that I have a different problem. Where she wanted the output to be what was the same, I need the difference. Also, I need to preserve the line numbers of the one file. Essentially, I have one file that has lines inserted into it; otherwise the two files are the same. Because of the added lines however, I can't use the line numbers as a basis of comparison. After seeing her solution, I think that awk might hold the answer, I just can't figure out how.

---

### Post by geirha on 2010-07-11
Having the line numbers in the file complicates things. Without the line numbers, you could use a simple grep:
```
grep -nvxF -f file2 file1
```

See [http://mywiki.wooledge.org/BashFAQ/036](http://mywiki.wooledge.org/BashFAQ/036)

---

### Post by soltanis on 2010-07-11
Actually, it's no problem for awk. Since you haven't figured it out for yourself, I'll post what I believe will be a solution:

```

#!/bin/sh
awk 'NR>FNR { if (ln[$1] != substr($0, length($1) + 2)) { print $0 } } NR==FNR { ln[$1] = substr($0, length($1) + 2) }' file1 file2

```

Try it out, since I haven't tested it myself.

---

