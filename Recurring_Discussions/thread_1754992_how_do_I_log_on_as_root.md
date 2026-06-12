---
title: "how do I log on as root ?"
date: 2011-05-10
forum: Recurring Discussions
---

### Post by zeelog on 2011-05-10
I can't figure out how to log onto Ubuntu as root.
This machine will not be on any network ever, and I will
be the only one with access to it. Everything is easier
when you're root. 
  How do I set up Ubuntu so I can log in as root?

---

### Post by Smart Viking on 2011-05-10
You don't. Use sudo or gksudo where you need the privileges, if you do not know how to log in as root, then you definitely shouldn't.

---

### Post by SavageWolf on 2011-05-10
You should never EVER login as root. EVER!

Sudo'll do you just fine, also, why does your computer not use internet?

I don't even know if root HAS a GUI...

---

### Post by demilord on 2011-05-10
Root is evil, its not windows without being disrespectful.
use sudo or gksudo

---

### Post by nothingspecial on 2011-05-10
> **zeelog said:**
> I can't figure out how to log onto Ubuntu as root.
This machine will not be on any network ever, and I will
be the only one with access to it. Everything is easier
when you're root. 
  How do I set up Ubuntu so I can log in as root?

No one is permitted to tell you.

To paraphrase something........ somewhere (I mean no offence)

If you don't know how to do it, then you shouldn't

If you do know how to do it then you wouldn't need to ask.

Read this

[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

and this



[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by uRock on 2011-05-10
> **nothingspecial said:**
> [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

+1 one on the link. It explains how to log in as root and there is a reason for all of the warning signs and such on that page.

Regards,
uRock

---

### Post by collisionystm on 2011-05-10
> **zeelog said:**
> I can't figure out how to log onto Ubuntu as root.
This machine will not be on any network ever, and I will
be the only one with access to it. Everything is easier
when you're root. 
  How do I set up Ubuntu so I can log in as root?


Root has a GUI. It is just like another account. The only difference is file permissions have no effect on it. It can come and go as it pleases. This is why its dangerous. Certain programs use  file permissions as boundaries when they are running or being installed. Running root is like having a big dog thats not fenced in.

You should not enable root. This is any easy way to break your system. 

If you do however want to enable root, I am sure a simple Google search will help you.

Linux and Ubuntu is all about freedom of choice...You can do whatever you want with the system because it is YOURS. the only reason we tell you to leave root disabled is because we are trying to help... if you do however ignore the help... well, your lesson learned =)

I have used root before, and it sucks when you accidentally delete a file or modify something without thinking it through. At least sudo helps you stop for a second and think about what your doing

---

### Post by zeelog on 2011-05-11
It's a good thing I asked this nasty question.  It gives everyone
a chance to jump up and down and act self-righteous. 
 Looks like I'm going to have to learn all about sudo.

---

### Post by uRock on 2011-05-11
Moved to Recurring.

---

### Post by aysiu on 2011-05-11
You've been given the answer you're looking for. No need to insult others on the forums.

---

