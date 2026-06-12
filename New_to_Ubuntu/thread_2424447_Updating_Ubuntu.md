---
title: "Updating Ubuntu"
date: 2019-08-08
forum: New to Ubuntu
---

### Post by harley512 on 2019-08-08
I see that 18.04.3 is out I have 18.04 is there a way to update my installed version without reinstalling everything again.

---

### Post by cruzer001 on 2019-08-08
You sure?  In terminal:
```
lsb_release -a
```

---

### Post by oldfred on 2019-08-08
fred@bionic-z97:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.2 LTS
Release:    18.04
Codename:    bionic
fred@bionic-z97:~$ sudo apt update

After update:
fred@bionic-z97:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.3 LTS
Release:    18.04
Codename:    bionic


The 18.04.3 is an updated ISO so you do not have to download as much to make it current. But it now will use the newer kernel as part of HWE. That is more for those with newer hardware that need newer kernel. If you have HWE, you have to upgrade kernel/HWE each release through 18.04.5, see below. You get all the updates, normally but now new versions of kernel if you have installed 18.04 or 18.04.1.  If you must have newer kernel you can install it with the HWE commands.

       Ubuntu 18.04.3 LTS Released - Switches To Using 19.04's Linux 5.0 HWE - Aug 2019
[https://lists.ubuntu.com/archives/ubuntu-announce/2019-August/000248.html](https://lists.ubuntu.com/archives/ubuntu-announce/2019-August/000248.html)
[https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes](https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes)
With 18.04.3 LTS HWE upgrades will be required to 18.04.5 HWE when available
[https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack)

---

### Post by Bashing-om on 2019-08-08
harley512; Hello -

Allow me to expand on 18.04.3 just a bit.

If you installed ubuntu 18.04 or 18.04.1 - and are updated - then you have the default "4.15.0-55-generic
" kernel. That maybe exactly what you want to remain on.

the 18.04.3 is a HWE (HardWare Enablement) release to support newer hardware. Only of interest here IF you need the enhancements that HWE brings. IF so, there is a means to upgrade to the HWE cycle from the default install. 

```

sysop@x1804mini:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.3 LTS
Release:	18.04
Codename:	bionic
sysop@x1804mini:~$

sysop@x1804mini:~$ dpkg -l | grep linux-
<snip>
ii  linux-image-4.15.0-52-generic         4.15.0-52.56                        amd64        Signed kernel image generic
ii  linux-image-4.15.0-54-generic         4.15.0-54.58                        amd64        Signed kernel image generic
ii  linux-image-4.15.0-55-generic         4.15.0-55.60                        amd64        Signed kernel image generic
ii  linux-image-generic                   4.15.0.55.57                        amd64        Generic Linux kernel image
<snip>

```

Where I have no interest in HWE.

[INDENT]hope this helps
[/INDENT]

---

### Post by cruzer001 on 2019-08-08
As oldfred pointed out a manual update may be needed.
```
sudo apt update && sudo apt full-upgrade -y
```

And like Bashing-om, I also stick with the 4.15 kernel version.

---

### Post by CatKiller on 2019-08-09
The other thing to be aware of is that it's *only* whether you're on the HWE track by default that's different between installing 18.04 (or 18.04.1) and upgrading, or installing 18.04.2/18.04.3. All the other software will be exactly the same with exactly the same updates, and your version number will be listed as 18.04.3 after updates.

---

### Post by walts48 on 2019-08-09
I didn't do anything special to update, just let the Software Updater do its work when notified of updates.

Today I checked Settings > Details and Ubuntu 18.04.3 LTS is what I got.

---

### Post by harley512 on 2019-08-13
I updated everything and still get 18.04 when I run lsb_release -a

---

### Post by deadflowr on 2019-08-13
Post the output.

Does it say 18.04 in the Release field or in the Description field?
Or Both?

---

### Post by harley512 on 2019-08-13
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 19.04
Release:    19.04
Codename:    disco

---

### Post by deadflowr on 2019-08-13
You're on 19.04, all is good.
19.04 isn't an LTS release so no point releases.

---

### Post by harley512 on 2019-08-13
Thanks that answer my question.

---

### Post by deadflowr on 2019-08-13
Please mark this thread as solved then:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

