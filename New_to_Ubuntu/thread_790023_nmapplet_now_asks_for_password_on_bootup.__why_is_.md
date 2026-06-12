---
title: "nmapplet now asks for password on bootup.  why is it doing it?"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by Rukaru on 2008-05-11
It's really annoying.  i think they actually called it keychain or something.  Anyway, it actually needs my old account password.  I tried entering my new one (I changed it) and that didn't work.  Why is it doing this?

---

### Post by sdennie on 2008-05-11
Is it asking for it at bootup or after resume from suspend/hibernate?

---

### Post by Aearenda on 2008-05-11
I think it is because the keyring password needs to be changed too, to match. See system->preferences->Encryption and Keyrings, click on the 'login' keyring, and make the same change. I hope that will sort it out for you.

BTW: This is the unlock for your secure password cache, where the network passphrases are kept. It is automatically unlocked by the authentication system if the login and unlock passwords match.

---

