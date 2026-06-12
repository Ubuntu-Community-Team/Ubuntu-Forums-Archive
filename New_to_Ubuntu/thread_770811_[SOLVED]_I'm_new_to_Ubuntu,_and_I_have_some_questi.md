---
title: "[SOLVED] I'm new to Ubuntu, and I have some questions..."
date: 2008-04-27
forum: New to Ubuntu
---

### Post by josh995 on 2008-04-27
I'm loving Ubuntu, it's pretty nice. My questions are:

1) If I install a program, like a messenger program, how do I delete it? I'm used to Windows, so I keep looking for "Uninstall Programs" but don't know what Ubuntus equivalent is...

2) Why, when I update, do I sometimes get a message saying something like "Some packages could not be received." Or something like that?

That's it for now, if I have another question I'll ask.

Thanks for any and all help!

*edit* Also, I installed the Beta version of 8.04, did it automatically update to the full, real version of 8.04? 

Thanks.

---

### Post by tamoneya on 2008-04-27
adding and removing programs can be done through synaptic package manager.
System -> Administration -> synaptic package manager.

As for this problem receiving packages i am not sure.  Can you post the full error

---

### Post by jaytek13 on 2008-04-27
1) you can use synaptic to uninstall program (system->administration->synaptic) or you can uninstall something from the command line using apt (apt-get remove program-name)

2) the software repositories are very busy right now. Some times it is having difficulty resolving the packages. This should disipate after while, but is extra busy right now due to the release of 8.04

---

### Post by encompass on 2008-04-27
> **josh995 said:**
> I'm loving Ubuntu, it's pretty nice. My questions are:

1) If I install a program, like a messenger program, how do I delete it? I'm used to Windows, so I keep looking for "Uninstall Programs" but don't know what Ubuntus equivalent is...

2) Why, when I update, do I sometimes get a message saying something like "Some packages could not be received." Or something like that?

That's it for now, if I have another question I'll ask.

Thanks for any and all help!
1) you install and remove almost everything from the addremove programs in the applications menu.  There are other ways to do the same thing... like synaptic package manager.
you already have a messenger installed on your computer if oyu have ubuntu.  It's called pidgin.  Try it out... it's very nice.  If you want to do more with it, drop me a line and I can help you out... just pick any messenger that I use and we can get started. :D
It could be that the update server is very busy.  What version of ubuntu did you download and install... was in Ubuntu 8.04 Hardy Heron?
Happy to see your having fun... don't be afraid to ask us if you have more questions.

---

### Post by c4v3m4n on 2008-04-27
After the upgrade is all set up and the servers have been freed when you use your update manager it will give you an option to upgrade to 8.04.  Does it tell you it couldn't receive packages in synaptic package manager?  Or when using the terminal?

---

### Post by Can+~ on 2008-04-27
There's a simpler version of synaptic:

Applications > Add/Remove.

The big difference between windows and linux (at least, debian-like), is that you have full access to a "repository", which is a server holding packages of applications and libraries.

So with Add/Remove, you do a single click on a checkbox, "apply" and new software will be installed. Same for removing. Some people will tell you commands like "sudo apt-get install something", because it's the same as opening the Add/Remove program, but it's easier to copy and paste on the shell.

Welcome btw.:KS

---

