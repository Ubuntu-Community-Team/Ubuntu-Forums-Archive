---
title: "[SOLVED] [Java] Make JFrame have exclusive access"
date: 2008-08-12
forum: Programming Talk
---

### Post by Despot Despondency on 2008-08-12
Hey, I was wondering how to make a JFrame exclusive, i.e. so that I can't access any other JFrames while this frame is open? (Like those annoying error message boxes that you have to close before you can do anything else on your computer.) Had a look at the API and I can't seem to find any relevant methods. Thanks in advance.

---

### Post by Reiger on 2008-08-12
You must be talking JOptionPanes. And you know what the good news is...? JOptionPane static methods take *any* object for a message -- meaning you can have an entire Swing app being the ... message?

---

### Post by Java Geek on 2008-08-12
> **Reiger said:**
> You must be talking JOptionPanes. And you know what the good news is...? JOptionPane static methods take *any* object for a message -- meaning you can have an entire Swing app being the ... message?

I had a similar problem with a project long past. Thanks!

---

### Post by Despot Despondency on 2008-08-13
Cool, thanks. Never heard of JOptionPane before, or noticed it on the API. I'll have a play around with it. Cheers :)

---

