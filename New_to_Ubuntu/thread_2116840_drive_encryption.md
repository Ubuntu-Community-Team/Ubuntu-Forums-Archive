---
title: "drive encryption"
date: 2013-02-16
forum: New to Ubuntu
---

### Post by swansonkts on 2013-02-16
how do I shut it off? I chose the option to encrypt the drive when I installed Ubuntu Studio 12.10. Now, any time I need to restart (such as from updates) It takes forever for it to restart. I end up manually shutting off my PC and turning it back on. Then it still takes roughly 2 minutes before I can enter the password. I really don't like this. I thought this would be a good idea, and it probably is, but I don't like it. Is there any way to shut it off with reinstalling the OS?

---

### Post by DuckHook on 2013-02-17
Encrypting your drive is not a process designed to be reversible. Otherwise it would defeat the very reason for encryption's existence (as a security tool that stops bad guys from getting at your data). It is possible to yank out encryption on files and even whole directories, but this is through brute force. Basically, you copy the data to a backup in unencrypted form, delete the encrypted directory, create a replacement clear directory and copy the data back in. Can't do that with an entire HDD because OSes are far more sensitive than simple data. UUIDs, config files and dozens of other dependencies get borked, so your only option is to backup all important data to an external medium and reinstall.

The larger picture:

It's a running joke among friends and family that I'm paranoid when it comes to IT security, but even I would not encrypt my whole drive unless I were being pursued by the Martian Secret Police. Encryption incurs significant computational overhead and if you encrypt your OS (not just your data), then every time your OS needs to access a system file, it must decrypt/encrypt in addition to the read/write process itself. This includes /tmp and any caches held on the HDD. Moreover, you are truly and completely borked if you must ever resort to a LiveCD to recover or reconfigure any part of your OS. And since your password is already well-defended, there isn't much advantage to be gained from whole-disk encryption either.

A better way:

This is why many people choose to encrypt only their /home directory and leave / in the clear. /home is where all of the sensitive data is, so in the vast majority of cases, it is enough to encrypt /home. However, this still creates some issues. The overhead is still severe and often for pointless reasons. After all, why do I have to encrypt my 200GB of games? Moreover, it breaks things like the ability to remotely ssh into your /home prior to yourself having already physically logged in.

The best way:

Therefore, the encryption tools that come with Ubuntu allow you to encrypt any directory you want, but in particular, a special one--the Private directory--normally found just below your own /home/user/. You will need to:```
sudo apt-get install ecryptfs-utils
```Once installed, do:```
man ecryptfs-setup-private
```for instructions. [This]("https://help.ubuntu.com/community/EncryptedPrivateDirectory") is also a good link to read. Once the directory is successfully encrypted, dump all sensitive data into Private. Move your e-mail in and symlink back to the original directory. Move only your private keys into Private while keeping your .ssh directory clear. Now you can remote ssh to login with no problems.

Don't let your current difficulties sour you on encryption. If it's done properly, it can really safeguard and privatize your data. Unfortunately, you can only backup and reinstall at this point if you want to decrypt your HDD, but hopefully the above guide will help you afterwards.

---

### Post by swansonkts on 2013-02-18
Thank you. I appreciate your response. I was afraid i would have to do a reinstall. no big deal I guess since I don't have a lot of files to copy.

Thanks again 
Kevin

---

