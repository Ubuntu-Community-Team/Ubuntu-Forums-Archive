---
title: "Need command line to determine compositing"
date: 2012-03-01
forum: Programming Talk
---

### Post by rg4w on 2012-03-01
I'm working on an app in which I need to have one of two different UIs depending on whether rich window compositing is available, similar to how Unity chooses between "3D" and "2D".

There are C interfaces for this, but it would be a tremendous time-saver if I could just make a Bash call.

I didn't see anything in env which would tell me this - where should I look?

TIA -

---

### Post by ofnuts on 2012-03-01
> **rg4w said:**
> I'm working on an app in which I need to have one of two different UIs depending on whether rich window compositing is available, similar to how Unity chooses between "3D" and "2D".

There are C interfaces for this, but it would be a tremendous time-saver if I could just make a Bash call.

I didn't see anything in env which would tell me this - where should I look?

TIA -TCompositing can be dis/enabled on the fly (typically set of on my machine when it enters the more aggressive power saving modes).

---

