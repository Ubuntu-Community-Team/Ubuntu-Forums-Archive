---
title: "Easy way? Or false hope?"
date: 2011-09-07
forum: Packaging and Compiling Programs
---

### Post by MG&amp;TL on 2011-09-07
Having forced my brain through the great literary works of the *debian new maintainer guide,* the *ubuntu packaging guide* and still made a fool of myself on this forum, I was understandably (I feel) a little bit annoyed with the debian packaging system in general. Don't get me wrong, it's wonderful for the end-user. Just not for the developer.

However, I did find a tool:

[http://www.ubuntugeek.com/ubucompilator-easy-way-of-creating-deb-packages-from-source-files.html]("http://www.ubuntugeek.com/ubucompilator-easy-way-of-creating-deb-packages-from-source-files.html")

BUT-does it's output produce .deb's that comply with ubuntu standards? Any fool can make a 'basic' .deb, but the ubuntu standards are somewhat more stringent.

I'm just hoping that either someone knows what they are doing and has the time and inclination to get ubucompilator, or somebody has used ubucompilator to make a repository entry.

Any joy? Thanks, forum!

---

### Post by SevenMachines on 2011-09-08
* Firstly, not making a fool of yourself! Mistakes have to be made to learn how something new.

* Personally I wouldnt hold out too much hope for something like ubucompilator, there have been a number of programs like this that have come and gone. At the end of the day it just tends to be quicker to run dh_make and edit the debian/ files.

* As I remember, your grubby packaging was almost done, the grubby.install file I posted was the only change I made to have a working package, albeit needing some *polish* :).

---

### Post by SevenMachines on 2011-09-08
Although, I note from this weeks ubuntu app developers week on irc that canonical is working on pkgme as part of their drive to enable app devs to easily add their stuff to the software centre without knowing about packaging, I've no idea quite how it'll work yet though.
[https://launchpad.net/pkgme](https://launchpad.net/pkgme)

---

### Post by MG&amp;TL on 2011-09-08
Cool. I'll see if I can get onto the dev team for that. Thanks for all your support and that, sevenmachines, I'm sorry I didn't post on that thread about this, I know it was almost done <guilty> It's just that actually my package had been superseded. So I was a bit depressed. :lolflag:

Yeah, I did make a fool of myself:

"Can I be cowardly, spineless and lots of other bad things, and ask someone to do it for me?"

But I appreciate the moral support. :)

---

