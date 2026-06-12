---
title: "Partial mouse &quot;lock&quot;"
date: 2014-02-05
forum: New to Ubuntu
---

### Post by Skye_Trust on 2014-02-05
Hello there,

obviously I'm an absolute beginner in Linux which is why I chose Ubuntu as it is said to be the most user friendly Linux OS. That said, please explain any suggestions and answers a bit in detail. Also I appologize should this problem have been discussed many times before, I could not find appropriate solutions.

On a sidenote, I have a Windows background. So please excuse any misused terms.

**The actual problem:**

The mouse will eventually be "locked" to a single application. For example, highlighting text within an application in the foreground will result in highlighting text in the "locked" application. This usually happens after a couple of minutes of using the application. Closing the "locked" app will lock the mouse to the next application that receives focus. Closing all applications will "free" the mouse and the bug will eventually reoccurr after a couple of minutes.

It certainly is not a hardware issue. I installed Ubuntu alongside Windows which does not have any issues at all. I also tried using a wired mouse and still experience the same issue.

I also noticed that the error already occurrs in the installation but not in the live demo. For example, when managing partitions, changing the role (Drop-down which says "Use as", I believe) of a partition, the popup ignores all input and instead the partition manager in the background receives all clicks even though the popup has focus. One can simply hit space or enter to activate the button and close the popup, or hit tab to change the focused element...
In contrast though, as said, the live demo works totally fine without any issues at all.

I tried updating Gnome and using it instead of Unity, to no avail. The error persists.

Before I try to install a different "flavor" of Ubuntu, I'd like to know whether there are any known solutions to this known problem? Several already existing threads on the Internet are mainly answered with *Me too* responses and seem not to lead to any solution.
From all this, my inexperienced humble self deduces that this could be a driver issue...

Thank you in advance for any leads, hints, or answers.

Sincerely


P.S.:
My rig, should anyone need it:
[LIST]
[*]Intel Core i5 CPU 750 @ 2.67GHz (Quad Core) x64 
[*]NVIDIA GeForce GTX 770 
[*]Seagate Barracuda 7200.11 1.5TB SATA HDD 
[*]8GB DDR3 RAM 
[*]Mad Catz R.A.T. 9 Mouse 
[/LIST]

---

### Post by QIII on 2014-02-05
Hello and welcome to the forums!

If this is a specialty mouse and is built for Windows, there might possibly be a problem with using it with Linux.  I don't know.

Before we start experimenting with all sorts of possibilities, can we see if we can eliminate that from consideration by booting the machine to Ubuntu with a plain old run-of-the-mill mouse that you know to be working?

Borrow one if you have to.  Let us know what you find.

Best wishes.

---

### Post by Skye_Trust on 2014-02-05
That... that actually did the trick! Now that's kind of embarrassing... I did test the other (wired) mouse, but I did not unplug the RAT9 which lead me to believe the error was hardware independent. I should've asked days ago, it would have saved me a lot of wasted time. Thanks for expanding my knowledge. ;) Checking the Internet whether said mouse has compatibility issues, I even stumbled upon [this little thread]("http://ubuntuforums.org/showthread.php?t=2159607") on these forums... ha. I guess I didn't do my homework well enough!

Many thanks, now that this is no longer bugging me, I can finally delve into the fascinating world of Linux!

---

