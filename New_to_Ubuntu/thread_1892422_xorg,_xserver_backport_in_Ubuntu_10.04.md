---
title: "xorg, xserver backport in Ubuntu 10.04"
date: 2011-12-07
forum: New to Ubuntu
---

### Post by willykilly on 2011-12-07
Hi,
How to install xorg xserver 1.8 in ubuntu Lucid 10.04. I tried adding repositories and updated apt. Then I chose synaptic and clicked reload. Then uninstalled xorg and installed it again. Still it remains in the same version.
I need to install xorg xserver 1.8 from backports for ubuntu Lucid 10.04.
Also I am not able to find a "new thread" link in a backports forum of this same group. I had to come to absolute beginners and use the "new thread" link.

Thanks in advance.

---

### Post by beew on 2011-12-08
Add the xorg-edgers ppa and update

```
sudo add-apt-repository ppa:xorg-edgers/ppa

sudo apt-get update

sudo apt-get upgrade
```It should be pretty safe since they have stopped updating for Lucid and Maverick long time ago. But their old stuffs would still be a lot more up to date than what you have from the repo.

In case something goes wrong you should install ppa-purge 
```
sudo apt-get install ppa-purge
```If something does go wrong ```

sudo ppa-purge ppa:xorg-edgers/ppa

```This will downgrade all the packages installed from the ppa to your old versions, then reboot.

In the future if you intend to upgrade (I would recommend clean install personally) , you will also need to run ppa-purge on xorg-edgers or the upgrade will fail.

EDITED: Some people use Ubuntu-tweak and it has a ppa purge option. Don't use that, it doesn't work.

---

### Post by willykilly on 2011-12-09
Thanks for the response. I will try what you said.

---

