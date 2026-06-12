---
title: "synaptic gone from sys&gt;admin menu?"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by tparker on 2008-06-14
Somehow 'synaptic', 'hardware drivers', and 'software sources' have been removed from the options to use in the System>Admin menu. They used to be there and worked fine. I am running Hardy and using the default login that was created on install. I have previously used 'hardware drivers' for adding nvidia drivers and 'synaptic' for adding programs, as this login, so I know they were there and worked. 

I tried right clicking on 'System' and choosing 'Edit Menus'. The editing box opens, Synaptic, etc. are listed under Admin but are in italics and unchecked. If I check their boxes the check shows for a second, then goes away. I tested by unchecking and rechecking something else (Time and Date). When it was unchecked it went to italics but switched back to regular font and stayed selected when I rechecked its box but Synaptic and the others will not stay checked.

---

### Post by ibuclaw on 2008-06-14
This sounds like typical behaviour of when you have been removed from the "admins" group.

Can you open up a terminal and type in the command:
```
groups
```
And post the output in your next post.

Regards
Iain

---

### Post by tparker on 2008-06-14
typing groups in terminal gives me:

users admin housenet

---

### Post by ibuclaw on 2008-06-14
:-s
So that is very odd indeed.

To confirm that you're admin group is functional, does this command work?
```
sudo id
```

Regards
Iain

---

### Post by tparker on 2008-06-14
I type in sudo id, give it my password, and get back this:

uid=0(root) gid=0(root) groups=0(root),100(users),115(admin)

---

### Post by dendy7h on 2008-06-15
I had a similar problem, I joined my machine to a domain and am logging in as a domain user.  I fixed the problem by editing the /etc/passwd file and adding my information to that file.  You can get your uid by opening the terminal and typing
```
id
```
you might also want to
```
less /etc/groups
```
and make sure your username is in the following groups
```
your_username(mine is dendy7h) dialout cdrom floppy audio dip video plugdev fuse lpadmin admin
```

HTH,


Dendy

---

### Post by tparker on 2008-06-20
Thank you both for the help. I checked /etc/group and everything looked fine. I ended up using sudo gedit and deleting the admin:115 group from my groups list, rebooting, re-editing the list and putting the admin group back in, and rebooting again. Something in that fixed the problem and I have Synaptic and the other options back in my drop down list now. I really have no clue why they went away or how that process fixed it, but I'm glad it did so.

Thanks again.

---

