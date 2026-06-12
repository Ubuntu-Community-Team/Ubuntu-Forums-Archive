---
title: "Unresponsive Password?"
date: 2012-01-23
forum: New to Ubuntu
---

### Post by RadhikaM on 2012-01-23
I've been working in Ubuntu and tried Psychocats' post about resetting your password, but it says I had the same password as before. My login does not require a password, but when I attempt to authenticate something, I type in the same password and it says it's wrong. The button for "change" on the User Accounts password change doesn't light up when I fill in everything either. What do I do? (Reinstallation is my last option, I know, but it's headachey to re-do the settings.)

---

### Post by bodhi.zazen on 2012-01-23
Is your user in the admin group ?

---

### Post by RadhikaM on 2012-01-24
> **bodhi.zazen said:**
> Is your user in the admin group ?

Yes. My account is the administrator.

---

### Post by haqking on 2012-01-24
> **RadhikaM said:**
> I've been working in Ubuntu and tried Psychocats' post about resetting your password, but it says I had the same password as before. My login does not require a password, but when I attempt to authenticate something, I type in the same password and it says it's wrong. The button for "change" on the User Accounts password change doesn't light up when I fill in everything either. What do I do? (Reinstallation is my last option, I know, but it's headachey to re-do the settings.)

you dont have one but then you say you typed in the same one ?

use the recovery console and input a different password than the one it is telling you is the same as before ;-)

and when following that guide, are you resetting your user password (which should be a sudo user) or are you doing the root account (which by default is locked and should remain so) ?

Cheers

---

### Post by RadhikaM on 2012-01-24
> **haqking said:**
> you dont have one but then you say you typed in the same one ?

use the recovery console and input a different password than the one it is telling you is the same as before ;-)

and when following that guide, are you resetting your user password (which should be a sudo user) or are you doing the root account (which by default is locked and should remain so) ?

Cheers

I believe it was the root account. How do you change your user password then, without knowing your user password?

---

### Post by haqking on 2012-01-24
> **RadhikaM said:**
> I believe it was the root account. How do you change your user password then, without knowing your user password?

using pyschocats link that you was following and using

```
passwd username
```

where username is your yourusername

what were you typing then ?

---

