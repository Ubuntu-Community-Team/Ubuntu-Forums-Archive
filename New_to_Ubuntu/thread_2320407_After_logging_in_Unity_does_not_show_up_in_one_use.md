---
title: "After logging in Unity does not show up in one user account"
date: 2016-04-13
forum: New to Ubuntu
---

### Post by zurga on 2016-04-13
Ubuntu 14.04.4
I can log in to Guest account and everything works normally.
If I log in to the main user account, the password is accepted, but I only get a default background wall paper, and no Unity. I can log in using the tty shell, and everything seems fine, except of course there will be no unity.

I have searched for similar posts, and have found many, but I believe my case is unique in that logging into Guest if fine, with the problem arising only if I log into the main user account. As far as I am aware, this problem has not arisen as a consequence of updating, or setting up and customising user interface. Any help please.

---

### Post by zurga on 2016-04-16
After 3 days, there is no response, so it had to be a case of DIY. The  fact that the problem arises with one user account and not the other,  suggests that there is no problem with the drivers, the unity, or the  desktop packages, rather it is to do specifically with the account, and  that points to a possible corruption of a config file, though I cannot  read and interpret these files to pinpoint the problem. So, crudely, I  removed all of them by:
```
         $ mv ~/.config ~/.config.bkup ## strictly rename rather than remove so it can be used if necessary
```
Then rebooted the system, and all was fine. The config files re-established themselves to their default state.

---

