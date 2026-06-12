---
title: "Shell&amp;Profile configuration"
date: 2014-01-30
forum: New to Ubuntu
---

### Post by daveabes on 2014-01-30
Okay, so I am busy learning the terminal and am looking at the shell and profile configuration files.
Thus far it seems local confifuration takes place in the files ~/bashrc and ~/profile (usually hidden files) and more global settings are defined in the /etc folder.

I am using nano to view and possibily edit these files but cannot make sense of the language used. Is this bash scripting language and will I ever learn how to edit these kinds of files myself?

Many thanks.

---

### Post by Lars Noodén on 2014-01-30
You can learn to write shells scripts fairly easily.  If they get too complex, it is probably time to reach for a different scripting tool, such as perl or python.  

There are several shells, bash is common but a bit bigger and slower.  It is the default interface for Ubuntu in the terminal and even in OS X.  Dash (aka **sh** in Ubuntu) is a bit smaller and faster and even more portable.

Here are some references:

[list]
[*] [http://mywiki.wooledge.org/BashFAQ](http://mywiki.wooledge.org/BashFAQ)
[*] [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)
[*] [http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)
[*] [http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)
[/list]

The examples there will help give an idea on how to program shell scripts.  Most of the things you can do in bash you can also do in sh.  But since bash is a superset of sh, not everything in bash will work in sh, though everything in sh will work in bash.  You can see from the first line of the script which shell interpreter is being used.  It will be #!/bin/sh or #!/bin/bash

---

### Post by daveabes on 2014-01-30
Very useful information and thanks Lars. Will check out those links. I think this is what I have been looking for. :)

---

