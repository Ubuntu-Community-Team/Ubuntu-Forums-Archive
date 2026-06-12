---
title: "Octave"
date: 2012-10-24
forum: New to Ubuntu
---

### Post by enperera on 2012-10-24
Hi...
I just installed Octave and I got the follow message in a terminal window when I tried to run it:

GNU Octave, version 3.2.4
Copyright (C) 2009 John W. Eaton and others.
This is free software; see the source code for copying conditions.
There is ABSOLUTELY NO WARRANTY; not even for MERCHANTABILITY or
FITNESS FOR A PARTICULAR PURPOSE.  For details, type `warranty'.

Octave was configured for "i686-pc-linux-gnu".

Please advise me, what can I do to get run it?

---

### Post by newb85 on 2012-10-24
So, after that message, does it return you to the normal command prompt (ending in $)?

What architecture are you using?

---

### Post by wojox on 2012-10-24
> **enperera said:**
> 
Octave was configured for "i686-pc-linux-gnu".

Virtual Machine?

---

### Post by enperera on 2012-10-26
> **newb85 said:**
> So, after that message, does it return you to the normal command prompt (ending in $)?

What architecture are you using?

Yes, it returns to the prompt...my machine is i386...thank you!

---

### Post by enperera on 2012-10-26
> **wojox said:**
> Virtual Machine?

No, it's a i386 running Ubuntu 11.10...thank you!

---

### Post by newb85 on 2012-10-26
How did you install Octave?

---

### Post by enperera on 2012-10-28
> **newb85 said:**
> How did you install Octave?

Through  Synaptics

---

### Post by newb85 on 2012-10-28
I don't know why, but it seems octave was mis-configured upon installation.

I would try completely removing and reinstalling octave.

```
sudo apt-get purge octave3.2
sudo apt-get install octave 3.2
```

---

### Post by El Tito on 2012-10-28
Hi there.

You don't have the latest version of octave (mine is 3.6.2), although this can't be the problem. When you type [COLOR=Blue]*octave*[/COLOR] in a terminal, do you get the following promt?:

*octave:1>*

if so, then everything is ok. I'm used to the matlab interface, you could try to install a friendlier interface:

*apt-get install qtoctave*

hope this helps.

---

