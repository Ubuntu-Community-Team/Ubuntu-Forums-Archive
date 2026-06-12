---
title: "HowTo: Fix broken Lightning extension in Thunderbird after Jaunty upgrade"
date: 2009-05-01
forum: Outdated Tutorials &amp; Tips
---

### Post by Rocket2DMn on 2009-05-01
I found that after upgrading to Jaunty, the Lightning extension in Thunderbird stopped working, which I use for Tasks.  I believe this applies to those who downloaded the extension from the web, rather than installing it from the Ubuntu repositories.

The following directions are derived from Launchpad bug [lpbug]278853[/lpbug].

First remove Lightning from Thunderbird: **Tools->Addons**, select Lightning, and uninstall.  Close Thunderbird.

Now install libstdc++5:
```
sudo apt-get install libstdc++5
```

If you don't have the .xpi file for Lightning, get it at [https://addons.mozilla.org/en-US/thunderbird/addon/2313](https://addons.mozilla.org/en-US/thunderbird/addon/2313)

Now open Thunderbird again, and go back to **Tools->Addons**.  Click the Install button, and browse to the extension file, lightning-0.9-tb-linux.xpi - click Open.  At the Software Installation prompt, click Install Now after the short countdown, then click Restart Thunderbird.

Enjoy.

[UPDATE]

In 9.10 Karmic Koala, the libstdc++5 package is no longer available in the repositories.  You will have to uninstall the Lightning extension in Thunderbird (Tools->Addons), then install the Lightning plugin direct from the Ubuntu Universe repositories.
```
sudo apt-get install lightning-extension
```

---

### Post by asatsi on 2009-05-15
Thanks alot dude. You rock!

---

### Post by KarenAK on 2009-05-23
This worked perfectly in Intrepid as well - had to use Sunbird before, because Lightning just didn't work.


THANK YOU :-)

---

### Post by Kiwi Jono on 2009-06-01
Fantastic!

I just upgraded to Jaunty and was totally lost without my Calendar at work. Now all good again!

Cheers.

---

### Post by wolfie2x on 2009-06-03
THANK YOU!

Can't believe I wasted 3 days on this. I just remembered after seeing this that I did the same in hardy too. 

Why isn't this still fixed? It's a simple dependency fix from what I understand. It's the usual finger pointing with "My component works perfectly; it's the other one that has a problem"; And the end user suffers!

btw, is lightning still being actively developed? and is Thunderbird going to have a built-in calendar in 3.0 (with meeting request support)?

---

### Post by enigma32 on 2009-06-11
This package (libstdc++5) saved my life (thunderbird/lighting).
Thank you.

---

### Post by ajgreeny on 2009-06-21
I have just spent a very frustrating amount of time trying to get the lightning extension installed in 9.04 on my wife's Compaq CQ70 211EM laptop, using the instructions on the mozilla website, but could not get it to work at all; it just sat there uselessly doing and showing nothing.

It was only by accident that I then found the extension when using synaptic, so tried installing that way.  Two extra dependencies were needed, and "Bingo!"  it now works just as I expected it to.

Is there something about ubuntu that is different from most other OS installations?  Incidentally, I have had lightning on my own machine since it first appeared without either of the two dependencies added by synaptic, and my system worked and still works brilliantly, also on 9.04.  What is going on, anyone know?

Incidentally, I have the libstdc++5 & 6 packages installed on my machine, my wife only had libstdc++6, but the two dependencies synaptic added must have the same effect as the libstdc++5.

---

### Post by sancho panza on 2009-06-25
Thanks!

---

### Post by posterberg on 2009-09-08
Thank you!

---

