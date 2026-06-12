---
title: "Can't login anymore"
date: 2013-08-10
forum: New to Ubuntu
---

### Post by macstl on 2013-08-10
My first user created with admin rights won't login anymore. my second user created standard user does login in. I tried as user 2 to set user 1 with no password but it does not work but keeps going backto pw login screen. My user1 password works when I give admin privilege to unlock user and group gui as user 2.  I am using 12.04 desktop . Have I been locked out by a hacker? If my pw was changed by someone why would pw work on unlocking user and group gui?
Right now I am stuck using user 2 standard user with out my desktop settings and programs loaded. bummer.
any help would be greatly appreciated!

---

### Post by steeldriver on 2013-08-10
It sounds like there is nothing wrong with your password - however your user #1 X session is unable to start

Try switching to your user #1 account from user #2 by opening a terminal (Ctrl-Alt-t) and issuing the following command

```
su - *user1*
```

where user1 is your first (admin) user's login name. If that works (accepts your original password) then check the ownership and permissions on the home directory and associated files

```
ls -ld ~/
```
and
```
ls -l ~/.{ICE,X}authority
```

and report back the results

---

### Post by macstl on 2013-08-10
when I do su - user1
and type in password I get authentication error..

---

### Post by macstl on 2013-08-11
I seem to have gotten myself into a black hole so I reloaded Ubuntu 12.04.
It was my own fault. I was messing aroound with some commands related to x term while reading ubuntu unleashed.

I don't know how to mark this as solved. I don't see anytlhing here for it. Can someone tell me about that. I see solved selectiion when I first created the thread but not on a reply.

---

### Post by Bashing-om on 2013-08-11
macstl; Hi !

(re-)installing is often the quicker way to reach resolution ... I have done so several times .. has taught me to keep good backups !
As to marking a thread "solved"
Thread Tools drop-down -> Mark thread as solved. - Might have to be done from your first post (??).

[INDENT][INDENT]happy trails to you ->
[/INDENT][/INDENT]

---

### Post by philinux on 2013-08-11
Imho. Reinstalling is usually the last resort. Most things can usually be sorted without resorting to that.

---

