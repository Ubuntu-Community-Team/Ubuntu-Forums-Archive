---
title: "A little BASH help please"
date: 2012-12-02
forum: Programming Talk
---

### Post by 0011235813 on 2012-12-02
Hi.

I have downloaded a program called ‘Markdown’ from here: [http://daringfireball.net/projects/markdown/](http://daringfireball.net/projects/markdown/)

Basically, it's a program that takes a specific plain text input and outputs HTML. I like to write fiction in my spare time and write all my chapters in plain text + its markup and then combine all the files into one for formatting in Sigil.

Thing is, it's much less hassle-some for me to work with an HTML file rather than manually adding in formatting with Sigil later on. BUT, the program in question gives me the HTML output straight in the terminal – not in a file. I can't find any documentation on how to log the output to a specific file (e.g. ~/Documents/Chapters.html).

Is there any way to make a bash-script to run the program and log the output to a specific file? I was thinking of coding it straight into the source code of the program, but I don't have any experience with Perl, and I'm no BASH guru :redface:

---

### Post by Gompa on 2012-12-02
so someting like > output ?
example : ls > test.txt

---

### Post by 0011235813 on 2012-12-02
> **Gompa said:**
> so someting like > output ?
example : ls > test.txt
Thanks. I figured it out to be:
```

#!/bin/bash
/home/username/Software/Markdown_1.0.1/Markdown.pl /home/username/Documents/test.text > /home/username/Documents/test-output.html

```
Which seems to be working.

---

