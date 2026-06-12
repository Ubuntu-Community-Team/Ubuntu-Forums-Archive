---
title: "full disk encryption"
date: 2012-07-09
forum: New to Ubuntu
---

### Post by aef54 on 2012-07-09
I'd like to do a full disk encryption of the drive on which Ubuntu is installed. If it were windows, I'd use TrueCrypt. However, it doesn't have that option for Linux.

What method should I use to do Full Disk Encryption on Ubuntu?

---

### Post by cryptotheslow on 2012-07-09
I believe if you use the Alternate installation CD rather than the usual Desktop one it gives you the option to encrypt the entire disk during the installation process. n.b. a small boot partition will be created that will not be encrypted as it needs to be accessible to carry out some early boot processes.

You could also consider the option the normal Desktop installation CD process gives to encrypt just your home directory.

---

### Post by Double.J on 2012-07-09
There's a couple of options really. First it's worth pointing out that full disk encryption isn't always necessary with linux; you can just encrypt your home partition. This is very popular because it allows you to protect your personal information and documents, whilst leaving access open to the system. This can be very useful when carrying out maintenance - boot loader repairs, etc. as you are able to access the config files from say a live CD or other distro.

You can encrypt your home partition as Cryptotheslow says either during alternate install, or retrospectively using information on [this thread]("http://ubuntuforums.org/showthread.php?t=1449168"). 

I've never attempted full disk encryption;  I need to access my system from my other distros, but there is ubuntu documentation on the subject [here]("https://help.ubuntu.com/community/FullDiskEncryptionHowto").

Hope it helps!

---

### Post by aef54 on 2012-07-09
Thank you gentlemen. I installed Ubuntu on a spare hard drive and it's a sandbox kinda project. I just experiment with it, and if it gets messed up, I format and reinstall.

I'm going to investigate both options you suggested and if encounter anything worth noting, you'll be the first to hear it.

---

### Post by Double.J on 2012-07-09
> **aef54 said:**
> Thank you gentlemen. I installed Ubuntu on a spare hard drive and it's a sandbox kinda project. I just experiment with it, and if it gets messed up, I format and reinstall.

You're welcome! Whilst your experimenting with the alternate installer and seeing what linux can do, may be worth checking out [LVM]("http://en.wikipedia.org/wiki/Logical_volume_management"); it's pretty big in other distros, some use it by default now. Ubuntu doesn't to keep things simple, and it's not strictly necessary on a single hdd, but it does have the awesome feature of letting you resize partitions after install relatively easily.

Of course it's not at all necessary... just thought it'd be interesting to experiment with ;)

---

