---
title: "Terminal asks for Product - Name and won't let me progress."
date: 2013-07-05
forum: New to Ubuntu
---

### Post by mcfc on 2013-07-05
Ist time I've tried using the terminal but won't let me. Turns out that I don't have access to certain areas of my computer (root etc) due to no 'special preferences'. Something to do with 'SuperUser preferences). What's this all about and how can I fix - if at all?

---

### Post by westie457 on 2013-07-05
Welcome to the Forum.

This page might explain things for you. It certainly explains them better than I could. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Any thing you are not sure of just ask. Someone will answer you.

Thank you.

---

### Post by mcfc on 2013-07-05
Thanks for your reply Westie.

Was told by a friend to do 'sudo apt get-clean' but terminal wouldn't let me. Seems I may have inadvertently been trying to do something a bit bigger than I actually intended to do (and reading too much into the inaccessible areas of my computer). Ah well, It's a hard life when you're a dimwit - think I'd better stick to e-mail and the Absolute Beginner status.

---

### Post by The Cog on 2013-07-05
Don't do yourself down. There is a lot to learn for newcomers and you have to start somewhere. I've been using Linux for ten years, and I just had to look up what apt-get clean does in the manual. 

Welcome to the forums. It's a good place to just lurk and read about things - you'll learn a lot. Post if you have any questions.

If you still have questions on the issue you posted for, please post a bit more detail in this thread. I don't recognise the term 'special preferences'.

---

### Post by The Cog on 2013-07-05
Don't do yourself down. There is a lot to learn for newcomers and you have to start somewhere. I've been using Linux for ten years, and I just had to look up what apt-get clean does in the manual. 

Welcome to the forums. It's a good place to just lurk and read about things - you'll learn a lot. Post if you have any questions.

If you still have questions on the issue you posted for, please post a bit more detail in this thread. I don't recognise the term 'special preferences'.

---

### Post by westie457 on 2013-07-05
> **mcfc said:**
> Thanks for your reply Westie.

Was told by a friend to do 'sudo apt get-clean' but terminal wouldn't let me. Seems I may have inadvertently been trying to do something a bit bigger than I actually intended to do (and reading too much into the inaccessible areas of my computer). Ah well, It's a hard life when you're a dimwit - think I'd better stick to e-mail and the Absolute Beginner status.


When you tried the 'sudo apt-get clean' command you should have gotten a prompt for your password. This password should be the one you set up while you were installing the OS, unless you deliberately left the password fields blank and selected to 'Log in without a Password'.

If that is the case you need to go here and create the password. [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

When typing your password into the terminal nothing shows on the screen. This is normal and part of the built in security. Nobody looking over your shoulder at the screen will be able to tell how long your password is be able to guess at it.

Hope this helps.

---

### Post by Zill on 2013-07-05
> **mcfc said:**
> ...Was told by a friend to do 'sudo apt get-clean' but terminal wouldn't let me...
The command 'apt get-clean' does not exist.  The actual command is '[apt-get clean]("https://help.ubuntu.com/community/AptGet/Howto")' and, as a command that works at system level, this *must* be run with the 'sudo' prefix.  Having said that, you may not need to run this at all as it is basically a maintenance command that may help if you have problems running other apt-get commands.  So, I suggest you advise exactly what you are trying to achieve and we may be able to give better guidance.

Most user functions can be done via a "friendly" GUI these days and so you may not need to resort to terminal commands at all.  However, as you gain experience, you will find that many things can be done more efficiently using terminal commands - which is why they are popular. ;-)  A further reason for terminal commands in this forum is that they are "universal" and so work on any flavour of Linux.  OTOH, trying to give GUI "click-here, click-there" commands is very difficult when there are so many different GUI's and versions of GUI's out there!

---

