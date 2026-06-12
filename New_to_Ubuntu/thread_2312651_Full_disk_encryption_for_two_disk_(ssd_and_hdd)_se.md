---
title: "Full disk encryption for two disk (ssd and hdd) setup ?"
date: 2016-02-06
forum: New to Ubuntu
---

### Post by mark253 on 2016-02-06
If I set Ubuntu system on a 40Gb ssd drive with full disk encryption, will I be able to set user folder to be on encrypted Hdd with the same password so the system boot like normal 1 dysk system setup ?

---

### Post by TheFu on 2016-02-06
Each partition must be opened separately, but you can set the passphrase to be the same if you like.  dm-crypt has 8 slots to hold different decryption keys (so you can setup an "admin key" for the dm-crypt stuff, then give each user of the device their own dm-crypt decryption key, provided there are less than 7 users. ;)

Been using a Yubikey device with a static passphrase (and a pin) in one of the slots - this means that opening the encrypted partition can be easy, but highly secure (something I know and something I have).

Encryption of a folder or HOME directory uses a different method of encryption (vastly slower). Played with this once until I realized that  automatic backups wouldn't work at 3am on the system since encrypted HOME directories are only mounted when a user is logged in.

Hope this helps.

Now, I think you can use LVM and spread the PV across both disks, then add the encryption to that level (maybe, don't really know).  Found this - haven't read it carefully:
[https://wiki.archlinux.org/index.php/Dm-crypt/Specialties#The_encrypt_hook_and_multiple_disks](https://wiki.archlinux.org/index.php/Dm-crypt/Specialties#The_encrypt_hook_and_multiple_disks) Seems like some options.

---

