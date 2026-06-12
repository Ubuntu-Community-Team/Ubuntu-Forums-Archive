---
title: "Issue with bash command vs. shell script"
date: 2008-04-11
forum: Programming Talk
---

### Post by adleberg on 2008-04-11
I've noticed a strange occurence while doing some simple shell scripting that commands behave differently when inputed into the command line and when used in a shell script. 

For example the command, echo {a..z} in the command line will produce
abcd --> z while the same command in a shell script will simply print {a..z}. I use #!/bin/sh , how is it possible that the command is interpreted differently?

---

### Post by slavik on 2008-04-11
because /bin/sh is a link to dash, while the terminal emulator is probably running bash.

---

### Post by LaRoza on 2008-04-11
> **adleberg said:**
> I've noticed a strange occurence while doing some simple shell scripting that commands behave differently when inputed into the command line and when used in a shell script. 

For example the command, echo {a..z} in the command line will produce
abcd --> z while the same command in a shell script will simply print {a..z}. I use #!/bin/sh , how is it possible that the command is interpreted differently?

Change #!/bin/sh to #!/bin/bash

---

### Post by adleberg on 2008-04-11
Thanks! it was causing some issues with my while loops as well but its all fine now :KS

---

### Post by LaRoza on 2008-04-11
> **adleberg said:**
> Thanks! it was causing some issues with my while loops as well but its all fine now :KS

See this article for more:  [http://en.wikipedia.org/wiki/Debian_Almquist_shell](http://en.wikipedia.org/wiki/Debian_Almquist_shell)

---

