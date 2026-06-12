---
title: "Nvidia pkg. missing"
date: 2014-05-28
forum: New to Ubuntu
---

### Post by Timothy_Cota on 2014-05-28
I get a message after login that nvidia pkg. failed to install.  Would this pkg. be in a repository?  If not where could I find it?   unktim

---

### Post by cariboo on 2014-06-03
Which Nvidia driver are you trying to install, it looks like the latest driver in the 14.04 repositories is nvidia-331. If you need anything newr, you may need to set up the [zorg-edgers ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa"). To enable the repository, open a terminal and type:

```
sudo apt-add-repository ppa:xorg-edgers/ppa
```

and follow the prompts. When done type:

```
sudo apt-get update && sudo apt-get install nvidia-<version>
```

where <version> -s the number of the version you want to install.

---

### Post by SeijiSensei on 2014-06-03
Before installing a PPA, try running "sudo apt-get install nvidia-current".

---

### Post by Timothy_Cota on 2014-06-15
[**[COLOR=#000000]Seijisensei[/COLOR]**]("http://ubuntuforums.org/member.php?u=698195")
Thanks, It worked.  First thing I have had go smoothly since I switched to Linux.  unktim

---

