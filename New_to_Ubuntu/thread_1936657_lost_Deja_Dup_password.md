---
title: "lost Deja Dup password"
date: 2012-03-06
forum: New to Ubuntu
---

### Post by old koot on 2012-03-06
Recently I tried to upgrade to Ubuntu 11.10,  Then I got hit by a power bump as I was upgrading. I was lucky that I used Deja Dup  to backup my files  to separate  drives.  One is a external harddrive (Seagate)  and the other is an internal hard drive (/dev/sdb1/ )   My main drive where I would like to keep the working data is  /dev/sda1/,  All data was lost after the the power bump.
Unfortunately I had saved the password in passwords and Keys in 10.04.  I am now in a situation  where I do not know the password for Deja Dup to recover my data files.  

My technician  changed  my computer user to “ubuntugdskt” instead of   my previous computer user.


This the first file on the Deja Dup backup .
duplicity-full.20120212T173538Z.manifest.gpg
PGP/MIME-encrypted message header (application/pgp-encrypted)

---

### Post by lechien73 on 2012-03-06
I'm sorry to tell you that unless you can get access to your old keyring (which sounds unlikely), then you won't be able to get access to the encrypted backup file.

As far as I know, deja dup protects the backup files with 128-bit encryption, so trying to brute force the password would so much time and computing power that - for all intents and purposes - it's not possible.

---

