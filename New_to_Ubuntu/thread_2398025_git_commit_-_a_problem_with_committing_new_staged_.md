---
title: "git commit - a problem with committing new staged changes"
date: 2018-08-06
forum: New to Ubuntu
---

### Post by alialriai on 2018-08-06
Hi Linux community, 


I am having problem with "git commit" command. I am typing the following in the command line:


$ git commit


then my default text editor, emacs, pups up with default message. I tried to add addition information and save. Then I go to the file -> exit. However, I receive the following message:


"Aborting commit due to empty commit message."


when I check the status of git with "git status", I can see that my changes are not committed, yet. 



Can you please help me with this problem? Am I not saving the comments properly? Keeping in mind that I am hitting save and exiting from file -> exit. Also, the same problem persist when I change the default text editor to nano text editor. 

I also tried "git commit -v" but still the same problem persist. 


The only time that "git commit" works is when I try "git commit -m "some message"", but I do not like this method because "git commit -v and git commit" has a lot of useful pre-configured information that will take me a lot of time to type if I decided to use "git commit -m."



Thank you,

Ali,

---

### Post by wildmanne39 on 2018-08-06
Hello and welcome to the forum!

*Thread moved to **New to Ubuntu for a more appropriate fit**.* 

The Resolution Centre is only for:
> This is the place to contact a forum admin concerning problems with your forum account, to appeal moderator action, to request a thread be moved from the jail, or to file a complaint about forum harrassment or abuse. 

---

### Post by alialriai on 2018-08-06
Thank you, I will be more careful with any future threads. 

Ali,

---

### Post by spjackson on 2018-08-06
It works for me with both
```

export EDITOR=emacs
export EDITOR="emacs -nw"

```

> **alialriai said:**
> 
The only time that "git commit" works is when I try "git commit -m "some message"", but I do not like this method because "git commit -v and git commit" has a lot of useful pre-configured information that will take me a lot of time to type if I decided to use "git commit -m."

What pre-configured information? Do you mean all the details of added/changes files which are commented out with #?

Do you actually type a message? Does what you save have any lines which are neither blank nor begin with #? Do you get a confirmation of save e.g.
```

Wrote /home/user/tmp/g/.git/COMMIT_EDITMSG

```
Perhaps you could post a sample file content just before you exit.

---

