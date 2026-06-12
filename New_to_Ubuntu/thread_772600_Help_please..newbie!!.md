---
title: "Help please..newbie!!"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by mc2000 on 2008-04-28
I installed Ubuntu a few days ago and learning as I go  lol. Anyways, now when I try to access System Package Manager I receive this error....

E:dpkg was interrupted, you must manually run 'dpkg --configure - a' to correct the problem.
E: cache-> open() failed, please report.

How do I do that?  How did I create this problem?

---

### Post by LaRoza on 2008-04-28
> **mc2000 said:**
> I installed Ubuntu a few days ago and learning as I go  lol. Anyways, now when I try to access System Package Manager I receive this error....

E:dpkg was interrupted, you must manually run 'dpkg --configure - a' to correct the problem.
E: cache-> open() failed, please report.

How do I do that?  How did I create this problem?

Open a Terminal. (Application->Accessories->Terminal) 

Run:

```

sudo dpkg --configure -a

```

(Enter your password, you will not see it on the screen. Just type it and press enter)

---

