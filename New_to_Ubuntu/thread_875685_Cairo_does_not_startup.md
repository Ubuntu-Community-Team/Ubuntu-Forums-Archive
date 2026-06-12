---
title: "Cairo does not startup"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by Frenske on 2008-07-31
He there, a small problem. I have put cairo in the list of startup programs and used 'cairo-dock' as the command. For some kind of weird reason it works sometimes but most of the time it does not (perhaps related if I hat it opened previous session).

Any ideas on what is going on and how to rectify it?

---

### Post by norwizzle on 2008-07-31
Is the process listed as running? Check the system monitor after starting up.

---

### Post by Frenske on 2008-07-31
Yes, it is! I guess the problem is cairo itself. But then when I start it through application it works as it should!?

---

### Post by norwizzle on 2008-07-31
> **Frenske said:**
> Yes, it is! I guess the problem is cairo itself. But then when I start it through application it works as it should!?

Hmm, maybe it has something to do with the auto-hide feature? Did you try hovering your mouse near the bottom? 

BTW I'm no expert at this but having just installed and tweaked cairo I'm thinking that maybe I can help.

---

### Post by Frenske on 2008-07-31
Okay, I will have a look at the settings when I am back at home. A man's gotta do what a man's gotta do and in this case work.

---

### Post by fabounet on 2008-07-31
you can try to replace 'cairo-dock' with 'launch-cairo-dock-after-beryl.sh', which is just a script that launches the dock after the WM. (with Beryl it was needed)

---

