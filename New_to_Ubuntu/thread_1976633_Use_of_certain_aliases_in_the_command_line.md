---
title: "Use of certain aliases in the command line"
date: 2012-05-09
forum: New to Ubuntu
---

### Post by vasa1 on 2012-05-09
Suppose I decide to make an alias "*sm*" to run /usr/local/seamonkey/seamonkey from the terminal with **nohup**. So my entry in .bash_aliases would be:
```
alias sm='nohup /usr/local/seamonkey/seamonkey'

```
My question is this: how do I know, before hand, whether "*sm*" is already an existing command to run something?

In this case, I first typed "sm" at the control prompt and got the response that:
```
The program 'sm' is currently not installed.  You can install it by typing:
sudo apt-get install sm

```

Since **sm**, the program, is not installed, is there any harm in using *sm* as an alias now? And, just for argument, what would happen if I later installed **sm**, the program? What would typing "sm" at a terminal prompt do?

(I guess the easy way out is to use a longer alias :) )

---

### Post by vasa1 on 2012-05-09
I found two links that should help:
[http://stackoverflow.com/questions/948008/linux-command-to-list-all-available-commands-and-aliases](http://stackoverflow.com/questions/948008/linux-command-to-list-all-available-commands-and-aliases)
and
[http://www.oreillynet.com/linux/cmd/](http://www.oreillynet.com/linux/cmd/)

---

### Post by papibe on 2012-05-09
Hi vasa1.

Bash expands aliases before start looking into the path for programs, so your alias would have priority.

In case there's a program called sm, you would be able to call it using its full path. For instance:
```
/usr/bin/sm
```
Does that answer your question?
Regards

---

### Post by vasa1 on 2012-05-09
> **papibe said:**
> Hi vasa1.

Bash expands aliases before start looking into the path for programs, so your alias would have priority.

In case there's a program called sm, you would be able to call it using its full path. For instance:
```
/usr/bin/sm
```
Does that answer your question?
Regards
That's what I was about to ask: which has priority? 
So that answers my question! Thank you :)
(Marking as "Solved")

---

