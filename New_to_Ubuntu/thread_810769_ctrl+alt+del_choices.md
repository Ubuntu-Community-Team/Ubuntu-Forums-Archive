---
title: "ctrl+alt+del choices"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by Zopiac on 2008-05-28
on the live disk when you press the combo it brings up a box with options to do various things, including restart and shut down. when i do that in the installed copy, it does not show those two options, only: logout, lock screen, switch user, and hibernate.

---

### Post by sayakb on 2008-05-28
That's strange, it brings up the same dialog for me that I get after selecting Quit from panel/menu. Can you post a screenshot?

---

### Post by decoherence on 2008-05-28
Under System -> Administration -> Users and Groups, click your name a select Properties. Select the User Privileges tab and make sure "Administer the system" is checked.

don't know for sure if that'll fix it but worth a shot. Shutting the system down is considered an administrative task (comes from being a predominantly server-oriented system)

---

### Post by chrisccoulson on 2008-05-28
Shutting down the system is not an administrative task when logged in locally from GDM. All options are available regardless of whether the user is an administrator or not.

Do you know if you're using xserver-xgl?

---

### Post by sayakb on 2008-05-28
> **decoherence said:**
> Under System -> Administration -> Users and Groups, click your name a select Properties. Select the User Privileges tab and make sure "Administer the system" is checked.

don't know for sure if that'll fix it but worth a shot. Shutting the system down is considered an administrative task (comes from being a predominantly server-oriented system)
Yes, but I do get it on the limited account I've made for my roommate..

---

### Post by Zopiac on 2008-05-28
screenshot? i cant seem to take one when i press ctrlaltdel, at least w/ printscreen button

---

