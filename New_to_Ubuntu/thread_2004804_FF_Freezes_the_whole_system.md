---
title: "FF Freezes the whole system?"
date: 2012-06-16
forum: New to Ubuntu
---

### Post by mapes12 on 2012-06-16
I set my Dad up with an Ubu machine a while ago. He's been getting along fine with it. But recently he received a unsolicited email with a hyperlink in it. Foolishly (his words, not mine) he clicked the link. It took him to some page he can't remember and now FF appears to be totally screwed. It goes to a home page that we didn't set. The mouse wont move. And the HDD just thrashes away.

The machine starts and runs fine but as soon as I we launch FF the faults above initiate. The only way I can get it to stop is by pressing the reset key. 

I've tried completely removing FF in Synaptic then reinstalling it but no joy. 

The machine's running 10.04

Any ideas how I can fix this without going through a fresh install?

---

### Post by UltimateCat on 2012-06-16
A fresh install is something I would probably consider, but first maybe try scanning your Dad's system with anti-virus program.

I opened an unwanted e-mail a while back and Avast for Linux detected a virus associated with an e-mail I opened. 

I'm not the best a diagnosing Operating System hang ups but there are very well educated folks in this group.  Sorry I don't know more...


[http://www.avast.com/de-ch/linux-home-edition](http://www.avast.com/de-ch/linux-home-edition)

---

### Post by Frogs Hair on 2012-06-16
Export the bookmarks if needed , close Firefox , open home / hidden folders (Ctrl + H) and delete the .mozilla folder .

This will allow you to have brand new profile the next time Firefox is opened . He probably didn't encounter a virus but a browser exploit.  After removing the folder all extensions will need to be installed again .

Reinstalling will not remove a corrupted profile , but removing the folder will.

---

