---
title: "[Hardy Heron] Num lock is on but numbers dont work in Gnome and work in Consoles"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by legolas_w on 2008-04-30
Hi
I have problem with my keyboard, sometimes after some hours which my computer is on the numbers which are located on numpad does not work :O
even I tried to restart the X environment and it has no effect by using ALT+CTRL+BackSpace.

Numbers works fine in other environments (e.g ALT+CTRL+F3). but they do not work in x environment.


Any comment?

Thanks.

---

### Post by alienexplorers on 2008-04-30
Try removing xnumlock:
> sudo apt-get remove numlockx
then try reloading it
> sudo apt-get install numlockx

---

### Post by bluefrog on 2008-04-30
at first wanted to tell you to check system/pref/keyboard mouse keys tab and uncheck the box, but now that I see the full text of your message I wonder why your numpad would work then stops.

---

### Post by bluefrog on 2008-04-30
you would not press <alt> <shift> <numlock> from time to time by chance?

---

### Post by legolas_w on 2008-04-30
> **bluefrog said:**
> you would not press <alt> <shift> <numlock> from time to time by chance?

Thank you for the reply.
It was the problem :O
Can you tell me what happens when we press alt+shift+numlock?
when I press it again my numpad start working :-)

PS: How I can mark this thread as solved?

thanks again.

---

### Post by bluefrog on 2008-04-30
should find the option in thread tools

---

