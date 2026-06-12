---
title: "Can anyone recommend a defrag and/or optimization tool?"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by SammySpencer on 2008-05-11
Hey, folks!

Now that I have Ubuntu 7.1 installed, running smoothly without any broken applications, and with a number of applications installed, I'd like to be able to clone this computer for not only back-up purposes, but also to place it onto another computer.  I have heard that Clonezilla is good for this.  Any input on that?

Before I clone, though, there are a couple things I'd like to do.  After running Disk Usage Analyzer, I see that my hard drive needs some major defragging.  Ubuntu doesn't seem to come with any defragging tools, nor do I know of any.  Can anyone suggest a good tool?

Coming from the "Windows world," I always use an optimization tool to repair the tons of issues that develop in Windows from just daily use (or even from a clean install).  Are there any such tools that should be used for Ubuntu?  I am glad to see that I have no broken applications, but I can tell that my system is running more sluggishly than it had when I first installed.  Is it a good idea to use an optimization tool (such as Norton SystemWorks) for Ubuntu (or Linux in general)?  Can anyone make any recommendations?

Thank you again, folks!


Sincerely,

Sammy Spencer

---

### Post by SunnyRabbiera on 2008-05-11
No defrag needed in ubuntu, as linux firesystems dont have as many issues with that sort of thing.
Your slowdown might be coming from all the applications you run at a time, its hard to say as we dont know what you installed.

---

### Post by SammySpencer on 2008-05-11
Hmmm...  My slow-down issues seem to be centered around Firefox (the build which was installed with Ubuntu 7.1).  In fact, as I watch the system monitor, memory and hard drive load are almost always maxed-out.  I do have a few extensions set up (similarly as I had with Windows), but it seems to be the culprit.

One extension I have is the Beagle indexing extension.  Could this be what may be causing my slow-down?  Or are there any other known culprits?

So, one doesn't need defrag or optimization tools with Ubuntu, eh?  That's good to know.

Thanks for your feedback!


Sincerely,

Sammy Spencer

---

### Post by mmb1 on 2008-05-11
Like SunnyRabbiera said, Ubuntu doesn't need to be defragged, and I'm unaware of any maintenance that needs to be done. :)

Here's a more detailed explanation: 

[http://www.whylinuxisbetter.net/items/defragment/index.php?lang=](http://www.whylinuxisbetter.net/items/defragment/index.php?lang=)

---

### Post by mmb1 on 2008-05-11
Firefox is known to be a memory hog, but this is supposed to be fixed in version 3.  I reccomend Kazehakase if you get the chance.

---

### Post by inportb on 2008-05-11
Firefox has always been slow for me. On Windows, it's optimized... on Ubuntu, it's not. You can rebuild it so that it is, or go for something like Swiftweasel.

---

### Post by jameswillmer on 2008-05-11
beagle indexes everything at the start (same way as google desktop)
just let it complete and then it will be fine....

JW

---

### Post by Puptentacle on 2008-05-11
I'm having fewer issues with Firefox in Hardy than I had previously with Gutsy but it will occasionally grab all the resources it can get it's grubby little paws on. At least it's not freezing on 80% of all flash video anymore!

I would run system monitor on the resources tab set for always on top and try to determine what is causing the problem.

---

### Post by SammySpencer on 2008-05-11
I have been playing around with Firefox, and have localized that it seems to be the problem with my memory issues.  I have even disabled all of my extensions, and the memory load always remains around 90%.

I would consider upgrading to the new version of Firefox, or possibly even using a different Web browser.  The only show-stopper issue I have is that I need to be able to use [LogMeIn]("http://www.logmein.com/") so as I can connect to my office and work remotely.  I had the hardest time getting it to function properly with the Firefox 3 beta, which was a driving issue for me to use Ubuntu 7.1 instead of 8.04.  (It works great with Ubuntu 7.1.)  Has anyone had any luck using LogMein with other Web browsers?

I suppose I could always install another Web browser and give it a try.  I'll report back here to let others know how it went.

Thanks for the great feedback!


Sincerely,

Sammy Spencer

---

### Post by SlappyPappy on 2008-05-12
Dude, I've cloned my Gutsy twice now even though people warned me not to. I started on a 20GB as a test bed for Ubuntu. Then I moved up to a 60GB using the following tutorial. EZ as pie.

[http://ubuntuforums.org/showthread.php?t=599599](http://ubuntuforums.org/showthread.php?t=599599)

Then I cloned the 60 to a 120GB drive someone gave me later. Still works great! No hiccups that I've found at all. Only thing I found out of wack was the UUID in fstab for the swap partition but all I did was find out what the correct UUID is and changed that in fstab using nano.

Good luck!  :)

---

### Post by SammySpencer on 2008-05-12
As a follow-up, I found that LogMeIn works with Iceweasel.  Though, I must say, Iceweasel consumes about the same amount of memory as Firefox 2 does.  On the plus side, Iceweasel has a much smaller system load than Firefox 2.

Thanks for everyone's input!


Sincerely,

Sammy Spencer

---

