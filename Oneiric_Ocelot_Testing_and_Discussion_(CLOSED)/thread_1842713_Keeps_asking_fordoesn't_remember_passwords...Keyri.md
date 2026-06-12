---
title: "Keeps asking for/doesn't remember passwords...Keyring problem?"
date: 2011-09-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ClyN3il on 2011-09-12
It doesn't remember and repeatedly asks me for passwords, both for empathy and for my wireless network key. It appears to save the passwords, but after some period of time will apparently lose them and as me to enter them again. I'm only asked for my keyring password once, after log in. I'll try deleting the keyring file in ~/.gnome2 and then not entering a keyring password, but even if that works, wouldn't that be less secure and isn't there a better way?

---

### Post by ClyN3il on 2011-09-20
So my Google search turned up my own post. Great.

PS: Deleting ~/.gnome2 was of no help at all.

---

### Post by Paddy Landau on 2011-09-20
Are you using auto-login?

If you use auto-login, then the keyring does not have access to your password and needs to ask. For that reason, even if your computer is physically secure, it's a good idea to use normal login where you type your password.

---

### Post by ClyN3il on 2011-09-20
You mean have it log me in without asking for a password? No, I'm not using auto-login.

---

### Post by ClyN3il on 2011-09-20
This just started after upgrading to Oneiric (Beta).

It doesn't ask me for empathy passwords every time, but I get the pop-up that says the connection is untrusted, but even though I check the box that says "remember this choice for next time" they keep coming back.

It asks me for my wireless network key after log in, and something like every 5 minutes after that.

---

### Post by cariboo on 2011-09-20
Do you have more than one entry in Passwords & Encryption Keys? See the screenshot.

---

### Post by PuddingKnife on 2011-09-20
Im having this same issue Cly...

It randomly asks for my wifi password while I'm on the internet. Usually afterward, it will then ask for my keyring password.

---

### Post by CaptainMark on 2011-09-20
> **ClyN3il said:**
> This just started after upgrading to Oneiric (Beta).

It doesn't ask me for empathy passwords every time, but I get the pop-up that says the connection is untrusted, but even though I check the box that says "remember this choice for next time" they keep coming back.

This bug has been kicking around for what seems like forever, it was in the 11.04 dev cycle and it never got fixed but just suppressed for the main release of natty,

---

### Post by smallblackanimal on 2011-09-30
For the wireless key try system settings -> network -> wireless -> configure -> wireless security.  See if the password field is blank, if so enter your password for your AP. I had a similar problem where every time I brought my netbook back from suspend or after rebooting it requested the password, this seemed to fix it.

---

