---
title: "tinkering with the CLI"
date: 2014-03-04
forum: New to Ubuntu
---

### Post by koydl on 2014-03-04
Folks!

I had the weird idea to encrypt (symetric) "ls" with gpg in order to prevent others to see any results that ls usually provides. The encryption worked very well (btw. I did make an extra-folder 'ls-backup', copied original ls there, just to be safe), tried to decrypt it with gpg ls.gpg. The passphrase was correct, and the system tells me, that ls had been rewritten. But - surprise, surprise - I now always get a 'permission denied' altough I am root!

Can somebody help me out here?

Regards..

ps: init 6 doesn't work properly anymore. GUI=ok, but no menus!

---

### Post by Impavidus on 2014-03-04
A weird idea indeed.

You may have to restore execute permission with chmod: **sudo chmod 755 /bin/ls**

---

### Post by whitesmith on 2014-03-04
> **koydl said:**
> Folks!

I had the weird idea to encrypt (symetric) "ls" with gpg in order to prevent others to see any results that ls usually provides.Few would agree that encrypting built-ins is a pregnant idea. If you want to deny others permission to read certain files, just do this```
cd ~/SecretDirectory
chmod 740 *
```. This will give the owner (you) maximum permissions; the owner's group just read; and others no access at all. It's easier and doesn't bork other things.

---

