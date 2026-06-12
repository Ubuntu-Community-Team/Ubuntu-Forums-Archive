---
title: "[SOLVED] Home directory and multiple users same programs."
date: 2008-11-02
forum: New to Ubuntu
---

### Post by Kellemora on 2008-11-02
Hi Gang

I should have this down pat by now, but still messing up somewhere.

I'm picking up another new computer that will be solely Ubuntu 8.04

I'm already putting Home in it's own partition, usr and var to simplify backups.

The Normal set-up is /home/userA, with all the other users under the same /home directory, but as /userB, /userC, etc.

Here is the problem, /userB decides they like a particular program, I download it for them since they don't have administrative rights.
Then /userC says they want it too!
I have to download the program for /userC in their file.

NOW I have two copies of the same program using up HD space.

When I go to set up the new computer, can I do this?????

/home/allusers/userA  then of course the SAME /home/allusers/directory would contain /userB /userC etc.
THEN when someone wants a program, the user named allusers (me as administrator) can load the program under /allusers
If I do that will the programs then be available to /userA, userB and userC or is their a better an easier way.

On another computer in the /usr folder, I made a new folder named Programs and that works also, but I prefer to do that for system wide programs that should be available on ALL Machines.
I'm thinking of programs ONLY used by certain employees.
I'm not making sense am I?

TTUL
Gary

---

### Post by taurus on 2008-11-02
Why not just install the programs in /usr/local/bin so everyone who wants to use them can just run them without modifying anything.

---

