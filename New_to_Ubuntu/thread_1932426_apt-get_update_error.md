---
title: "apt-get update error"
date: 2012-02-27
forum: New to Ubuntu
---

### Post by stonecoldjha on 2012-02-27
Hi,
when i try updating using **sudo apt-get update** it starts downloading package files, but ultimately ends up with this:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EFB4FA7E41D78D0C
E: Unable to parse package file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-security_restricted_i18n_Index (1)
sonu@sonu-desktop:~$ 

how do i fix this?

---

### Post by cortman on 2012-02-27
Hi, the first set of instructions given in [this blog post]("http://cortman.wordpress.com/2012/02/27/how-to-fix-gpg-errors-in-ubuntu/") should resolve the problem.

---

### Post by stonecoldjha on 2012-02-27
I ran the first set of commands given there, and after that i ran sudo apt-get update, i get the following errors:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EFB4FA7E41D78D0C
E: Unable to parse package file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-security_restricted_i18n_Index (1)
sonu@sonu-desktop:~$ 
i tried running the last command replacing hex_key_here with EFB4FA7E41D78D0C. But, I get the same output.

---

### Post by Jake5 on 2012-02-27
Have you rebooted the system? I got a similar response from
# sudo get-apt -install gde
If memory serves I actually had to reboot twice for some reason...
Cortman was there to help. He knows what's up, listen to his advice.

---

### Post by cortman on 2012-02-27
> **stonecoldjha said:**
> I ran the first set of commands given there, and after that i ran sudo apt-get update, i get the following errors:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EFB4FA7E41D78D0C
E: Unable to parse package file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-security_restricted_i18n_Index (1)
sonu@sonu-desktop:~$ 
i tried running the last command replacing hex_key_here with EFB4FA7E41D78D0C. But, I get the same output.

So you say you DID run

```
sudo rm -r /var/lib/apt/*
sudo apt-get update
```

? If so, please post the output of

```
cat /etc/apt/sources.list
```

I wonder if something is messed up in your sources.list file.

---

