---
title: "Html generating  script"
date: 2007-08-13
forum: Programming Talk
---

### Post by Acglaphotis on 2007-08-13
Hi

I need a script that does "ls" to a certain folder and generates an html based on the output. Any ideas?

---

### Post by CptPicard on 2007-08-13
Sounds like you might want to look into either the utilities "sed" or "awk"... write an appropriate program for either of them and them pipe ls to them :)

---

### Post by chriscando on 2007-08-13
Im not really sure how you want it formatted but maybe you could use this as a start.

```
#!/bin/bash

#start html page
echo "<html>"
echo "<title>ls output</title>"

while read line
do
echo "<p>$line</p>"
done

echo "</html>"

```

then run it using:
```
ls | ./script.sh
```

---

