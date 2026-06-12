---
title: "How to turn off ecryption login?"
date: 2013-12-22
forum: New to Ubuntu
---

### Post by bhansmn on 2013-12-22
I am an absolute noob and need some help. I installed Ubuntu 13.10 onto my computer and I checked a box during install that had something to do with encryption. Now every time the computer turns on it is password protected. Is there a way to turn this off?

---

### Post by Iowan on 2013-12-22
I know there is an option to encrypt a directory, but the password is probably the standard login password. If you are really, really sure that you don't want a password, there should be an option under System Settings>User Accounts to automatically log in. That same page has password-change options. I've never used it - I prefer a bit more security on my machines.

---

### Post by sandyd on 2013-12-22
> **bhansmn said:**
> I am an absolute noob and need some help. I installed Ubuntu 13.10 onto my computer and I checked a box during install that had something to do with encryption. Now every time the computer turns on it is password protected. Is there a way to turn this off?

If you receive that message at boot time (at the purple ubuntu screen), it cannot be turned off because your entire Ubuntu installation is on an encrypted partition. The best way to get rid of it is to backup any data that you want to keep, and reinstall.

You can try removing the password by creating an identical partition, and copying your Ubuntu installation to it, but if you are just starting, reinstalling may be easier.

---

### Post by bhansmn on 2013-12-22
Thank you for the help. I just loaded Ubuntu onto the computer so there is really nothing I would lose by re-installing Ubuntu. I think I will do this.

---

