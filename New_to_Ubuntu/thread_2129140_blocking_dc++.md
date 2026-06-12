---
title: "blocking dc++"
date: 2013-03-25
forum: New to Ubuntu
---

### Post by 3v3rgr33n on 2013-03-25
Schools normally block dc++ clients from a computer. I was wondering how I can do that for my home computer?

Firefox has an add-on called:
**BlockSite**

It's for blocking url's. It's password protected. I'm looking for something similar but with applications. The computer has three users and they all know the root password. How can get like a 'password protected firewall app' if it exists. The password should be different from the
root password.

---

### Post by r.stiltskin on 2013-03-31
Configure your firewall (ufw)  [https://help.ubuntu.com/12.04/serverguide/firewall.html]("https://help.ubuntu.com/12.04/serverguide/firewall.html") to block all ports except the specific ones you want to allow.

That's easy, but the problem is that anyone with the root password can thwart it by changing the rules or even simply shutting down the firewall.  Why do all of your users have the root password?  I would think that the first thing you should do is change the root password & set up another user account (or accounts) for the other users, and you can give each of them whichever privileges are appropriate.

---

