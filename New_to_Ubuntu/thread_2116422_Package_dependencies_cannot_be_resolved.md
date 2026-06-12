---
title: "Package dependencies cannot be resolved"
date: 2013-02-15
forum: New to Ubuntu
---

### Post by Lordofthrall on 2013-02-15
Whenever I try to download anything from the Ubuntu Software Center, I get this error: Package dependencies cannot be resolved. Then I just exit out of the software center and all is well, but does anyone know how to fix this?? The programs I tried in particular were Wine and Steam. This is a problem I'm having on both my laptop and my desktop even after installing all updates so I'm lost. Thanks for the help!

---

### Post by slickymaster on 2013-02-15
Open the terminal and try the following commands:
```
sudo dpkg --configure -a       
sudo apt-get install -f
```

---

### Post by Lordofthrall on 2013-02-15
I entered both of those into the terminal and followed what they asked and then tried again but to no avail :( Thanks for the try though

---

### Post by slickymaster on 2013-02-15
I have to apologize to you, in my previous post I misplaced the position of the argument. It should be:
```
sudo apt-get -f install
```

But in the case that also doesn't work, go to Synaptic Package Manager and open Edit--Fix broken packages.

If you don't have Synaptic installed, or you don't want to install it, you can try this:
[How To Fix Broken Packages In Ubuntu Or Debian]("http://www.thepowerbase.com/2012/04/how-to-fix-broken-packages-in-ubuntu-or-debian/")

---

### Post by Lordofthrall on 2013-02-15
Thank you very much Slicky! :D Everything checks out now! My deepest thanks to you!

---

### Post by slickymaster on 2013-02-15
Glad you got it fix. Don't forget to mark the thread as SOLVED.

---

