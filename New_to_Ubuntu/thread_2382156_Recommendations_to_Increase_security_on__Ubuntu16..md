---
title: "Recommendations to Increase security on  Ubuntu16.04 - first time user."
date: 2018-01-09
forum: New to Ubuntu
---

### Post by Jonesy_sa on 2018-01-09
Hi
First time user. I installed Ubuntu Desktop 16.04 on a spare PC primarily for internet banking and possibly investigating cryptocurrency which requires desktop wallet. My daily PC is W10 and used for everything including torrenting and public wifi so not secure.
I would like to make Ubuntu and a recommended browser as secure as possible while still user-friendly. I watched a few YouTube's and searched google but there was many contradictions.

What software and browser add-ons would you suggest installing?
I currently have a super-user account and I think default guest account. Once set up should I delete the guest option and create a user account seperate from the super-user?
I have a number of very large passwords. Is there software that would allow me to encrypt a single folder which may contain a .txt file of this info? (I would prefer not to use full disk or home folder encryption incase I need to run a live CD to fix issues.
Any advice or link to a trusted guide would be great.

---

### Post by yancek on 2018-01-09
Read the Ubuntu link below on Security which should answer a lot of your questions.

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

You might also read the link below which explains 'sudo' and not having a root/superuser account by default.

[https://help.ubuntu.com/lts/serverguide/user-management.html](https://help.ubuntu.com/lts/serverguide/user-management.html)

The default guest account is re-created on every boot and it is not possible to change or save anything on re-boot.  It is also not possible to access anything (write to) anywhere on the system outside the guest user directory.  It is not possible to gain root/sudo access as a default guest user.

---

### Post by mastablasta on 2018-01-10
plenty of ubuntu hardening websites. most important one - keep security updates up to date.

browser - Firefox or Chromium - use some kind of skript blocker. i use firefox with "no script" added and then manually decide what scripts can and can't run.

even more secure way is to install a linux distro from minimal iso to virtualbox. add some desktop and browser. or better yet install security oriented distro with extra hardening in place (e.g. Tails, backbox...) then save snapshot, do the thing and then restore snapshot.

> **Jonesy_sa said:**
> 
I have a number of very large passwords. Is there software that would allow me to encrypt a single folder which may contain a .txt file of this info? 

a better solution is to use something like keepass2 or keepassx - both are crossplatform and work on windows as well. i use keepass2 and often use it's password generator to create long passwords.

info on difference: [https://superuser.com/questions/878902/whats-the-difference-between-keepass-and-keepassx](https://superuser.com/questions/878902/whats-the-difference-between-keepass-and-keepassx)

other option is to use the built-in gnome keyring (Kubuntu uses KWallet).

---

### Post by Jonesy_sa on 2018-01-15
Thank you for the input. I am new to NoScript and it appears the latest version has re-written the UI completely. Is there an update of the following guide:
[https://wiki.ubuntu.com/BasicSecurity/NoScript](https://wiki.ubuntu.com/BasicSecurity/NoScript)

---

### Post by mastablasta on 2018-01-16
i just have it installed and leave it at defaults. while all settings are helpful they can also make legitimate sites not work. so by default scripts are blocked and then i decide which one is always unblocked.

---

### Post by gordintoronto on 2018-01-16
For folder encryption, SiriKali, if it's available. (I'm on 17.04.)

---

### Post by deadflowr on 2018-01-16
Always set your browser to ask where to save files.
That's my two cents.

---

### Post by sonicwind on 2018-01-17
Jonesy_sa:

See the top of NoScript's website for a list of resources and instructions for the new NoScript version. Also, my understanding is that the new version doesn't currently have the ClearClick and ABE protections, but they are coming as soon as version 10.2.

[https://noscript.net/](https://noscript.net/)

---

### Post by oldrocker99 on 2018-01-17
You probably need to activate ufw (uncomplicated firewall) thus:
```
sudo ufw enable
```

---

