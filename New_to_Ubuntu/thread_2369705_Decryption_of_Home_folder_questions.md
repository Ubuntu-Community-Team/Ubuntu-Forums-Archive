---
title: "Decryption of Home folder questions"
date: 2017-08-26
forum: New to Ubuntu
---

### Post by webmiester on 2017-08-26
Hi everyone,

I have been installing several Ubuntu machines lately (over 20 already in the past month).  The setup always asks me if I want to encrypt the home directory, which I do so.  I am just curious because never did the system ever ask me to produce an encryption key.  In case, if my system goes down and I want to recover the files using a different computer, what encryption method do I use (what software too), and what would be the password?  Would the password be the same as the initial root password?  If the root password was changed over time, would the encryption password change too?  Or perhaps this method doesnt need a password.

I found this article through another thread in our forums: [www.linux-mag.com/id/7568/](www.linux-mag.com/id/7568/)

The article is really nice, but I noted that the eCryptfs provided a passkey to the user.  The ubuntu installation setup encryption doesn't.   Also, since this article was written for Ubuntu 8.10, I am not sure if it is still the default encryption used by the latest 16.04 and 17 versions.  Thank you so much.

---

### Post by HermanAB on 2017-08-26
AFAIK Ubuntu uses LUKS with AES256 by default, same as other Linux distros.  So provided that you don't forget your password, you can recover the data with another system.

You can add additional passwords, or change the passwords quite easily.  Read the cryptsetup man page for details.

The more of the disk you encrypt, the better.  Encrypting only the home parition is better than nothing, but unencrypted data will leak into /tmp and /swap for example.  Therefore, so called 'whole disk' encryption is better (/boot always has to be plain text in order to start up).

---

### Post by deadflowr on 2017-08-26
When you create the home folder with encryption is does create a passphrase for it, that is then synced to the user's main password, so the system is unlocked at login.
Upon first boot after the install it should give you a pop window to show how to find the passphrase, like here:
[https://askubuntu.com/questions/293446/how-to-retrive-encryption-passpharase]("https://askubuntu.com/questions/293446/how-to-retrive-encryption-passpharase")

---

### Post by webmiester on 2017-08-27
Oh Thank you so much!  yeah, I kinda remember seeing a window like that but I didnt figure out what it was.  Alright, Ill try it out!
Re: whole disk encryption: will this slow down my system?  Thanks

---

