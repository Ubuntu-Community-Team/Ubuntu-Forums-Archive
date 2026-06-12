---
title: "Good book on bash scripting (Been through the sticky thread)"
date: 2013-06-27
forum: Programming Talk
---

### Post by pmu on 2013-06-27
Hi,

In my previous thread I had posted a question on Bash Scripting and was suggested that its better to be very well versed with it.

I have been through the sticky thread and the links, but am looking for a more recent printed book on bash scripting. Something that would help me write production grade scripts at the earliest. I do understand that this will not happen overnight, but I am ready to put in the efforts. I have written a few Perl Scripts so hoping that the experience will help me with bash.

Any system admins here, if you could suggest a good book on scripting, I will be thankful.

---

### Post by Vaphell on 2013-06-27
why would you need a recent book for shell scripting? It's a neckbeards' stronghold and they are not eager to turn everything upside down every 2 years ;-)
i learned everything i know about bash by reading this forum and googling from time to time, though be warned there are plenty of quick and dirty hacks on the internet that teach bad habits.

if you know some perl you should be already familiar with standard programming concepts like for and while loops, if else's etc. and that's half of success.
When you pick a task and whip up a script for it, post it here so flaws can be pointed out early.

---

### Post by pmu on 2013-06-27
Hi Vaphell,

Thanks for the reply.

So this is sort of a Perlmonks for Bash Scripting then ? :)

This had happened with me while learning Perl, where I tried and learnt the stuff from net, but the Monks adviced me against certain ways of scripting  were gracious enough to point me in the right direction. Hoping the same will happen here too.

---

### Post by Cheesemill on 2013-06-27
I'll point you in the direction of a great little web page I discovered recently...
[www.shellcheck.net](www.shellcheck.net)

You paste your script into it and it will check it for common errors and bad practices. And as everyone knows it's much easier to learn correctly in the first place than to relearn what you've been doing wrong for years :cool:

---

### Post by Vaphell on 2013-06-27
> **pmu said:**
> Hi Vaphell,

Thanks for the reply.

So this is sort of a Perlmonks for Bash Scripting then ? :)

This had happened with me while learning Perl, where I tried and learnt the stuff from net, but the Monks adviced me against certain ways of scripting  were gracious enough to point me in the right direction. Hoping the same will happen here too.

yes, pretty much :-) there are many hacks that sort of work but can blow up in spectacular ways if some nasty edge case happens. Check your script with this list :-)
[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)

this one covers things that frequently occuring minitasks that are used to build greater whole
[http://mywiki.wooledge.org/BashFAQ/](http://mywiki.wooledge.org/BashFAQ/)

and to make the collection complete [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

---

### Post by pmu on 2013-06-27
Hi Cheesemill,

Whoa....thats awesome!!

It tells me whats wrong and what the right way to do it.

Thanks a lot.

---

### Post by Kujua on 2013-06-27
When you write shell scripts, it's not just shell syntax and features that you will need. You will also have to use a whole lot of other commands and tools (eg: sed, awk, grep). There are books on some of these tools themselves. So you will never find a book that will have "everything you need". And it's not practical to read books on all of these either.

One of the best ways to learn about them is the documentation that is already there on your system: man and info pages. Don't bother to read them top-to-bottom, as they can be very very long. Read a little to get a feel of what the shell/tool has to offer. Syntax and specifics you can lookup later when you need. The docs are right there on your system.
True, man and info are not always an easy read. But they are concise and straight-to-the-point. Combine this with a little digging around on the internet, and that's almost all you will need.

---

### Post by pmu on 2013-06-28
Hi All,

Thank you so very much for your help. 

I am truly thankful to you for sharing so much information. All the links you have provided and the amazing advice you have given, I have no words to express my gratitude.

---

### Post by Habitual on 2013-06-28
One or two of these you may already have, but I couldn't help myself! ;)

[http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html) 
[http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html) 
[http://tldp.org/HOWTO/Bash-Prompt-HOWTO/](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/)
[http://www.gnu.org/software/bash/manual/html_node/index.html](http://www.gnu.org/software/bash/manual/html_node/index.html)
[http://www.grymoire.com/Unix/Sh.html](http://www.grymoire.com/Unix/Sh.html)
[http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)
[http://tldp.org/LDP/abs/abs-guide.pdf](http://tldp.org/LDP/abs/abs-guide.pdf)
[http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/) 
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

Not all are programming-related, but I have found it necessary on occasion to have those as well.

Now Go and code something. 
Make us all Proud.

---

