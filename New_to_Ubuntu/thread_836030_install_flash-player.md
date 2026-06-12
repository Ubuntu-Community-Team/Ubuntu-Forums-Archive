---
title: "install flash-player"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by ignorant fool on 2008-06-21
i am trying to install flashplayer. first of all i have no idea whether to pick .tar.gz or .rpm or YUM and there is no guidance on the adobe site at all to which one i must pick, so hell i picked tar.gz now it asks me to type ./flashplayer-installer in the terminal it sais: command not found. i tried it with out the dot and without the slash too, doesn't work either.
am i gonna need to use this terminal thing all the time? because the reason i want to use ubuntu is because vista is full of stuff like that. i just want a simple OS, that doesn't require me to know alot or go through complicated things, like this. even in vista this would be easier.

---

### Post by housam on 2008-06-21
use this guide :[[COLOR="Red"]_http://www.psychocats.net/ubuntu/flash_[/COLOR]]("http://www.psychocats.net/ubuntu/flash")

---

### Post by Sinkingships7 on 2008-06-21
Alternatively, you can just type
```
sudo aptitude install flashplugin-nonfree
``` into the terminal and you should be good to go.

---

### Post by Pjotr123 on 2008-06-21
This is an easy method for full 100 % multimedia support (not just flash):

Step 1:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

Step 2:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

---

### Post by crossedout on 2008-06-21
Assuming you are using Hardy and FF3.0, I can tell you what worked for me.

Go to a page that you know requires flash, obviously it won't work but you should be presented with an option to install missing plugins.  Simply click on the install icon and select the first choice (there were 3 for me).  The rest is painless as it walks you through it step-by-step, installing flashplugin-nonfree.
Much to my surprise that worked like a dream, I had nothing to lose by giving it a shot and since manually setting it up has been the norm (for me) in the past I figured I'd just do it that way if FF's install failed.

Good Luck!
-Xout

---

### Post by ignorant fool on 2008-06-23
im doing pjotr123's reccomendation now. however. is this terminal gonna have to be used often, because i really think that if linux wants to be accessible to everyone, the terminal should not be needed at all. its not easy to use.

ok i got it now. but still this terminal thing is too complicated for normal people.

---

