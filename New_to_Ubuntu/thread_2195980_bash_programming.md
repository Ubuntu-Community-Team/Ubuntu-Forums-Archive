---
title: "bash programming"
date: 2013-12-27
forum: New to Ubuntu
---

### Post by avdiel1946 on 2013-12-27
Using ubuntu 13.10 on Acer Aspire 5733 with i3 64-bit quad-core. Recently abandoned Windows 7. Now trying to learn to program in bash using 4.2.45. In the Tools section of the menu bar there is a command to reset and clear the terminal. Would like to know how to do that programmatically.

---

### Post by steeldriver on 2013-12-27
The CLI commands are just 

```
reset
```

```
clear
```

(yes it really is that simple) - see

```
man reset
```
and
```
man clear
```

for details / usage

---

### Post by The Cog on 2013-12-27
This will send a cursor home and clear screen ANSI escape sequence that works on most terminals:
```
echo $'\x1b[H\x1b[J'
```

The two sequences are:
ESC [ H (cursor home)
ESC [ J (clear from cursor to end of page)

EDIT:
Doh! Of course, if you are in a bash script you can just call those commands, like steeldriver says. Nothing more needed.

---

### Post by Bashing-om on 2013-12-27
avdiel1946; Hi !

> 
Now trying to learn to program in bash


My favorite tutorial:
[http://mywiki.wooledge.org/FullBashGuide](http://mywiki.wooledge.org/FullBashGuide)
Amongst many others.

[INDENT]ubuntu;
[INDENT][INDENT][INDENT]A wonder to behold
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by avdiel1946 on 2013-12-27
reset works fine. clear just moves everything up. Reason for needing to clear, program will have several screen changes and do not want to keep all the old stuff around.  Many thanks....

---

### Post by Habitual on 2013-12-27
Here's just a few resources for your collection of References:

[http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html) 
[http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html) 
[http://tldp.org/HOWTO/Bash-Prompt-HOWTO/](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/)
[http://www.gnu.org/software/bash/manual/html_node/index.html](http://www.gnu.org/software/bash/manual/html_node/index.html)
[http://www.grymoire.com/Unix/Sh.html](http://www.grymoire.com/Unix/Sh.html)
[http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)
[http://tldp.org/LDP/abs/abs-guide.pdf](http://tldp.org/LDP/abs/abs-guide.pdf)
[http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/) 
[http://mywiki.wooledge.org/BashFAQ](http://mywiki.wooledge.org/BashFAQ)
[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)
[http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz)
[http://mylinuxbook.com/linux-shell-environment/](http://mylinuxbook.com/linux-shell-environment/)
[http://www.subsignal.org/doc/AliensBashTutorial.html#Table%20Of%20Contents](http://www.subsignal.org/doc/AliensBashTutorial.html#Table%20Of%20Contents)
[http://www.rigacci.org/docs/biblio/offline/TLCL-09.12.pdf](http://www.rigacci.org/docs/biblio/offline/TLCL-09.12.pdf)
[http://www.linuxhomenetworking.com/](http://www.linuxhomenetworking.com/)
[http://mylinuxbook.com/bash-shell-scripting-part-i/](http://mylinuxbook.com/bash-shell-scripting-part-i/)
[http://mylinuxbook.com/bash-shell-scripting-2/](http://mylinuxbook.com/bash-shell-scripting-2/)
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)
[http://linuxcommand.org/lc3_learning_the_shell.php](http://linuxcommand.org/lc3_learning_the_shell.php)
[http://unixhelp.ed.ac.uk/](http://unixhelp.ed.ac.uk/)
[http://www.linuxquestions.org/questions/blog/druuna-60084/resources-useful-links-35334/](http://www.linuxquestions.org/questions/blog/druuna-60084/resources-useful-links-35334/)
[http://www.linuxquestions.org/questions/linux-general-1/links-for-helpful-linux-articles-and-books-4175433508/](http://www.linuxquestions.org/questions/linux-general-1/links-for-helpful-linux-articles-and-books-4175433508/)
[http://www.hammondslegacy.com/forum/viewforum.php?f=40&sid=5859bbcf18ccb151f7de3e86cafdf486](http://www.hammondslegacy.com/forum/viewforum.php?f=40&sid=5859bbcf18ccb151f7de3e86cafdf486)
[http://linux-shell-commands.jimdo.com/](http://linux-shell-commands.jimdo.com/)
[http://flossmanuals.net/command-line](http://flossmanuals.net/command-line)
[http://tille.garrels.be/training/tldp/](http://tille.garrels.be/training/tldp/)
[http://www.collegeathome.com/blog/2008/05/22/open-courseware-for-linux-geeks-50-resources/](http://www.collegeathome.com/blog/2008/05/22/open-courseware-for-linux-geeks-50-resources/)
[http://www.codecoffee.com/tipsforlinux/index-linux.html](http://www.codecoffee.com/tipsforlinux/index-linux.html)

---

