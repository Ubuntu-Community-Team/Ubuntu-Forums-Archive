---
title: "[SOLVED] ATI woes solved"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by upptown on 2008-05-16
I have been dealing with the white screen after enabling compiz effects and black screen after splash issues for days with my ATI X1300.

At first I thought it was the result of some new update but after three re-installs I was still getting nowhere near being able to use the restricted drivers or compiz.

After many hours of searching I ran into one post that mentioned BIOS settings.  Now I thought to my self "Self, didn't you adjust the AGP aperture just recently...?" (Self and I talk a lot)

Long story short, the fglrx driver does NOT like an aperture lower than 64 or higher than 128.  Anything other than those two settings resulted in failure.

Hope this helps someone.

---

### Post by talsemgeest on 2008-05-16
Good man for helping others, it's what this forum is all about.

Might be a good idea to mark this thread as solved though...

---

