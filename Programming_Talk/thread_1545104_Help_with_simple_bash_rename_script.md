---
title: "Help with simple bash rename script"
date: 2010-08-03
forum: Programming Talk
---

### Post by julian.irwin on 2010-08-03
Hey, 
I'm trying to learn a bit about shell scripts and I know renaming is a practical, easy place to start. I'm trying to rename files of this form

1-22Bach-StMatthewPassion-Part01-22.mp3

To this form:

#.mp3

Where # simply starts at 1 and goes up for each additional file.

I tried:

```
#!/bin/bash
j=1
for i in ls -n; do
	rename * $j.mp3 
	$j = $((j + 1))
done
```

But I got a message saying I was missing an operator before "Bach". Can anyone help?
Thanks!

---

### Post by Jacobian on 2010-08-03
This seems to work:

```
#!/bin/bash

i=1
for file in *.mp3; do
    mv -- "$file" "$i.mp3"
    i=$(($i+1))
done
```

This prevents the dash character from being interpreted as a parameter argument.

---

### Post by julian.irwin on 2010-08-03
Thanks, that worked perfectly.

Can you tell me what the "mv --" does? I looked in the man page for mv but I couldn't figure out what those dashes were for.
Thanks again.

---

### Post by Bachstelze on 2010-08-03
The dashes tell mv that this is the end of the aguments list, and that what's after is the source and destination filenames.  Otherwise, if a filename starts with a dash, mv will interpret it as a command-line argument.

---

### Post by Jacobian on 2010-08-03
Here is some further explanation of the "--":
[http://www.cyberciti.biz/faq/linuxunix-move-file-starting-with-a-dash/](http://www.cyberciti.biz/faq/linuxunix-move-file-starting-with-a-dash/)

---

