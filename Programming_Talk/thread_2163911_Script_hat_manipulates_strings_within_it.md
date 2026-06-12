---
title: "Script hat manipulates strings within it"
date: 2013-07-20
forum: Programming Talk
---

### Post by bkpsusmitaa on 2013-07-20
I want the following script to check the speed of the internet data transfer, and if it is slow or off, invoke pppoeconf for access concentrator
```

#!/bin/bash
while :
do
x=0
y=0
x=`pppstatus --bytes | grep "Bytes received" | some further operation to collect the numerical data  in bytes or kbytes> /dev/null`
sleep 5
y=`pppstatus --bytes | grep "Bytes received" | some further operation to collect the numerical data... > /dev/null`
z is the final value given by (y-x)/5 to calculate the rate of data transferred
if z is lower than some value
then
echo "speed below $z";
pppoeconf > /dev/null
else
sleep 1
fi
done

```

Now, what the portion of ```
pppstatus --bytes | grep "Bytes received" 
``` does is gives result of the form:
```
Bytes received: 14427556
```
How to collect only the numerical data only and do the mathematical operations within script? I am aware of bc and mathematical operations. But can't find way to collect only the digits. grep [0-9] highlights the digits only, but prints the whole line. Also, grep -o [0-9] yields the digits each in one line. Do I have to use redirection with read?

---

### Post by sudodus on 2013-07-20
use ***cut*** and use : as delimiter and select field no 2:

```
cut -d : -f2
```

---

### Post by Vaphell on 2013-07-20
```
awk '{ print $NF; }'
``` will return the very last 'word' in the line and ```
awk '/Bytes received/ { print $NF; }'
``` will make grep step unnecessary

bash only does integer arithmetic natively but it should be good enough. You can write your condition as
```
if (( (y-x)/5 < N ))   # (( )) is integer math mode
then ...
```

---

### Post by bkpsusmitaa on 2013-07-20
**Wow!** Thanks. Why don't you guys prepare a guideline for us novices to ease our learning bash scripting?!

---

### Post by Habitual on 2013-07-20
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
[URL="http://www.hammondslegacy.com/forum/viewforum.php?f=40&sid=5859bbcf18ccb151f7de3e86cafdf486"]http://www.hammondslegacy.com/forum/viewforum.php?f=40&sid=5859bbcf18ccb151f7de3e86cafdf486


[/URL]

---

### Post by bkpsusmitaa on 2013-07-20
I am sorry I could not explain myself. It would be like a syllabus - a guideline, like say first, para(1) to para(3) from  page xxx, second para(3) to para(5) from page yyy, and so on and so forth... The easiest of route, the one you believe, with full honesty and integrity, would have served you best had you taken it while learning...
BTW, are you the same habitual of [http://bashscripts.org](http://bashscripts.org) ? In that case, **please refrain from engaging yourself on my questions.**
Reason? The last post of [Unary operator]("http://bashscripts.org/forum/viewtopic.php?f=8&t=1721&p=6375#p6375")

---

### Post by Vaphell on 2013-07-20
dude, while he was a bit dry, he still pointed to the relevant chapter, if you read it you would know what went wrong. People on the forums are not for your convenience, if you are not willing to investigate a bit on your own and expect answers to fall from the sky, you won't find much sympathy.

---

