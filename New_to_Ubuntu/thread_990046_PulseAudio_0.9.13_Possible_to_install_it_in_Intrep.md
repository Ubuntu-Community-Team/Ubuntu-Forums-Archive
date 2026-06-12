---
title: "PulseAudio 0.9.13 Possible to install it in Intrepid?"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by Kosimo on 2008-11-22
Hello.
I am wondering if it is possible to update pulseaudio in intrepid, from 0.9.10 to 0.9.13 witch is the latest stable version with tons of bugfixes.

Thank you!

---

### Post by igknighted on 2008-11-22
> **Kosimo said:**
> Hello.
I am wondering if it is possible to update pulseaudio in intrepid, from 0.9.10 to 0.9.13 witch is the latest stable version with tons of bugfixes.

Thank you!

WARNING: DO THIS AT YOUR OWN RISK.  BREAKAGE MAY OCCUR AND YOU MIGHT NEED TO REINSTALL

If you don't mind living on the wild side a bit, change all your sources to jaunty (from intrepid), mark pulseaudio for update (0.9.13 is in Jaunty), install it and let it update all needed dependencies, then change your sources back.  Enjoy.

---

### Post by Kosimo on 2008-11-22
> **igknighted said:**
> WARNING: DO THIS AT YOUR OWN RISK.  BREAKAGE MAY OCCUR AND YOU MIGHT NEED TO REINSTALL

If you don't mind living on the wild side a bit, change all your sources to jaunty (from intrepid), mark pulseaudio for update (0.9.13 is in Jaunty), install it and let it update all needed dependencies, then change your sources back.  Enjoy.

Ouch!  That hurted :P

---

### Post by igknighted on 2008-11-22
> **Kosimo said:**
> Ouch!  That hurted :P

I've installed out of the next version's repo plenty of times and never borked my system, so it is feasible.  But it is a possibility when mixing repo's, so I feel the need to give fair warning.  I wouldn't try it if a reinstall was a completely unacceptable outcome, but if you don't mind trying something, by all means, go for it.

---

### Post by Kosimo on 2008-11-22
> **igknighted said:**
> I've installed out of the next version's repo plenty of times and never borked my system, so it is feasible.  But it is a possibility when mixing repo's, so I feel the need to give fair warning.  I wouldn't try it if a reinstall was a completely unacceptable outcome, but if you don't mind trying something, by all means, go for it.

Let me ask you a question.
So if I change all my sources, then it'll update almost everything, not only pulseaudio, right? How can I only update what I need in order to have latest PulseAudio and all pulseaudio tools updated?

Thank you again

---

### Post by igknighted on 2008-11-22
> **Kosimo said:**
> Let me ask you a question.
So if I change all my sources, then it'll update almost everything, not only pulseaudio, right? How can I only update what I need in order to have latest PulseAudio and all pulseaudio tools updated?

Thank you again

Either in synaptic just mark pulseaudio for upgrade, or "apt-get upgrade pulseaudio" should do the trick on the cli.  Just look at the list of what is being updated before you click ok... it will need some other dependencies I am sure, but if it bringing in the kitchen sink I might not do it.

---

### Post by Kosimo on 2008-11-22
> **igknighted said:**
> Either in synaptic just mark pulseaudio for upgrade, or "apt-get upgrade pulseaudio" should do the trick on the cli.  Just look at the list of what is being updated before you click ok... it will need some other dependencies I am sure, but if it bringing in the kitchen sink I might not do it.

I'll may give it a try first to a virtual machine, then I'll see what I can do. Thanks for helping ;)

---

### Post by kostkon on 2008-11-22
It think there is a new version coming in *Intrepid*. It is currently in the *Proposed* repo, so, if you want, you can activate the repo to get the update.

It is not a major version change, I think from *0.9.10-2ubuntu9* to *0.9.10-2ubuntu9.1*.

---

### Post by igknighted on 2008-11-22
> **Kosimo said:**
> I'll may give it a try first to a virtual machine, then I'll see what I can do. Thanks for helping ;)

Always a safe bet... good luck!

---

