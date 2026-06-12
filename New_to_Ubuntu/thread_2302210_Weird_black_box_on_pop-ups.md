---
title: "Weird black box on pop-ups?"
date: 2015-11-08
forum: New to Ubuntu
---

### Post by Soprano_Aurora on 2015-11-08
Hey, new user here,

I installed Ubuntu yesterday. When I booted my computer (MacBook) into Ubuntu this morning, I noticed that a strange black box appeared on pop-up boxes.

[ATTACH=CONFIG]265425[/ATTACH][ATTACH=CONFIG]265426[/ATTACH]

I haven't noticed this before.

---

### Post by matt_symes on 2015-11-08
Hi

> **Soprano_Aurora said:**
> Hey, new user here,

I installed Ubuntu yesterday. When I booted my computer (MacBook) into Ubuntu this morning, I noticed that a strange black box appeared on pop-up boxes.

[ATTACH=CONFIG]265425[/ATTACH][ATTACH=CONFIG]265426[/ATTACH]

I haven't noticed this before.

Did you suspend and resume your laptop over night or did you shut it down and then start it up ?

Kind regards

---

### Post by Soprano_Aurora on 2015-11-08
I suspended and resumed, but the system hung on resuming. I had to forcefully shut it down.

---

### Post by matt_symes on 2015-11-08
Hi

> **Soprano_Aurora said:**
> I suspended and resumed, but the system hung on resuming. I had to forcefully shut it down.

You don't want to forcefully shutdown Ubuntu. The same goes for Windows and MACs as well. Try getting to a console and shutting down from there. 

I'm unsure if/how you  can run the magic key combination on a MAC keyboard but, assuming you can, that'll shut it down gracefully if you've not had a major kernel panic.

You did not mention what version of Ubuntu you are using or your graphics card so this information may not apply to you - I'm having to suppose here... 

The black borders may have something to do with this bug.

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1292830](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1292830)

Is this the same as your setup ? Is anything different ?

Kind regards

---

### Post by Soprano_Aurora on 2015-11-08
I have an nVidia GeForce 320M. Drivers have been installed :-)

Doing Ctrl-Alt-F2 doesn't do anything, it seems...

---

### Post by matt_symes on 2015-11-08
Hi

> **Soprano_Aurora said:**
> I have an nVidia GeForce 320M. Drivers have been installed :-)

Doing Ctrl-Alt-F2 doesn't do anything, it seems...

Does the workaround in post #8 of the link i posted above work for you ?

If so then you have the same issue as them.

I have not read through all the bug report as i'm trying to do three things at once at the moment, but you may want to.

It may provide a solution in the later posts.

BTW: I don't own a MacBook so i'm not sure the key combination to get to a console on it.

Kind regards

---

