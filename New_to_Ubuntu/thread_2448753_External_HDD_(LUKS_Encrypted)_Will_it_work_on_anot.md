---
title: "External HDD (LUKS Encrypted) Will it work on another Ubuntu Installation."
date: 2020-08-13
forum: New to Ubuntu
---

### Post by ia148-461 on 2020-08-13
Hello. I have an external hard drive (3TB) that I have formatted to EXT4 with LUKS encryption. When I turn my machine on I must enter a password that I set to decrypt and mount the disk in my system.

The issue I have is that I would like to upgrade my internal HDD and reinstall a fresh copy of Ubuntu 20.04. Will the new Ubuntu install be able to mount the disk and access all my data or will I need to backup some sort of encryption key?

cheers.

---

### Post by TheFu on 2020-08-13
**Short answer**
LUKS is portable.  The auto-mounting may need some setup, but it does work.  

**Longer**
I've had LUKS on external disks for years. Whenever those external disks get connected to other machines, I have to use **cryptsetup open** and usually **vgchange -ay** to get the LVM VGs, LVs, recognized on the new system, but after that, all the storage is available.  Just one of the correct LUKS unlock entry methods is needed.  There are 8-slots to hold different LUKS credentials.  These can be a long, complex, passphrase, a key-file, or some sort of challenge/response from a hardware device, like a Yubikey. I keep a 65 random character passphrase in slot-0. Not sure I could type that in, but it is there as a backup.  The 4k keyfile is used when in trusted locations. This is stored on USB flash storage only during boot.  Most of the time, I use the challenge/response with a yubikey. It required about 10 minutes of setup, but works well. Best to setup this for a few different devices, so when we lose one for a few days, it doesn't kill our access.

---

