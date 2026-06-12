---
title: "Passphrase"
date: 2019-12-05
forum: New to Ubuntu
---

### Post by antee on 2019-12-05
Hello,

If you want to recover encrypted home directory you need passphrase.
And it was easy to retrieve. Here is explanation:
[www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/]("http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/")

Ubuntu 19.10 doesn't offer to encrypt home directory during installation but you can setup password for logging into your user account.
What i don't know is if you have this password do you have encryption and passphrase.
If passphrase has been generated, how to retrieve it latter.

Thank you
antee

---

### Post by crip720 on 2019-12-05
The password is only for logging in and/or for using sudo.  Are you sure encryption was not offered or maybe missed seeing it?

---

### Post by TheFu on 2019-12-05
Linux uses passwords to login.  This is standard.  It has nothing to do with encryption most of the time.
A linux system that doesn't use a password for login is the oddity, an exception.  I've never seen one of these in person.  I suppose a few people with a desktop only used by them at home might choose this option. I would not.

There is no way to retrieve a Linux password later.

There are multiple ways to modify a Linux password later using alternate boot media or a "Try Ubuntu" runtime or grub options that all provide a different root capability.   Look up resetting password guides - howtogeek has one.  This has nothing to do with any encrypted files or file system.

---

### Post by crip720 on 2019-12-05
The OP was offered the password, but not to encrypt the hard drive.  OP is asking if hard drive is encrypted using the logged in password.

---

### Post by deadflowr on 2019-12-05
> What i don't know is if you have this password do you have encryption and passphrase.
No.
The only encryption offered on install is full-disk, done when you select the partitioning layout.
Home encryption has been removed as an option at install
(For a variety of reasons).

FDE (full disk encryption) does require a passphrase to be set,
but it not tied to any user as it is set to lock and unlock the system as a whole and not any one user's directories.

---

### Post by antee on 2019-12-06
Thank you guys. I thought that setting up password during installation means you have some kind of encryption.
Login password without encryptioin is not very usefull i guess.

---

### Post by CatKiller on 2019-12-06
> **antee said:**
> Login password without encryptioin is not very usefull i guess.
A login password is *extremely* useful even if you don't encrypt your drives. It means that each user's stuff is private from other users, and neither an unauthorised user nor a nefarious process can modify system-level stuff without a notification for authorisation.

Disc encryption is a different thing, for restricting access to a drive's contents from a different environment or when the drive is physically removed from the machine.

---

### Post by antee on 2019-12-06
Thank you. It makes sense.

---

### Post by TheFu on 2019-12-06
> **antee said:**
> Thank you guys. I thought that setting up password during installation means you have some kind of encryption.
Login password without encryptioin is not very usefull i guess.

Only to a point-n-click, single-system, non-networked, user.  
Advanced-beginners and experts have many uses for login passwords.  I cannot imagine doing anything without a login.  Right now, I'm using a laptop from a cafe to connect via x2go, to my home "desktop" where I'm writing this response using a browser that has been up and running for a few weeks with my credentials to about 15 different web logins. No need to re-authenticate just because we move locations, except via x2go to one system.
On that desktop, there terminals into ... let me count ... into 7 other computers.  I couldn't have made those initial connections without each of them having logins with passwords.  In reality, those connections and the x2go connect don't use a login password for authentication any more, they use ssh-keys, which are 1,000,000x more secure than passwords, but that initial trust to setup the ssh-keys required login passwords.

With sshfs, we can mount storage safely over the internet to my local machine. Very handy. It also uses ssh-keys.
With rsync, we can mirror/clone files between multiple systems.  Sort of like a backup.
With rdiff-backup, ... sftp ... and probably at least 50 other program .... we can remotely run programs, remotely access programs, remotely check system status for completion, connect to get output or pre-run data.  I like to have my computers work for me, so they do a bunch of things automatically, pull the results back local, so when the internet is out/unavailable, I have local copies of that information.  Had a 58 min outage here yesterday, but didn't notice it for most of that time. I track outages every week.
```
 Period 20191201-062611  - 20191206-082011
  Total Time: 7316 (min) 121.93 (hrs)
  Percent Up Time: 99.21 % 
  Percent Down Time: 0.79 % 
  Total Down Time: 58 min or 0.97 hrs
 Currently: UP
```

Basically, anytime I need to access stuff on any other computer, there was a login password involved at some point.

Are other people living in the same apartment/house?  Logins with passwords can allow each to use the same computer, have completely different GUIs, settings, and private file storage, if they want.

Linux is multi-user from the bottom to the top. Always has been, unlike Windows.  Windows still carries with it some single-user ideas and it always will, so there will always be code that didn't consider multiple users on the same system concurrently.  BTW - 1,000 different people can use the same Linux machine concurrently ... thanks to logins and passwords.  In the old days - you know, 1995 - I was sent to training where 12 monitors and keyboards were connected to a single computer. Your PC is probably more powerful than the Unix computer hosting 3,000 users concurrently in 1995. They all used remote terminals over ethernet to access the same "server."

Logins with passwords are extremely handy.

---

### Post by antee on 2019-12-06
Thank you. Very interesting but advanced examples. I am the only user of my pc but it sounds like a good protection against malware.

---

