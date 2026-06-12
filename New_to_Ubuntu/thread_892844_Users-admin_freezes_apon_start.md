---
title: "Users-admin freezes apon start"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by wowfunhappy on 2008-08-17
Okay, I did something REALLY stupid. I was trying to create an account for my younger sibling, a four-year-old. He knows how to spell his name, but he doesn't know how to spell any other six-letter words...

This left me with a problem: I wanted my brother to be able to log on to his account without my help, but that was impossible, since password's have to be at least six characters in length.

A quick search on google brought me to [THIS]("http://ubuntuforums.org/showthread.php?t=551675") thread.

> Aha -- I figured out one way to answer my own question.

   1. Use sudo -i to become root.
   2. Run adduser. New user accounts created by root do not enforce new-password strength requirements.
   3. Click System > Administration > User and Groups, then configure the newly created account's group settings, etc.

Ta da!

Cheers & hope this helps,
Ric

So I followed the instructions. Steps 1 and 2 went well, but the problem was that I had to create my brother's account using the terminal, which is a lot harder than using a GUI. It went fine at first, but when it asked me for a "room ID" or something like that, I relized that I was in over my head.

So... forgetting my common sense as well as *all*the things I've read about how it's dangerous to do things as the root user, I exited out of the terminal before completing the creation of my brother's account.

***_BIG MISTAKE!_*** After exiting out of terminal, I went and started the graphical tool for creating new users, "Users-admin". The program freezes immediately after I start it, and I have to end the process manually using the system monitor.



Running the following command at the terminal hints at what may be causing the problem. In case it helps:

```
$ sudo users-admin

** (users-admin:29905): CRITICAL **: Unable to lookup session information for process '29905'

```


So, can anyone help me?

---

### Post by t0p on 2008-08-17
A guess... **adduser** is still running, so you can't run **users-admin** which uses the same stuff.  So you'll have to kill adduser.  Because you ran it as root, you'll need to do
```
sudo pkill adduser
```

---

### Post by daveysan on 2008-12-05
I have just come across a similar problem. It looks like to solve this you need to revert back to the command line. I was able to add a user using the following commands:

sudo addgroup fred
sudo adduser --ingroup fred fred

This should prompt you for password and a couple of basic user fields. Hope it works for you ...

---

