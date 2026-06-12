---
title: "How to use Seahorse"
date: 2013-06-30
forum: New to Ubuntu
---

### Post by mpellegr on 2013-06-30
I've had Ubuntu for quite awhile but I've never really understood how Seahorse works. Of the three tabs (Passwords, My Personal Keys, and Other Keys) I only have information stored in Passwords. Wifi passwords are in there and were automatically added. They are prepended with 'Auto', does that mean Seahorse is what is supplying my Wifi passwords when the Wifi is in range and automatically connecting me? All the other data is just passwords I've manually added. I usually use Firefox to remember all my passwords for sites that allow it, and for banking sites and such I stored the password in Seahorse. When I need to use it, I click the '+' next to 'Password' to expand it, click 'Show Password', and copy and paste the password into the login form. Is this a typical use case for Seahorse? Also, is it possible to export all these passwords to a thumb drive for safe keeping?

---

### Post by Zill on 2013-06-30
Seahorse is a GNOME application for managing GnuPG encryption keys.  See [GnuPrivacyGuardHowto]("https://help.ubuntu.com/community/GnuPrivacyGuardHowto") for further details.

For storing your personal passwords, such as banking sites etc, I suggest a Password Manager would be more suitable.  A password manager is accessed via a single password and all your passwords will be held securely in an encrypted file.  I recommend [Figaro's Password Manager 2]("http://als.regnet.cz/fpm2/") (FPM2) - it's in the repos.
```
sudo apt-get install fpm2
```

---

### Post by su:bhatta on 2013-06-30
U can check out this techradar page, which lists down a number of password managers...:
[http://www.techradar.com/news/software/applications/8-of-the-best-linux-password-managers-916152](http://www.techradar.com/news/software/applications/8-of-the-best-linux-password-managers-916152)

I will provide u the list of 8 from that page for your ready reference:
> 
**Our selection **
Fiagaro's Password Manager
Gpass
Gpassword Manager
Gringotts
KeePassX
MyPasswords
PasswordSafe
Revelation




Gringotts!!! Now Thats Interesting....:)

---

