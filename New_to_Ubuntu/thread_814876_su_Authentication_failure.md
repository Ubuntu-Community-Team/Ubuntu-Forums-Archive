---
title: "su Authentication failure"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by Lourie2 on 2008-06-01
I am trying to install an application and have reached a point where I have to enter my password in terminal after su, the response is "su Authentication failure".  Then, obviously it does not allow me to go to the next step of "make install".  Why does 8.04 not accept my password?

---

### Post by wormser on 2008-06-01
Ubuntu uses sudo instead of switching to root.  Put sudo infront of the command then type your password.

More here:  [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by Lourie2 on 2008-06-01
Thanks for the quick response, also for the link.

---

### Post by The Cog on 2008-06-01
Putting sudo in front of the command doesn't always work - e.g. if the command has pipes or redirection (<, | >) in it. It is probably easier to use the command **sudo -i** to get a proper root prompt and do your work from there.

---

### Post by Toz on 2012-11-01
Old thread. Closing.

---

