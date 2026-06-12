---
title: "eric4 + qt-designer: vague/general questions"
date: 2009-06-10
forum: Programming Talk
---

### Post by lykwydchykyn on 2009-06-10
I've written a few tools/scripts using pyqt4 just using Kate or emacs, but I got tasked with making a simple utility the other day at work and thought I'd try the "IDE way" to see if I could get things done a little cleaner.

I installed eric4 and qt-designer from the repositories and have been working with them for the last few days.  I don't know if anyone here uses these tools regularly, but I have a few general questions:

 - Not wanting to get into the nitty-gritty on these, but it seems like I eric is constantly spitting out errors and warnings at me about all kinds of stuff.  For example, when I click on a .ui file in my project manager, it gives me an error that qt3-designer is not installed (even though I've disabled qt3 support in the preferences and created the .ui in qt4-designer), and it complains that such and such shared plugin's name starts with "lib" or similar when I try to "save as".  Is this normal or is my system messed up?

 - The version in the repos seems a few point releases back, so I'm wondering if some of this stuff is fixed.  Is there a ppa with the latest eric, or at least a .deb somewhere?  I couldn't find one searching launchpad, and I like to stick to using the package manager.

 - Obviously I'm not used to working with these tools, but it really doesn't seem like I'm saving much work with them  I mean, I can lay out the form, but I still have to do a lot of gui-related things by hand.  For instance, I can only connect predefined signals/slots, which accounts for a tiny fraction of my signal/slot connections.  All my callbacks and so forth have to be done by hand.  Or am I missing something?

Anyone have any advice on getting up to speed on these tools?

---

### Post by misanthropist on 2009-06-21
I've tried ERIC too but had problems with the autocomplete hanging and the help assistant was missing. I couldn't find any ERIC support forums and Googling isn't productive because inevitably you end up with lots of articles about someone called Eric. Its a pity because ERIC does look like it has potential.
I've now switched to Eclipse + PyDev plugin which seems to be working well for me although it is very early days.

---

### Post by lykwydchykyn on 2009-06-22
Yeah, I muscled my way through using it for my project, and I sort of have the hang of it now.  I can't figure out how to use the debugger, though.  There is no help file and no tutorials online.  What a shame, because it seems like someone has put an awful lot of work into it.

I tried eclipse a while back, but it was a little confusing.  It seems like one of those pieces of software you have to be "in to" to really use.  IIRC, it did have much better autocompletion than Eric.  Finding good python development plugins was kind of a pain.

---

