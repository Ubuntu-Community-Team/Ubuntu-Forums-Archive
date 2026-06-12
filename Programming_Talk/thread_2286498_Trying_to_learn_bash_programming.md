---
title: "Trying to learn bash programming"
date: 2015-07-12
forum: Programming Talk
---

### Post by macstl on 2015-07-12
I am using desktop ubuntu 12.04 LTS
I created short program using greater than operator 


clear
let Salary=3000
let NewSalary=2000
test $Salary -gt $NewSalary
echo "$?"
 

I comes back with a false zero on the screen. should'nt it be a true 1?

---

### Post by papibe on 2015-07-12
Hi macstl.

This should help to clarify things:
```
$ true; echo $?
0

$ ! true; echo $?
1

$ test true; echo $?
0

$ test ! true; echo $?
1
```
In other words, in Bash zero is true.

Another way to show the situation:
```
$ false; echo $?
1

$ ! false; echo $?
0

$ test false; echo $?
0

$ test ! false; echo $?
1
```
Does that help?
Regards.

---

### Post by macstl on 2015-07-12
I am reading Linux Programming for Dummies by Jim Keogh
Book says "A true value is one; a false value is a zero."
Is this a misprint or does this vary from one distro to another?

---

### Post by spjackson on 2015-07-12
Apparently that book is about Bash programming. In that case the statement is incorrect for all Linux distros. See the review dated 9 Sept 2001 here: [http://www.amazon.co.uk/Linux-Programming-Dummies-Jim-Keogh/dp/0764506919](http://www.amazon.co.uk/Linux-Programming-Dummies-Jim-Keogh/dp/0764506919) where the reviewer reported the mistake to the publisher and received a free book.

---

### Post by macstl on 2015-07-12
I read the review and the others too. pretty negative. Thanks for the heads up on that. 
Know any good books about bash programming for beginners without so many errors?

---

### Post by ofnuts on 2015-07-13
From your original post, I wonder if you are looking at the right language. Bash is not meant for general programming but for scripting. You aren't going to deal about individual employees with it. You are more likely to define some processing of files that holds all the employee information by issuing commands that process them, so that the bulk of the processing is done in these commands.... which is why bash True/False representation is the opposite of what you find in general-purpose programming languages: a command indicates success by returning 0 (interpreted as 'true" by bash), otherwise it returns some error code (interpreted as 'false").

---

### Post by Habitual on 2015-07-13
Some reading material:
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
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
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
[http://www.linuxquestions.org/questions/blog/rtmistler-575248/bash-scripting-for-dummies-and-geniuses-35795/](http://www.linuxquestions.org/questions/blog/rtmistler-575248/bash-scripting-for-dummies-and-geniuses-35795/)

and 
[http://www.shellcheck.net/](http://www.shellcheck.net/)

---

### Post by macstl on 2015-07-13
Thanks for all the reading material. This could take awhile....

---

### Post by Vaphell on 2015-07-13
ignore the tldp.org. There is some good stuff there but it's mixed with an unhealthy dose of deprecated/obsolete syntax and practices. As a newb you don't want to absorb how to write oldschool, dirty hacks.

look at the sidebar of [https://www.reddit.com/r/bash](https://www.reddit.com/r/bash), there are a few sources  not considered harmful (most likely all are in that extensive list you got).

---

