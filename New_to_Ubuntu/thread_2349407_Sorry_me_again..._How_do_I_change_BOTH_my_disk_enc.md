---
title: "Sorry me again... How do I change BOTH my disk encryrption password + login password?"
date: 2017-01-14
forum: New to Ubuntu
---

### Post by chris.2 on 2017-01-14
I've been reading about a lot of different commands that are supposed to either get rid of my password or change it but I haven't found anything that works. I'm trying to change both the full encryption of my new SSD and the login password. If you need more info please let me know how to find it because I'm brand new to Ubuntu and it's a huge learning curve for me. Thanks! :D

OK so of course once I post a question I find an answer... Top right of your screen hit the gear for settings > system settings, user accounts > click on the password and you'll be prompted to switch it.

Now I just need to figure out how to change the encryption password which is what I'm more worried about.

Also, how can I make a US keyboard layout my only layout? UK keeps showing up when I try to punch in my encryption password.

---

### Post by TheFu on 2017-01-14
whole disk encryption is usually managed via **cryptsetup**. There are 8 slots in LUKS so add a new passphrase (use 2FA please) and test everything out. Then you can clear the passphrase in the 1st slot.

To change a password for a userid, open a terminal and type **passwd**. Follow the prompts.  This is how Unix system passwords for userids has been managed since 1971. Works locally or remotely, though most remote connections are through ssh with keys these days so typing a password doesn't really happen all that much anymore.

To learn Ubuntu, there are thousands of youtube videos, more books and even amazon has videos.  There are also manpages built into the system which explain how every command (well, almost every command 99.99% of them) works.  If you want an easy introductions, look for "ubuntu desktop guide" and start reading. Most of the general knowledge stuff won't have encryption.

Be careful changing the keyboard/locale in the middle of changing passwords.  This could make the entries appear different ... since different keyboards assigned different keycodes to the same keys.  I've had this issue with my password manager.

If you used Home Directory Encryption, I don't know what you should do. Not my thing.

---

### Post by chris.2 on 2017-01-14
> **TheFu said:**
> whole disk encryption is usually managed via **cryptsetup**. There are 8 slots in LUKS so add a new passphrase (use 2FA please) and test everything out. Then you can clear the passphrase in the 1st slot.

To change a password for a userid, open a terminal and type **passwd**. Follow the prompts.  This is how Unix system passwords for userids has been managed since 1971.

To learn Ubuntu, there are thousands of youtube videos, more books and even amazon has videos.  There are also manpages built into the system which explain how every command (well, almost every command 99.99% of them) works.  If you want an easy introductions, look for "ubuntu desktop guide" and start reading.

Be careful changing the keyboard/locale in the middle of changing passwords.  This could make the entries appear different ... since different keyboards assigned different keycodes to the same keys.  

If you used Home Directory Encryption, I don't know what you should do.

I did read a lot that there are 8 slots in LUKS, but I have no idea what that means. 

is the passwd command just for my login password? I tried to use my encryption password and got this:

```
chris@Chris-Laptop:~$ passwd
Changing password for chris.
(current) UNIX password: 
passwd: Authentication token manipulation error
passwd: password unchanged
chris@Chris-Laptop:~$ 


```

---

### Post by TheFu on 2017-01-14
logins and encryption are NOT linked when LUKS is used. This is a security feature. It would be foolish to have both set to the same value, IMHO.  I use 2FA for disk encryption.

---

### Post by chris.2 on 2017-01-14
> **TheFu said:**
> logins and encryption are NOT linked when LUKS is used. This is a security feature. It would be foolish to have both set to the same value, IMHO.  I use 2FA for disk encryption.

:confused: What's LUKS? and my passwords aren't the same. I'm not too worried about 2FA, it would be a nice feature but for now I just need to change my encryption password.

---

### Post by TheFu on 2017-01-14
[https://linux.die.net/man/8/cryptsetup](https://linux.die.net/man/8/cryptsetup) - if you plan to run Linux with encryption, you'll want to become familiar with that. It isn't safe for us to make too many assumptions about your specific setup. Whereas you can review that page and follow the instructions to add a new unlock passphrase to 1 of the 8 slots.  

According to my googling, the [Arch guide for LUKS]("https://wiki.archlinux.org/index.php/System_Encryption_with_LUKS") is the best one to follow (and according to the [Ubuntu Community]("https://help.ubuntu.com/community/EncryptedFilesystems") help pages too).

The reason for multiple passphrase slots is so multiple users can have different access keys, including the corporate IT guys.

2FA isn't hard. Yubikey makes relatively cheap devices.  I've had a few yubikeys for a while now and have to admit that I delayed using them for this way too long.  For me, slot 1 is a terribly long, complex, hard to type, lots of special characters, etc, impossible to remember, passphrase. It is only for emergency use and much, much, much, more painful to use than 2FA - 60+ characters.  My 2nd slot is a mix of a long-passphrase and output from a specific yubikey - some before, some after the 2FA info gets entered. Probably 40+ characters in total.  Without the correct yubikey, I'm not getting in. And neither is anyone else. 

Regardless, if you use encryption, please, please, have fantastic backups. When things go badly, complete data loss should be expected.

---

### Post by chris.2 on 2017-01-14
> **TheFu said:**
> [https://linux.die.net/man/8/cryptsetup](https://linux.die.net/man/8/cryptsetup) - if you plan to run Linux with encryption, you'll want to become familiar with that. It isn't safe for us to make too many assumptions about your specific setup. Whereas you can review that page and follow the instructions to add a new unlock passphrase to 1 of the 8 slots.  

According to my googling, the [Arch guide for LUKS]("https://wiki.archlinux.org/index.php/System_Encryption_with_LUKS") is the best one to follow (and according to the [Ubuntu Community]("https://help.ubuntu.com/community/EncryptedFilesystems") help pages too).

The reason for multiple passphrase slots is so multiple users can have different access keys, including the corporate IT guys.

2FA isn't hard. Yubikey makes relatively cheap devices.  I've had a few yubikeys for a while now and have to admit that I delayed using them for this way too long.  For me, slot 1 is a terribly long, complex, hard to type, lots of special characters, etc, impossible to remember, passphrase. It is only for emergency use and much, much, much, more painful to use than 2FA - 60+ characters.  My 2nd slot is a mix of a long-passphrase and output from a specific yubikey - some before, some after the 2FA info gets entered. Probably 40+ characters in total.  Without the correct yubikey, I'm not getting in. And neither is anyone else. 

Regardless, if you use encryption, please, please, have fantastic backups. When things go badly, complete data loss should be expected.

:( I can't understand a thing that's said on that website. Where would you suggest a visual/kinesthetic learner finds this information?

---

