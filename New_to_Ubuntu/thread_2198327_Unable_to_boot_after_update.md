---
title: "Unable to boot after update"
date: 2014-01-08
forum: New to Ubuntu
---

### Post by czgirb on 2014-01-08
today, after update manager, i unable to boot to ubuntu. it boot to command prompt and there is:

ubuntu 12.04.3 LTS czgirb tty1
czgirb login:
password:

what should i do?

---

### Post by sandyd on 2014-01-08
Hi, can you login using your username and password, and run the following command?
```
sudo service lightdm stop
sudo lightdm --test-mode

```

Also, what is your video card, and do you have any proprietary drivers?

Thanks.

---

### Post by mastablasta on 2014-01-08
what is your GPU /graphics chip ?

---

### Post by czgirb on 2014-01-08
yes i can login

after do
> sudo service lightdm stop
it show:
**stop: unknown instance:**

> sudo lightdm --test-mode
it show a lot of Command Line and stop in:
*** checking battery state...**

**PS:**
i'm using Compaq **CQ40-328TU** and the **VGA** is **INTEL**

---

### Post by czgirb on 2014-01-08
VGA? Is the problem was caused by VGA?
Oh yes! The day before yesterday, I ever do a VGA upgrade by following this instruction from [https://wiki.ubuntu.com/Valve#Driver_Upgrades](https://wiki.ubuntu.com/Valve#Driver_Upgrades)
[B]Intel Graphic section.
[/B]> For Ubuntu 12.04 LTS, you'll need to update your mesa stack using the x-updates PPA.
On the command line (as root), run

[QUOTE]apt-add-repository ppa:glasen/intel-driver
apt-get install --install-recommends linux-generic-lts-quantal xserver-xorg-lts-quantal libgl1-mesa-glx-lts-quantal
apt-get update
apt-get -y dist-upgrade
glxinfo | grep "OpenGL version" # verify you have mesia 9.1.6

Then log out and back in, or reboot.
12.10 already includes all the necessary Intel bits, so if you're on this release no update is required. [/QUOTE]


And before that I do:
> 
**Purge Unity Lens with:**
* [COLOR=#000099]sudo apt-get purge unity-lens-video unity-lens-music
[/COLOR]**Remove Zeitgeist with:**
* [COLOR=#000099]sudo apt-get remove python-zeitgeist zeitgeist-core zeitgeist-datahub
[/COLOR]

---

### Post by czgirb on 2014-01-08
Again ...
While cleaning my Janitor, I was asking by Ubuntu Tweak if I wish to delete 3 files ... and I said YES
And after that ... my Ubuntu boot into **CLI (Command Line Interface)** ... not **G****UI (Graphical User Interface)**

---

### Post by mastablasta on 2014-01-09
janitor and such are not always a good idea. sometimes they might delete thing that shouldn't be deleted.

anyway i had a similar situation with proprietary drivers. upon update i got dumped to CLI.

but you have only opensource ones. a suggestion would be to boot with older kernel.
also since you are using 12.04.3 perhaps a better way would be to use: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) rather than PPA

---

### Post by czgirb on 2014-01-09
> **mastablasta said:**
> janitor and such are not always a good idea. sometimes they might delete thing that shouldn't be deleted.

anyway i had a similar situation with proprietary drivers. upon update i got dumped to CLI.

but you have only opensource ones. a suggestion would be to boot with older kernel.
also since you are using 12.04.3 perhaps a better way would be to use: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) rather than PPA

SORRY ... my english ability is not good.
Would you mind to guide me one-by-one for what I should do?

---

### Post by czgirb on 2014-01-09
do
> sudo apt-get install --install-recommends linux-generic-lts-raring xserver-xorg-lts-raring libgl1-mesa-glx-lts-raring
and the GUI is back ...
[SIZE=5]**THANK YOU to [MASTABLASTA]("http://ubuntuforums.org/member.php?u=964486")**[/SIZE]

---

