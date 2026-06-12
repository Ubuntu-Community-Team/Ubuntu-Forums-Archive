---
title: "Encryption lost!"
date: 2012-09-11
forum: New to Ubuntu
---

### Post by capribex on 2012-09-11
Help!!! Upgraded to 12.04, made some changes to the power settings, and computer stopped asking me for password of the encrypted Home folder. How do I reinstate encryption? I can't find any simple instruction anywhere. Neither do I understand how come encryption just cancelled itself. Thanks!

---

### Post by orange2k on 2012-09-11
Logout and try logging in as guest. If you can't access your home folder, then it's still encrypted...

---

### Post by capribex on 2012-09-11
Thanks Orange... 
When I log in as Guest - it doesn't show the hidden directory (.Private); If that's what you meant. But when I log in as User, it asks me for the log-in password but not for the encryption folder password and yet it DOES give me access to it! 
Straight after upgrading to 12.04 it did ask and it did work properly. Somehow, after I played with the power or hybernation settings, I seem to have lost the encryption. That is, I am no longer asked to supply the password and yet if I am logged in, I get full access.... 

What has gone wrong? How do I fix it? 

Thanks!

---

### Post by mips on 2012-09-11
Maybe there is something in here that can help [http://ubuntuforums.org/showthread.php?t=1975000](http://ubuntuforums.org/showthread.php?t=1975000)

---

### Post by capribex on 2012-09-11
Thanks Mips.... 

Sadly it doesn't solve my problem. It doesn't explain how to re-instate the encryption. Especially, I don't understand how it used to work, then stopped by itself, and still seems to be protected when I try to log in as guest - but opens freely when logged in as user, even though it asks not for the passphrase of the encypted directory.... 

If anyone understands the problem.... Please.

---

### Post by capribex on 2012-09-11
Or at least can you advise me how to report a new bug as this one seem to not be documented....

---

### Post by capribex on 2012-09-11
No Ubuntu Gurus on shift today???

---

### Post by orange2k on 2012-09-11
Your encryption hasn't been lost. Only you with the login password have acces to the home folder. Without the knowledge of the login password you can't access it...

If you are talking about the password that was used to encrypt the home folder, you have been asked to write it down when you installed Ubuntu. It is a long password and it is only used if you somehow corrupted your system and later want to recover your home folder. You will still need your login password and the long password you wrote down...

---

