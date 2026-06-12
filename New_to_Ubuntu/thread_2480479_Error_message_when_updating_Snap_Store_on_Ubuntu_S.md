---
title: "Error message when updating Snap Store on Ubuntu Software"
date: 2022-10-31
forum: New to Ubuntu
---

### Post by ddavid59 on 2022-10-31
I've just recently installed ubuntu 22.04 LTS on my old laptop (Acer Aspire V3-111P-C6LQ; Intel Celeron N2930; 4GB DDR3: 500GB HDD). I'm a complete beginner when it comes to computing.

Upon updating the software, I received the following error message:

> 
Unable to update "Snap Store":
(null): cannot refresh "snap-store": snap "snap-store" has
running apps (ubuntu-software), pids: 1968


Can anyone help me what does this mean and how can I resolve it? Thank you in advance.

---

### Post by Holger_Gehrke on 2022-10-31
For some reason the snap store stays in memory and running when you close it's window. This is AFAIK an intentional design choice to speed up starting it a second time after closing it. IMHO a questionable choice since it's not a small program. Obviously you can't update a program that's still running. You can stop it by either running 'snap-store --quit' or by sending it the termination signal (SIGTERM) using the 'kill' command with the PID, for example 'kill 1968'. After stopping the snap-store you can update it using 'snap refresh snap-store'.

Holger

---

### Post by ddavid59 on 2022-10-31
Oh my gosh! Thank you so much! I tried your recommendation and it worked!

Plus, I simply typed the command in the terminal and in a few minutes, it magically resolved. A big thank you to you!

---

