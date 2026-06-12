---
title: "Tulong sa pag-ayos ng orasan"
date: 2008-12-17
forum: Philippine Team
---

### Post by randytan on 2008-12-17
Hi All!

Kumusta na?

Well, I finally did it... No more XP, just pure Ubuntu on my office notebook and I love it! The speed and ease are just great!

Now for the sad news, apparently my recurring problem of the notebook typing the letter "n" after a while is already a hardware problem. :(

Since my system is up and running again, my boss agreed to have my unit repaired rather than replaced with another old notebook =D>

The "n" thing is really annoying and may have screwed up my upgrade from 8.04 to 8.10. My notebook went into screensaver mode while the unit was updating and the "n" issue popped up and I was no longer able to type in my password to get back in. Thinking that my hard drive light was due to the "n" issue, I shut the thing down and restarted it. Alas, it froze as the install was already apparently underway and I had interreupted it.

I replaced the 8.04 disc and got to install it again and update the system. During the course of installing all the programs I needed, I noticed that my firefox icon was gone and was replaced a monitor icon. Clicking on it made my system complain that the child folder or something could be found. This was the same for my evolution, pidgin, and skype. I had to re-install them via the synaptic manager and all was well. :oops:

Now on to the topic at hand, when I tried to manually change the time on my system's clock to reflect company time (which is 15 minutes faster than the rest of the world) when I clicked on "OK" to apply the new time, I keep getting the message:

[INDENT]Failed to set the system time
The name org.gnome.PolicyKit was not provided by any .service files[/INDENT]

Any idea on what's wrong and what I can do to rectify it?

Hindi naman siyang malaking problema pero since OC ako, gusto kong gumagana lahat ng sistema ng maayos. :oops:

Pasensya na sa mahabang post pero I wanted to make sure that you all had a little background on what happened in the hopes that it can shed a little light on what could've gone wrong.

Thanks.

Hope to hear from you guys again soon.

Best regards! ):P

---

### Post by loell on 2008-12-17
weird problem, try installing [policykit-gnome]("apt:policykit-gnome")

then try setting the time again.

---

### Post by randytan on 2008-12-17
Hi loell!

That did the trick.

Thanks a bunch!

:guitar:

---

### Post by loell on 2008-12-19
anytime.. no sweat. :D

---

