---
title: "Default Keyring Problems"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by Jack Bonner on 2008-09-12
Like many people I have Ubuntu installed on a wireless capable laptop, and entering the password to get the wireless to connect every time I boot up is getting tedious. I went looking around for a solution and found that by installing libpam-keyring (or libpam-gnome-keyring) seeing as I can't find the former, helps do that. I was following this tutorial: [http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/]("http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/") and I have done everything to the letter, yet it still asks me for my password to unlock the keyring when I want to connect to my wireless network. 

Any suggestions?

---

### Post by freak42 on 2008-09-12
that stuff didn't help me either..

what helped is to have a no-letter password (or no password at all, if you can manage that risk):
system->prefs-> password and ecnryption settings
choose your password keyring and press change unlock password. then leave the new password fields blank.

hth

---

### Post by Jack Bonner on 2008-09-12
> **freak42 said:**
> that stuff didn't help me either..

what helped is to have a no-letter password (or no password at all, if you can manage that risk):
system->prefs-> password and ecnryption settings
choose your password keyring and press change unlock password. then leave the new password fields blank.

hth

It might be an idea seeing as i'm the only user of this laptop. Thanks, I'll keep that in mind for if I can't find any other solution to it

---

