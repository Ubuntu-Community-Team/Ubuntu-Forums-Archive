---
title: "Microsoft Natural Keyboard Elite problem"
date: 2013-05-02
forum: New to Ubuntu
---

### Post by ptwil on 2013-05-02
Hello all;

I am using the Microsoft Natural Keyboard Elite keyboard with 13.04 (64 bit) and some keys either don't work or only work sometimes. The keys tend to be on the number row (first row), keys 3,4 seem to be most often affected (there is a separate keypad and as can be seen it does work with num lock on). Does anybody have any suggestions? Thanks

---------------------

In consideration of the comment below, I am leaning towards a hardware issue as well and so I will declare this solved or at least better understood. Thanks to all who assisted

---

### Post by m_duck on 2013-05-02
Are the non-working keys fairly random? It sounds as though it could be a hardware problem. Have you tried the keyboard on another computer/OS or using a live CD?

Otherwise you could try running xev from the command line and pressing the keys to see if anything is registering with Xorg at all.

---

