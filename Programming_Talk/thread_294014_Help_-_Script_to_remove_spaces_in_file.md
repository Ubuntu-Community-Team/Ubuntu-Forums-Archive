---
title: "Help - Script to remove spaces in file?"
date: 2006-11-06
forum: Programming Talk
---

### Post by featherking on 2006-11-06
I have a file where the records were input with 3 spaces inbetween each record instead of a comma or a carraige return between each. Is there a script i can run to remove the spaces and replace them with either a comma or a colon or a carraige return would be the best.

the only thing ive come up with so far is to somehow use awk

```
 awk '{print $1}' /home/chris/Desktop/list | sort
```

this prints only the first record, thinking that with the spaces the file actually only contains one record. Is there someway i can have it delete the spaces after the characters? then maybe i could take that output and just > into a new file?

---

### Post by ape on 2006-11-06
What about something like this:

 ```
perl -pe 's/ +/,/g' < input.txt > output.txt
``` 

This replaces any space(s) in your input file with commas and writes the new file out to output.txt

---

### Post by featherking on 2006-11-06
well that did exactly what you said, however my program apparently insists that each record be on its own line. Would it be easy to modify that formula to do this? So, instead of a comma we replace the space with a carraige return?

---

### Post by featherking on 2006-11-06
Nevermind, i just replace your , with a \r and it did the trick! thanks a million

---

### Post by ape on 2006-11-06
Glad I could help.  Be careful of your use of \r.  That is just a return and on some platforms will not force a newline.  You may want to try \n if \r gives you problems.

---

### Post by featherking on 2006-11-06
you were right, i could not figure out what was causing all kinds of program errors and it turned out to be the '\r' switch. For future reference '\n' worked flawlessly and would be a better way to go

---

### Post by po0f on 2006-11-06
featherking,

Just an FYI, **\r** is how Mac <=OS9 (don't know about OSX) ends lines, **\n** is how Linux ends lines, and **\r\n** is how Windows ends lines.

---

