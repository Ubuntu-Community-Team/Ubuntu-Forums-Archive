---
title: "possible to upgrade from 12.10 to 13.04 with liquorix kernel 3.8.3-1 installed?"
date: 2013-04-27
forum: New to Ubuntu
---

### Post by rootfairy on 2013-04-27
hi, 

i currently run xubuntu 12.10 with liquorix kernel 3.8.8-1. would it  be possible to upgrade via the upgrade-gui to 13.04 without messing it  all up? would the 13.04 kernel replace the current liquorix-kernel and  i'd have to reinstall liqourix again? whats going to happen? :D :Z 

best regards

edit: can some moderator change the title to 3.8.8-1 kernel?

---

### Post by pqwoerituytrueiwoq on 2013-04-27
raring uses 3.8.0-19 atm and 3.8.8>3.8.0 so it should not replace your default kernel
you could remove the stock kernel in synaptic (linux-image linux-headers linux-headers-generic linux-image-generic)

---

### Post by rootfairy on 2013-04-27
thx. on liquorix forums they advise to remove dkms in order to install non-free gfx drivers:

> 
dkms video drivers

dkms is a mess, and is not going to play well with a new kernel. Your best bet if you want to run a new kernel which will require a new video driver is to purge dkms and install the driver with sgfxi. That downloads and cleans out your system, then installs the driver from the actual company site that makes it, ie, nvidia or amd/ati. 


u think this is a good idea? can the system run without dkms at all?

---

### Post by snowpine on 2013-04-27
I recommend you remove all 3rd-party software sources (including Liquorix repo) before you attempt the upgrade.

I'm not making this up, it's straight from the Ubuntu Upgrade Notes:

> Using packages from repositories not controlled by Ubuntu is not recommended as it can be a security risk and may break or complicate your upgrade.

Then if you want, you can reinstall liquorix again after the upgrade (but I'm not sure why you'd want to).

Also consider the option of doing a fresh install, rather than a release upgrade.

---

### Post by rootfairy on 2013-04-27
i think the upgrade disables all 3rd party sources during the upgrade, at least thats what it said. i'd install the liquorix kernel coz i assume its better than the default kernel, or isnt it so?

---

### Post by snowpine on 2013-04-27
If you are having problems with the stable and supported Ubuntu kernel, then I agree it is logical to look for alternative kernels elsewhere. Liquorix is a fine project; I have nothing bad to say about liquorix kernel and its developer. :)

---

### Post by rootfairy on 2013-04-27
i probably do a fresh install. and what about purging dkms? good or bad idea?

---

### Post by snowpine on 2013-04-27
I use dkms on my computer.
But I don't use liquorix kernel, so therefore I don't read advice from liquorix forums. ;)

---

