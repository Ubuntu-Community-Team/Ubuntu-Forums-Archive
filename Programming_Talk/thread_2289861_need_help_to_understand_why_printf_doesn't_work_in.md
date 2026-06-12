---
title: "need help to understand why printf doesn't work in bash script"
date: 2015-08-07
forum: Programming Talk
---

### Post by mantazasas on 2015-08-07
Hi all.
I'm writing my first script but i have some troubles.  All i want is to nicely update my same lines without reset or clear commands. 
Here's my code: 
```

#!/bin/bash
# My first script


echo "testas";
while [ 1 ]; do sensors;printf "\033[1A";sleep 1;done;


```

it is very simple , but i can't understand why my printf won't work.
By idea the command should met my requirements but it don't.
Or I'm wrong here?

---

### Post by PaulW2U on 2015-08-07
*Thread moved to **Programming Talk**.* 

I've also changed the title to be a little more meaningful.

---

### Post by Lars Noodén on 2015-08-07
Your script uses [ANSI escapes](http://ascii-table.com/ansi-escape-sequences.php) to move the cursor up a single line.  The output of sensors is multiple lines, so you will have to count them and replace the 1 with the right number in the printf statement.

---

### Post by mantazasas on 2015-08-07
Thank you for reply but can you in which part i should replace it ?

---

### Post by Lars Noodén on 2015-08-07
The 1A should be something else, like 5A or 12A or whatever, depending on the number of lines that [sensors](http://manpages.ubuntu.com/manpages/trusty/en/man1/sensors.1.html) produces on your system.  Run 'sensors' by itself and then count the lines and use that number.  

The \033 is octal for the escape 'character'  On terminals, going way back in history, an Escape followed by [ followed by some chosen characters have special functions.  *n*A will move the cursor up *n* lines.  So if you print "\033[3A", it will move up three lines.  See the link in #3 above.

---

### Post by mantazasas on 2015-08-07
Thank you for answering everything works now :)

---

