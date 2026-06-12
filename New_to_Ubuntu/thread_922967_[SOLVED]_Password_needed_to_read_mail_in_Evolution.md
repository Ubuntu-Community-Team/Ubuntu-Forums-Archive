---
title: "[SOLVED] Password needed to read mail in Evolution"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by alienexplorers on 2008-09-17
When I use Evolution to read mail it comes up with a message about allowing keyring.  It then asks for a password.  How do I get rid of this so I don't need to put a password in every time to disable the keyring?

---

### Post by crazypenguin2008 on 2008-09-17
this worked in gusty not sure if it works in hardy but here it is 

System->Preferences->Encyption and Keyrings then
highlight the password keyring "login" then click Remove Keyring then reboot

---

### Post by Zzl1xndd on 2008-09-17
Also I've noticed that if your login password is the same as your keyring it wont ask.

---

### Post by alienexplorers on 2008-09-21
Found out I was using Auto Login and thats why it's asking for a password.  Switched back to manual login and evolution does not ask for a password.

---

### Post by fballem on 2008-10-01
There are instructions on how to synchronise your keyring password to your login password at this post: [http://ubuntuforums.org/showthread.php?p=5886460#post5886460](http://ubuntuforums.org/showthread.php?p=5886460#post5886460)

Hope this helps

---

