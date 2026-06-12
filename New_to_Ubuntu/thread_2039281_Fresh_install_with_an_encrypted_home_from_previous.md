---
title: "Fresh install with an encrypted home from previous install?"
date: 2012-08-08
forum: New to Ubuntu
---

### Post by nickjames1 on 2012-08-08
I'm making a fresh install of the latest ubuntu and I have 11.04 installed. How can I make the install recognize this and adapt accordingly?

I have separate root and home mount points.

I'm using 64bit if that matters.

---

### Post by audiomick on 2012-08-08
If the old /home were not encrypted, it would just be a matter of telling the installer to mount that partition at /home. You have to choose the manual option when the installer gets to the bit where you choose "use the whole disk" or "install beside" or whatever. I think the manual option is called "something else" on the current installer.

I really don't know, though, what difference the encryption makes.

---

### Post by nickjames1 on 2012-08-08
This much I know, I can format manually without wiping the home partition but then what? The partition is still encrypted. The new installation can't possibly decrypt it until I give it password. Even thing, it won't know that I want to use it like you would use an encrypted home partition, decrypt on startup for a particular account and encrypt after.

How do I set that up? Is it automatic?

---

### Post by audiomick on 2012-08-08
I've done a bit of searching, but not found anything conclusive. I have the impression that it may be possible to supply the installer with the password, but I doubt very much that is what you would call automatic.

I don't want to make any suggestions, though. I would be guessing wildly. Wait a bit, hopefully someone will answer who has more of an idea.

---

