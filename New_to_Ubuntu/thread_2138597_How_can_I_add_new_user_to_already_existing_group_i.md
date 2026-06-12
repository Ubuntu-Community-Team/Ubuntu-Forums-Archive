---
title: "How can I add new user to already existing group in console mode ?[Solved]"
date: 2013-04-24
forum: New to Ubuntu
---

### Post by Azano on 2013-04-24
Hi!
Like in the title, I want to add a user to already existing group.
In fact it´s seems that i already did this because i used a command "adduser --ingroup groupA user2” and when I look to the passwd i see that "user2(this is the user that i want to add)" is assignated to the groupA.
But the problem appear when i want to log in to the user2, because when I type the password, Linux don´t do nothing. I think that is some problem with permition, and i tried to change the owner of the document groupA(with chown) but it doesn´t gave me any any results, so here is my question:
Do i do something wrong or i need to use other command?

I hope i explained this well and i hope you can help me guys.

P.S.
Sorry for my english.

---

### Post by deadflowr on 2013-04-24
I just run
```
sudo adduser username groupname
```

Look here for more
```
man adduser
```

---

### Post by Lars Noodén on 2013-04-24
chown and many other system utilities won't say anything when they run correctly.  It is expected that they just work and not say anything unless there was an error.  Can you verify that you changed the group of the document using **ls -hl**?  

If both the user and the group already exist, you can add the user to the group with [gpasswd](http://manpages.ubuntu.com/manpages/quantal/en/man1/gpasswd.1.html)

```

sudo gpasswd --user user2 groupa

```

The membership in the new group won't take effect until that user logs out and then logs back in again.

---

### Post by clearski on 2013-04-24
Assuming that the group and username are already created, I do it with:

```
sudo usermod -aG <groupname> <username>
```

then I check with

```
cat /etc/group | grep <groupname>
```

I usually find the <username> as a part of the <groupname> in the /etc/group :)

---

### Post by Azano on 2013-04-26
Problem solved, i used the option from @deadflowr. Thanks guys.

---

