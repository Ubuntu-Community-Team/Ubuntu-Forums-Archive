---
title: "grub-mkpasswd-pbkdf2 ; a misunderstanding."
date: 2012-06-12
forum: New to Ubuntu
---

### Post by 00oddn4a on 2012-06-12
Hello to all!
If i create a password derivated from a function for the grub2 bootloader with the command grub-mkpasswd-pbkdf2
and i type for example: 
```
sleax@sleax-laptop:~$ grub-mkpasswd-pbkdf2 -c 2000 -l 100 -s 10
Enter password:  (linux)
Reenter password: (linux)
Your PBKDF2 is grub.pbkdf2.sha512.2000.01FEF59C3660E0297A23.B9CC6FB0EE8D02CF1995A2FD45EC7E6A5E04E2C11247514E101EA2F0EF48C8763488E48D8660C987867A0DE6A6694CD5F03250D4F1345B5337DC2204FDDF47FABB2AA4B1898597833E635369BC443DF7073B60722E642A95C892F6DFCFE3EB62427C0944

```well, now i would to say how the system can reverse the code, i.e. how can (after edited grub configs) the system go back to "linux" from that derivated key?
Maybe my question is stupid, but i'm curious!:confused:

---

### Post by 00oddn4a on 2012-06-13
Noone can tell me this?:(

---

### Post by twipley on 2012-10-26
It never goes that way, and it does not get to know the password, never.

What it does is check that the hash of the inputted password *matches* the stored Grub-config hash.

---

### Post by twipley on 2012-10-27
After thinking about it a little bit: not sure anymore, as there seems to be random salt added to the hashing process.

---

