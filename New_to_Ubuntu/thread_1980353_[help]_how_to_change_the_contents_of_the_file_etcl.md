---
title: "[help] how to change the contents of the file /etc/lsb-release?"
date: 2012-05-15
forum: New to Ubuntu
---

### Post by airinuxazis on 2012-05-15
Hello....

how to replace

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"

to

DISTRIB_ID=Airinux
DISTRIB_RELEASE=12.05
DISTRIB_CODENAME=world
DISTRIB_DESCRIPTION="Airinux 12.05 LTS'

if I replace immediately, there will be problems in the apt.

please .... I need this for my remastered distro.   [-o<  [-o<  [-o<  [-o<

*N.B = I only children aged 12 years, I am from Indonesia*

---

### Post by Lisiano on 2012-05-15
No way to safely modify it without breaking USC (Not that I know of at least).
[http://askubuntu.com/questions/91297/change-the-os-name-from-ubuntu-to-something-else](http://askubuntu.com/questions/91297/change-the-os-name-from-ubuntu-to-something-else)
Only issue I see is with USC, apt should function normally. Apt uses the deb lines to find what it needs, it doesn't care about lsb_release, USC might though.

I also recomend reading up on remastering
[http://www.linuxforu.com/2011/05/how-to-remaster-ubuntu-to-get-a-customised-distribution/](http://www.linuxforu.com/2011/05/how-to-remaster-ubuntu-to-get-a-customised-distribution/)
[http://www.remastersys.com/ubuntu.html](http://www.remastersys.com/ubuntu.html)

---

### Post by airinuxazis on 2012-05-15
Alpha
Really? so how? I need it ......

 but in [https://bugs.launchpad.net/ubuntu/+bug/599694](https://bugs.launchpad.net/ubuntu/+bug/599694) acceptable, if I ? how....

---

### Post by Lisiano on 2012-05-15
add-apt-repository gets broken simply because it assumes the codename is the one it needs. Just keep the codename as precise or instruct your users to manually add repositories. apt-get is unnafected.

---

### Post by airinuxazis on 2012-05-15
ok, thank you, :icon_frown:

---

