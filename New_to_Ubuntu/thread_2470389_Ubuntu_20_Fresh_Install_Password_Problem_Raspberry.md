---
title: "Ubuntu 20 Fresh Install Password Problem Raspberry Pi"
date: 2021-12-28
forum: New to Ubuntu
---

### Post by rorym1 on 2021-12-28
Hi all,

I am new to using linux/ubuntu so my knowledge base is limited. I am installing ubuntu core 20 to my raspberry pi 3b+ using the installer provided on their website. Everything goes alright until I ssh into the device and it prompts me for a password. I leave it blank as that is what everywhere says it should be. "Permission denied, please try again". I have tried other passwords that I have read including root, ubuntu, default, password for ubuntu one, nothing seems to work. I used putty for windows to ssh into the raspberry and a ubuntu VM  terminal. The ubuntu terminal actually prompted me with the ECDSA key  fingerprint and the putty did not. I typed "yes" and that is when it  prompted me for the password.

 I'm thinking it might have to do with my SSH keys but I am not sure. I generated them using putty key gen RSA 4096 as recommended on some thread I read.

Any help would be much appreciated.

Thanks

---

### Post by TheFu on 2021-12-28
I don't know the answer. Sorry.

Ubuntu Core isn't normal Ubuntu. I know nothing about Core, since it is very different and mainly for IoT development companies, not individuals.  I'm fairly sure that the login created to get Core is the one that has to be used.

Putty creates an odd version of keys for ssh. If you use the normal Unix ssh-keygen provided by other platforms, then the keys should just work.  I think Win10 has ssh built in and you can push the ssh-keys from Win10's ssh-keygen to Linux and all will be good. Sadly, Win10 doesn't provide ssh-copy-id like all Unix systems have for the last 20 yrs.

Sorry I'm no help.

I do know that on my non-Ubuntu Core raspberry pi installations, normal ssh works just like normal ssh does on all Unix systems.  I can only suggest that you watch a Youtube video with step-by-step instructions.

Ubuntu Core really isn't meant for people new to Unix/Linux.  It is for experts that want to create an IoT device to deploy around the world.

---

### Post by rorym1 on 2021-12-29
Thanks for your response I will try a different key generator.

---

### Post by TheFu on 2021-12-30
> **rorym1 said:**
> Thanks for your response I will try a different key generator.

That and I honestly hope you use a different distro from Ubuntu Core. The learning curve for it seems pretty steep and the forced tie into Canonical's SSO seems not-so-well thought out to me.

Update: I have an issue with Ubuntu Core mandate to use their infrastructure, snap packages, and SSO to log into a local system.  These are the main reasons why I haven't tried it and will likely never try it. Thought that was worth mentioning, so my near total ignorance is understood.

---

### Post by grahammechanical on 2021-12-30
This is a guess based on very little knowledge and even less experience of Ubuntu core. I think that we need to be connected to the internet because we use our Ubuntu Single Sign On as password and that has to be confirmed by the Ubuntu servers.

[https://ubuntu.com/core/docs/using-ubuntu-core](https://ubuntu.com/core/docs/using-ubuntu-core)

Regards

---

