---
title: "Struggeling with users and passwords."
date: 2020-01-14
forum: New to Ubuntu
---

### Post by sigurdsk on 2020-01-14
Hi!
I have made a couple of accounts for local users.
The one i am in now has all the stuff i need like, documents, apps, settings etc. 
I am lucky to be logged into the account now, but I forgot the password.
Is there any way to change the password without having to reenter an old password since i have tried like 30 passwords
And i dont know which one works? 

Cannot work when the system is like this.. 

Thanks!

---

### Post by CatKiller on 2020-01-14
If one of the accounts you remember the password for has sudo privileges it's pretty straightforward. Otherwise it's a bit more fiddly.

In the first case you'd log in with your sudo-able user and run ```
sudo passwd <user_name>
``` where  <user_name> is the name of the user whose password you need to set.

In the second case you need to invoke the Grub menu and boot into recovery mode, which will give you a shell already using root. Then you can run ```
passwd <user_name>
```

And then try not to forget your password in the future.

---

### Post by TheFu on 2020-01-14
usernames and passwords for direct, physical, logins is just something you have to deal with.  However, for network-based ssh logins, you can setup ssh-keys which will be used for authentication and you'll never be prompted for a password over those connections, except the password to unlock the ssh-key.

You can setup a physical device to provide authentication too - smartcards or yubikeys with challenge-response for authentication.

I used to work at a job where I had to physically manage logins and passwords for about 15 accounts.  It was a federal offense to have either written down. Each system had slightly different password change requirements, but the shortest was every 28 days, so every 28 days, I'd waste 4 hrs walking around the site, changing all the passwords.  None of the systems were on the same network.  Since I wasn't allowed to write anything down, I had used a method of shifting more secure system passwords to less secure systems every 28 days.  To access most of the systems, I had to get passed physical securty checks too.  For the sake of security, sometimes we just have to do what we have to do.

In a business or home setup, where you won't be arrested for violating policy, I'd use a password manager like keepassxc and I'd write down part of the password for each systems+userid, but never write down the entire password. Always have at least 10 characters in your head with needs to be appended or prepended to create the real password.

---

