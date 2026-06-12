---
title: "Error: Access control for X is disabled for root"
date: 2012-09-21
forum: New to Ubuntu
---

### Post by neuronetv on 2012-09-21
I asked this question on the backtrack forum but got no help, and as backtrack is based on ubuntu....
I'm accessing a backtrack5 machine using an ssh console from another pc running putty. whenever I start airoscript-ng I get:
**Error: Access control for X is disabled for root. Please, as your normal user execute 'xhost +root' and press enter to continue.**
logging in as a normal user and doing 'xhost +root' gives me: **xhost: unable to open display**. (can't do anything with that).
the airoscript-ng program will proceed nevertheless but after choosing a resolution I get:
[B]Warning: This program is an suid-root program or is being run by the root user. The full text of the error or warning message cannot be safely formatted in this environment. You may get a more descriptive message by running the program as a non-root user or by removing the suid bit on the executable.
xterm Xt error: Can't open display: %s[/B]

and when I get to the attack box and choose an ARP attack the program seems to jam up, flickers the above message when I press return and won't proceed.
I've been trawling google and cannot find a straightforward solution for this. can anyone help?

---

### Post by Cheesemill on 2012-09-21
I don't think you'll get any help here, discussion of aircrack is against forum policy.

---

### Post by neuronetv on 2012-09-21
that's just great. The only thing I can find on google about this is my own unanswered posts.

---

