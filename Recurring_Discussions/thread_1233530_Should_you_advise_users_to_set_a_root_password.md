---
title: "Should you advise users to set a root password?"
date: 2009-08-06
forum: Recurring Discussions
---

### Post by bhaverkamp on 2009-08-06
For those times where you absolutly need root it can be enabled by setting the root password via



This is good to have when you screw up the sudoers file and need another account.

---

### Post by aysiu on 2009-08-06
> **bhaverkamp said:**
> For those times where you absolutly need root it can be enabled by setting the root password via

sudo passwd root

This is good to have when you screw up the sudoers file and need another account. Actually, it's completely unnecessary.

If you screw up the sudoers file, you can boot into recovery mode to fix it.

---

### Post by slakkie on 2009-08-06
> **aysiu said:**
> Actually, it's completely unnecessary.

If you screw up the sudoers file, you can boot into recovery mode to fix it.


It is not unnecessary, IMHO. Changing your hostname on Ubuntu can cause you not to run sudo anymore, rebooting to solve such minor tasks is unnecessary.

---

### Post by aysiu on 2009-08-06
> **slakkie said:**
> It is not unnecessary, IMHO. Changing your hostname on Ubuntu can cause you not to run sudo anymore, rebooting to solve such minor tasks is unnecessary.
Fixing a ruined sudo is not a minor task.

Rebooting is perfectly warranted in such a case.

---

### Post by slakkie on 2009-08-06
Not in my book.

---

### Post by aysiu on 2009-08-06
> **slakkie said:**
> Not in my book.
You can do whatever you want in your book and on your own computer.

For consistency and because this is the official Ubuntu Forums, we will always recommend staying with the way Ubuntu is designed to work, especially for new users, and that is with *sudo* and without a root login enabled. This helps new users to use the majority of tutorials available.

If other users, who are not seeking advice and who know enough to use other approaches without having to ask here how to do it, want to enable a root account and use that instead, they have the freedom to do so.

For more details, read [Forum policy on log-in-as-root tutorials](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by slakkie on 2009-08-06
I know the policy from the UF, although I do not agree with it.

I don't think it is wrong to have a root password defined. I don't mind that the default install doesn't have an active root account, but I do mind that something like this cannot be discussed on the forums or advised to users.

---

### Post by bodhi.zazen on 2009-08-07
Thread closed.

When necessary setting a root password is supported.

On your own computer you are more then welcome to do as you please.

These forums, however, are moderated and we have a large number of new users. The philosophy behind the forums policy is to teach new users how to use their systems. This includes basic information of things such as permissions and how to use and configure sudo.

What we object to is when people instruct new users to simply use "gksu nautilus" rather then explaining permissions.

We object even more if you start running X (Gnome, KDE, firefox, etc) as root.

While it is true there are times when setting a root password is necessary, setting a root password also opens Ubuntu systems to security vulnerabilities. For example ssh (servers) by default allow root logins via a password. Now there is absolutely nothing wrong with that as by default the root account is locked. If however you set a root password , and are running a ssh server, you just opened a big security hole.

There are additional downsides of setting a root password.

I almost never see people listing all the downsides or security implications of setting a root password when, as the OP of this thread so nicely demonstrates, they post "sudo passwd" . Posting such commands without any explanation of the risks associated or alternate methods is simply irresponsible of the OP.

So if you wish to advise setting a root password, be sure to include all the risks of doing so and explain how to lock the root account when you are through. Also be sure to include basic instructions on Linux permissions and (as is the case 99.99 % of the time) include an explanation of how to perform system administration with sudo.

If you want a root shell, so you do ont need to keep typing sudo before each command, use :

```
sudo -i
```

---

