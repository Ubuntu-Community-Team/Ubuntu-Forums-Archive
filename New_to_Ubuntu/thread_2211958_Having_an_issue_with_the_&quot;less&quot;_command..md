---
title: "Having an issue with the &quot;less&quot; command."
date: 2014-03-18
forum: New to Ubuntu
---

### Post by Priest Apostate on 2014-03-18
I am using 12.04, and am currently experiencing problems with the 'less' command, in that I can break up long files into screen-by-screen readings -- but, all information is from previous screens is removed, preventing me from going back to read said content. How do I resolve that?

Added note. I've tried using "| less" and "|less" -- both resulted in the same issue.

---

### Post by whitesmith on 2014-03-18
Less should work if you just type something like```
less filename
```Have you tried other things like g (first line) and G (last line)? If these also fail you may have to reinstall the less utility.

---

### Post by ajgreeny on 2014-03-18
Just out of interest what type of file are you trying to look at using less?  Would cat work just as well in terminal, or are you using a command line interface with no scrollback?

---

### Post by oldos2er on 2014-03-18
Both PgUp and PgDn keys should work in less, if I'm understanding your question correctly.

---

### Post by Priest Apostate on 2014-03-19
Right now, I am trying to use the cat command to display two files, back to back, and pipe the output to the 'less' command. I think I have the issue resolved with the PageUp/Down buttons.

---

