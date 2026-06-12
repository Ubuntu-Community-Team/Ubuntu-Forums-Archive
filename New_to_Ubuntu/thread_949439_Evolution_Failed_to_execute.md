---
title: "Evolution Failed to execute"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by johnruben on 2008-10-16
Please Help with this error.
Failed to execute child process "evolution" (No such file or directory)
I'm on 8.10 which did all the updates etc. Everything was going well.
ATI tried to update, this froze and after that there was no evolution. Even the icon in the top panel disappeared.
In synaptic it still indicates green as if it is there.

Thanks, John

---

### Post by celticbhoy on 2008-10-16
first step i would take is to re-install through synaptic

---

### Post by johnruben on 2008-10-16
Thanks, how do I back up all my emails & contacts etc?
J

---

### Post by johnruben on 2008-10-16
I've uninstalled and am batteling to reinstall, via synaptic and sudo apt-get install evolution.
I get this evolution:
  Depends: evolution-common (=2.24.0-0ubuntu2) but 2.24.0-0ubuntu3 is to be installed
 Recommends: evolution-plugins but it is not going to be installed

Any suggestions?

---

### Post by johnruben on 2008-10-16
Solved
I killed evrything and anything to do with evolution, then installed via sudo apt-get install evolution, then when I started evolution it wanted a my password and it found all my emails and contacts.

I ask myself though, was all that really neccessary???

---

### Post by JDuc on 2008-12-25
extreme newbie to Ubuntu here (Linux in general).

I was trying to install the software to sync my WM6.1 phone with Evolution when I found that Evolution gave me this same error.

I've tried reinstalling via the package manager, but it didn't work.

When you say you killed anything and everything having to do with evolution, do you mean that you uninstalled everything related to it via the package manager?

Thanks for any information.

---

