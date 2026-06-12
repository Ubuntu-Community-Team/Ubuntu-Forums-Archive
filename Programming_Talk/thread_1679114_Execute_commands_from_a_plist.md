---
title: "Execute commands from a plist?"
date: 2011-01-31
forum: Programming Talk
---

### Post by bcooperizcool on 2011-01-31
This is the only place I can think of to put this...

How can I get a plist to set variable in a bash script, then execute commands in it?

Odd question, but I couldn't find it by googling.

Thanks!

---

### Post by lavinog on 2011-01-31
What do you mean by plist?
Can you explain what you are wanting to accomplish?

---

### Post by Vaphell on 2011-01-31
+1
what is plist and what is the format of that thing

---

### Post by Joeb454 on 2011-01-31
I've only ever seen plist files on OS X. The wikipedia page may help: [http://en.wikipedia.org/wiki/Property_list](http://en.wikipedia.org/wiki/Property_list)

---

### Post by Vaphell on 2011-01-31
wiki says that the format is not exactly fixed and there are different flavors. It would be cool if OP shed some light on it - what is the internal structure of the file?

EDIT:
rough script assuming human readable format where marker (eg xml tag) is in the same line as the value
```

#!/bin/bash

grep '<cmd>' plist.txt | sed -r 's:.*<cmd>(.*)</cmd>.*:\1:' | while read cmd
do
  echo command: $cmd
  eval "$cmd"
done

```

my test input:
```
<whatever>
<junk></junk>
<cmd>echo "oh noes"</cmd>
<junk></junk>
<cmd>date</cmd>
<cmd>echo "IT'S ALIVE"</cmd>
</whatever>
```
output:
```
$ ./plist.sh 
command: echo "oh noes"
oh noes
command: date
pon, 31 sty 2011, 23:08:06 CET
command: echo "IT'S ALIVE"
IT'S ALIVE
```

---

### Post by bcooperizcool on 2011-01-31
I'm trying to make a special page that calls sets variables when my script needs them, and then executes it.  It is for my iphone.  If you want to see my script, its on wintersled.blogspot.com
I am trying to make it vaguely GUI.   I know how to make basic plists, but just not execute commands from them.  :/

---

### Post by Vaphell on 2011-01-31
give an example of plist with parameters you want to feed the script with, so we can cook something up.

---

### Post by bcooperizcool on 2011-01-31
Like my actual plist work so far?  I haven't made one yet. I was googling stuff, and just putting into another plist to test, and then when I was done, I was going to put it in a new plist (No point making everything, then finding out it doesn't work. Build it bit by bit.)
Or the code I hope to execute, and such?
I would need to ad a textbox, that sets the $theme variable in my script.
And then just have it run the install theme.  I'm thinking there should be an easy way to do this, as I know you can launch a program on start with launchdaemons with an argument, but I don't know how to make that into a cell and such.

---

