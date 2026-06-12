---
title: "login without password ?"
date: 2013-04-19
forum: New to Ubuntu
---

### Post by goof on 2013-04-19
hi i have ubuntu 12.04 installed and encrypted my home folder and require a passord to login but i want to login without a password but cant find how to the option in user groups settings aint there is there a way to do this? thanks

---

### Post by arpanaut on 2013-04-19
What's the point of encrypting your home folder if you do not log on with a password?
Seems to defeat the purpose of encryption?????

---

### Post by goof on 2013-04-19
> **arpanaut said:**
> What's the point of encrypting your home folder if you do not log on with a password?
Seems to defeat the purpose of encryption?????

weel it was my laptopbuild but turning it to media center and remote desktop cant connect till after login so am looking for a way to cainge this witout rebuild

---

### Post by DuckHook on 2013-04-19
Not only does it defeat the purpose, it is not, to my knowledge, even possible. Encryption is tied into the Linux authentication module at such a fundamental level that it is not possible to decrypt the partition without physically typing in the password.

I am almost invariably opposed to nerfing Linux authentication, but the one area where this makes at least some sense is a media centre application where nothing else is run on the system. You will be exposed to malware and baddies, but you undoubtedly know this already and are willing to accept the risks.

You have no choice but to back up your /home directory, disable encryption and then restore your /home data. Detailed instructions are [here]("http://virtually-a-machine.blogspot.ca/2010/08/howto-disable-ecryptfs.html").

---

