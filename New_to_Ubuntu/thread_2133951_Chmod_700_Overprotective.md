---
title: "Chmod 700 Overprotective?"
date: 2013-04-09
forum: New to Ubuntu
---

### Post by mamamia88 on 2013-04-09
Ok basically I want to be able to read,write, and execute anything in my home directory.  I don't share the computer with anyone else and nobody connects to it but me so the use of a group for access to files seems unnecessary for me (since the group would consist of 1 person me). By setting chmod 700 wouldn't it in theory prevent a hacker from creating a user and accessing the files?   But to create a user they would need to be root anyway pretty much making chmod 700 useless in the first place?    I have a few programs that store config files in my home folder but assuming I'm logged in as my user having chmod 700 shouldn't cause any problems then right?

---

### Post by deadflowr on 2013-04-09
Changing the permissions to 700 will give you full rights and let nobody else see anything in the folder/directory.
I do it on all machines, but I also from time to time share my machines with others and am, at times, slightly embarrassed by the content I have.;)
So I usually set up a second account for other users and block their access to my folder.

But yeah, if a hacker gained root access, then whether they change the access to your folders is probably going to be the least of your worries.

---

### Post by mamamia88 on 2013-04-09
> **deadflowr said:**
> Changing the permissions to 700 will give you full rights and let nobody else see anything in the folder/directory.
I do it on all machines, but I also from time to time share my machines with others and am, at times, slightly embarrassed by the content I have.;)
So I usually set up a second account for other users and block their access to my folder.

But yeah, if a hacker gained root access, then whether they change the access to your folders is probably going to be the least of your worries.

true and all my good stuff is on dropbox anyway. should probably work on making that more secure

---

### Post by DuckHook on 2013-04-09
Greetings deadflower

You are already aware of this option but for the general reader:

An option to consider for this sort of risk is to encrypt a private directory using ecryptfs with a strong pass-phrase and dump all of your sensitive data into ~/Private. Even chroot-ing into your machine could not decrypt such a directory unless the cracker has the pass-phrase. Instructions [here]("https://help.ubuntu.com/community/EncryptedPrivateDirectory").

There are drawbacks. From assorted forum experience/feedback:
1. People change system passwords, forget their old one and then forget the encryption passphrase, in which case, they are hooped. Data is totally lost and unrecoverable.
2. Added complexity and overhead.
3. Lousy passphrase leads to hackable system thus imparting false sense of security.
4. Does nothing about residue in tmp, swap, cache, thumbnails, etc unless you move many of these into ~/Private and softlink back to original location. Also, need to encrypt swap and place /tmp and /var/tmp into RAM.
5. A deep disk scan can sometimes reconstruct the unencrypted originals from locations prior to moving into ~/Private.

Of course, if you are being chased by people who would go to those sorts of lengths, you have bigger problems than hiding a few files.

---

### Post by deadflowr on 2013-04-09
> **DuckHook said:**
> Greetings deadflower

You are already aware of this option but for the general reader:

An option to consider for this sort of risk is to encrypt a private directory using ecryptfs with a strong pass-phrase and dump all of your sensitive data into ~/Private. Even chroot-ing into your machine could not decrypt such a directory unless the cracker has the pass-phrase. Instructions [here]("https://help.ubuntu.com/community/EncryptedPrivateDirectory").

There are drawbacks. From assorted forum experience/feedback:
1. People change system passwords, forget their old one and then forget the encryption passphrase, in which case, they are hooped. Data is totally lost and unrecoverable.
2. Added complexity and overhead.
3. Lousy passphrase leads to hackable system thus imparting false sense of security.
4. Does nothing about residue in tmp, swap, cache, thumbnails, etc unless you move many of these into ~/Private and softlink back to original location. Also, need to encrypt swap and place /tmp and /var/tmp into RAM.
5. A deep disk scan can sometimes reconstruct the unencrypted originals from locations prior to moving into ~/Private.

Of course, if you are being chased by people who would go to those sorts of lengths, you have bigger problems than hiding a few files.

Great point.
I wasn't thinking in terms of encryption, but rather in terms of whether or not changing permissions to 700 was overkill.

But anyway, I have had point number one happen to me.:(

Luckily, I utilize backups, so...;)

---

