---
title: "[SOLVED] Question about sudo"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by SpongeBob SquarePants on 2008-05-13
Evening all,

I'm trying to talk a friend of mine into running Ubuntu (he's currently running Debian), but he has a problem with sudo. Because he has multiple users on his machine, he wants to be the only one that can mess about with system files (for fear of his kids knacking things up). His argument is that sudo seems to allow anyone with a user profile to use their own password to mess around with the system files, and he doesn't want that to happen.

Any suggestions?

---

### Post by Steveway on 2008-05-13
You need to be in the admin group to perform such tasks using sudo.
So he is wrong.
Just don't put them in that group and you should be done.

---

### Post by SpongeBob SquarePants on 2008-05-13
> **Steveway said:**
> You need to be in the admin group to perform such tasks using sudo.
So he is wrong.
Just don't put them in that group and you should be done.

Ah...thanks for the swift reply. So when you add a user do you get the option of choosing which group to put them in? I'm presuming that if you only have one account, you're made admin by default (as I don't remember being asked anything during installation).

EDIT: Is there any way of marking threads solved these days? Or did that feature go with the old software?

---

### Post by SoggyCornflake on 2008-05-13
> **SpongeBob SquarePants said:**
> Evening all,

I'm trying to talk a friend of mine into running Ubuntu (he's currently running Debian), but he has a problem with sudo. Because he has multiple users on his machine, he wants to be the only one that can mess about with system files (for fear of his kids knacking things up). . . .

. . . Any suggestions?

Tell him not to worry.

I believe only the first user has sudo rights as a default.  At least that's what I found when I installed.  On my home computer, I have sudo rights and I added my wife.  My kids don't have it.

This is easily managed with a GUI, but because I'm at work not using my home computer at the moment, I can't tell you which one.

---

### Post by qamelian on 2008-05-13
> **SpongeBob SquarePants said:**
> Ah...thanks for the swift reply. So when you add a user do you get the option of choosing which group to put them in? I'm presuming that if you only have one account, you're made admin by default (as I don't remember being asked anything during installation).

EDIT: Is there any way of marking threads solved these days? Or did that feature go with the old software?
By default, only the user initially created during the installation can use sudo. Any additional users need to be be given explicit permission to sudo.

---

### Post by kellemes on 2008-05-13
The sudo configuration file (/etc/sudoers) is used to setup the security policy.
You can setup sudo with a much more fine-grained security policy than when using the root account.
You can have authentication automatically expire after a specific time, for example.. you can configure it such that sudo will give a user root privileges for 15 minutes, or just 2 minutes.

Using sudo is safer since every cracker trying to get into your system will try to crack the root account first, since Ubuntu has no root account enabled by default, this crack attempt is a waste of time. sudo depends on user accounts, the names of these accounts will normally not be known by crackers.
It's much safer.

---

### Post by SpongeBob SquarePants on 2008-05-13
> **kellemes said:**
> The sudo configuration file (/etc/sudoers) is used to setup the security policy.
You can setup sudo with a much more fine-grained security policy than when using the root account.
You can have authentication automatically expire after a specific time, for example.. you can configure it such that sudo will give a user root privileges for 15 minutes, or just 2 minutes.

Using sudo is safer since every cracker trying to get into your system will try to crack the root account first, since Ubuntu has no root account enabled by default, this crack attempt is a waste of time. sudo depends on user accounts, the names of these accounts will normally not be known by crackers.
It's much safer.

Thanks for the answers everyone. I'll pass on the information anon. He seems to have gotten the wrong end of the stick somewhere. Again, much obliged.

---

