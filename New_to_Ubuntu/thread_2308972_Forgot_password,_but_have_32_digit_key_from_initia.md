---
title: "Forgot password, but have 32 digit key from initial boot please help"
date: 2016-01-06
forum: New to Ubuntu
---

### Post by kendallmcintosh on 2016-01-06
I'm curious if anyone can help me out.  Encryption has me locked out of my system, but I wrote down all of the 32 digits keys that the system gives you at first boot.  Is there anything I can do, or am I screwed?  I have ten keys from different installs, so I know what I  have is one of them, but I don't know which one.  Please advise, thanks.

I have searched, but I feel my question isn't just "I lost my password" because I have the key, but I don't know how to use it in this case.

---

### Post by kendallmcintosh on 2016-01-07
I answered my own question while I wait.  The 32 digit key you get at first boot is the encryption for the home directory.

The message is as follows:
> 
**[COLOR=#212121][FONT=Helvetica Neue]Record your encryption passphrase[/FONT][/COLOR]**

[COLOR=#212121][FONT=Helvetica Neue]To encrypt your home directory or "Private" folder, a strong passphrase has been automatically generated. Usually your directory is unlocked with your user password, but if you ever need to manually recover this directory, you will need this passphrase. Please print or write it down and store it in a safe location. If you click "Run this action now", enter your login password at the "Passphrase" prompt and you can display your randomly generated passphrase. Otherwise, you will need to run "ecryptfs-unwrap-passphrase" from the command line to retrieve and record your generated passphrase.
[/FONT][/COLOR]

Ultimately I'm back to trying passwords on the encryption because I think I may be up against the wall.  Can I brute force it sometime in the next 100 years at least?

---

### Post by sandyd on 2016-01-08
See [https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering_Your_Data_Manually](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering_Your_Data_Manually)

---

