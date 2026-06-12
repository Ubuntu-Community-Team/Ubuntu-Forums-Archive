---
title: "Update manager error message?"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by wdypdx1 on 2008-10-02
Can someone tell me what this means:

W: GPG error: [http://apt.wicd.net](http://apt.wicd.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY(some code here)

It occurs when I go into update manager and have it check. Is it some problem that I need to fix? Or what?

thx

---

### Post by houbysoft.xf.cz on 2008-10-02
What do you mean by "(some code here)"? Does it say that in the real output? If it really says some code, please post it, if not, it's probably a bug, just do nothing and wait and try again in some hours/days/weeks/years :) to see if it's fixed.

---

### Post by knattlhuber on 2008-10-02
When you add a third party repository (in your case, the Wicd repo) to Synaptic, you usually add a repository address and a GPG key. The GPG key is an encryption key that makes sure that the updates indeed come from that repository and not from someone who tries to sneak in malicious code.

That error message says that it can't find the GPG key for Wicd. What's strange though is that the Wicd repo doesn't have a key, at least according to their website ([http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)).

I would try to remove the repo using Synaptic and then add it back in and see what happens.

**EDIT:** I stand corrected. They provide a public key ( [http://apt.wicd.net/](http://apt.wicd.net/) ).

---

### Post by knattlhuber on 2008-10-02
Hey, here's the answer:
[http://ubuntuforums.org/showthread.php?p=5885913]("http://ubuntuforums.org/showthread.php?p=5885913")

If you need help with that, let us know.

---

### Post by wdypdx1 on 2008-10-03
Thanks, after 3 weeks on ubuntu, I learn a little more every day.

---

