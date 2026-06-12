---
title: "[SOLVED] Howto RemoveDefault Keyring"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by clive littlewood on 2008-11-05
Hi All

When i boot into the desktop i am stopped from connecting to the network by the "default keyring" 

As i am the only user of the system it is a niggle to key my password in on each login.

Is there a way to disable or remove this keyring feature.

Thanks hopefully

Clive      :p

---

### Post by LowSky on 2008-11-05
Very simple, ANd I keep posting the answer to this...Like the 4 time this week....lol

Go to /home file, hit Ctrl+h to see hidden files, delete the Keyring folder

Now when the defualt keyring prompt comes up just hit enter, do not put any password in the box, and viola it will be the last time you see that prompt

---

### Post by clive littlewood on 2008-11-05
Hi LowSky

Thanks for the quik reply.

It would appear that i do not have a keyring folder hidden or otherwise !!!!

Is it inside another folder ?

Clive         :confused:

---

### Post by LowSky on 2008-11-05
sorry here is the correct path

/home/.gnome2/keyrings/

---

### Post by clive littlewood on 2008-11-05
Hi

Thanks LowSky but when i delete the file and re boot it will then not let me access the network until i confirm a new default keyring ?

Back to square 1 !!!       :confused:

Clive

---

### Post by clive littlewood on 2008-11-05
Hi Lowsky

Solved

I was using auto login and when i changed this to manual login i got the option to use "auto activate default keyring on login"

You certainly live and learn with Ubuntu      :lolflag:

Thanks for your interest and iwill mark as solved

Clive

---

