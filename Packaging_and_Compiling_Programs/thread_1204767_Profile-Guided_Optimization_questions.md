---
title: "Profile-Guided Optimization questions"
date: 2009-07-05
forum: Packaging and Compiling Programs
---

### Post by lovinglinux on 2009-07-05
I'm trying to compile Firefox 3.5 with PGO enabled.

It seems that using the following option works:

mk_add_options PROFILE_GEN_SCRIPT='$(PYTHON) $(MOZ_OBJDIR)/_profile/pgo/profileserver.py'

But whenever I try to create my own profile script, the profile is created in the objdir, Firefox is launched with the new profile, but the compilation stops later due to some profile corruption. Any ideas what could be happening?

Additionally, I would like to better understand the concept behind PGO. I understand that the compilation is performed in two steps, "like" for example when you transcode a divx movie using two passes. A test profile is created and Firefox is launched, but what I'm supposed to do? Do I need to visit some sites I usually visit or that perform bad on my Firefox or should I just close it? If I need to interact, how long is enough to create a decent profile?

Another question is, what exactly profileserver.py do besides creating the profile folder? It launches Firefox but closes it just a few seconds later. Is there any advantage of using  a custom profile instead of profileserver.py?

---

