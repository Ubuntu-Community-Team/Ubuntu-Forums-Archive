---
title: "Problems with FONTS in java"
date: 2009-11-13
forum: Programming Talk
---

### Post by psychok7 on 2009-11-13
hey there.. im developing a cross-platform program in java and im using swing with netbeans. The thing is i have set some fonts in ubuntu (purisa in my case) and when i switch it to windows it gives me the default font.
Is there a way i can install that font in windows? or any other ideas to fix my problem?

thanks

---

### Post by Reiger on 2009-11-13
Well, presumably you configured your desktop to use Purisa as its default font for certain purposes which is why Java picks it up as default on your development platform -- but because it is not the default on your Windows environment it is not used there.

You can (a) set the font via various Java system properties; (b) configure your GUI with code to the same effect (setFont()); (c) use a 3rd party software library to do so (e.g. Java CSS or Swing Appframework)

---

### Post by psychok7 on 2009-11-13
> **Reiger said:**
> Well, presumably you configured your desktop to use Purisa as its default font for certain purposes which is why Java picks it up as default on your development platform -- but because it is not the default on your Windows environment it is not used there.

You can (a) set the font via various Java system properties; (b) configure your GUI with code to the same effect (setFont()); (c) use a 3rd party software library to do so (e.g. Java CSS or Swing Appframework)

b)doesnt really work for me.. the setfont it the same even in windows(purisa) but still is the default that appears. a)seems to be exactly like be but with GUI right? .. ill i have is c) to try out

---

