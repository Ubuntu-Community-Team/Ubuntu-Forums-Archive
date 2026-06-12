---
title: "Sed change next line"
date: 2012-05-20
forum: Programming Talk
---

### Post by bcooperizcool on 2012-05-20
Hello!  I am having some trouble with a script I am making, to change the next line after matching something.  The way I am doing it now is trying to match both lines, and then replace it.  (No, I don't want to delete the line, I want to change the "true" to "false".   I really don't have a clue what I am doing, so if anyone could explain when they answer, bit by bit what they did, I would really appreciate it :)

There are tabs before where it shows up in the file just FYI

```
#!/bin/bash

sed -i ':begin;$!N;s/\t<key>multitasking<\/key>\n\t<true\/>//;tbegin' /System/Library/CoreServices/SpringBoard.app/N81AP.plist

#This is what I want to replace it with....
#<key>multitasking<\/key>\n<false\/>
```

Is there some way to match multiple lines in sed and then just manipulate what comes after? Or change the lines themselves?

Thanks!

---

### Post by steeldriver on 2012-05-20
you are close I think - how about

```
sed '/<key>multitasking<\/key>$/{$!N; s/true/false/}'
```

The way it works I think is that first we find the primary pattern (i.e. /regex/); then we make sed append the next line to the pattern space provided we are not already at EOF ($!N); then we search and substitute AGAIN on the WHOLE two-line pattern space (including the escaped newline)

---

### Post by justanoob on 2012-05-22
So would this code snippet work for changing a couple of parameters in *.config files? I am setting up 45 laptops with Ubuntu, and need to do some modifications to log into Active Directory. I can do it by hand, but for 45? I'd like to write a /bash script to automate all the config changes and install the software needed.

---

