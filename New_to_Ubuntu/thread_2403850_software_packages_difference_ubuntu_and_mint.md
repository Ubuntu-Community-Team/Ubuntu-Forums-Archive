---
title: "software packages difference: ubuntu and mint"
date: 2018-10-17
forum: New to Ubuntu
---

### Post by otlichnik73 on 2018-10-17
Hi there! I am new to Linux generally,  have been using Linux Mint for over a year, after switching from Windows. Now I am playing around with Ubuntu 18 (as a VM), considering installing that on my next machine.
This is  a very basic question regarding the subject of software sources, which I probably don't really understand.
Noticed that when I searched for software, I can't find some packages on Ubuntu. I tried changing Ubuntu source to same as my Mint (http.//archive.ubuntu.com/ubuntu) which shows under "mirrors" "base (xenial)" in Mint "software sources".
I wanted to install "ubuntu-restricted-extras" in Ubuntu as I did in Mint. When I search for "ubuntu-restr.." in Mint software manager, it shows the package, but in Ubuntu software manager it does not. I installed in via command line in Ubuntu (sudo apt-get ubuntu-restricted-extras), seemed to work.
But why does it not show up in software manager? Generally, I noticed that Ubuntu manager seems to give you less options than Mint?
Thanks!

---

### Post by monkeybrain20122 on 2018-10-17
Install synaptic and use it to manage your package, you will find all packages. the Software Center only lists a small fractions of packages available in the normal repositories.
```

sudo apt install synaptic
```

---

### Post by mastablasta on 2018-10-17
you should probably just type restricted or something like that and it would show up (if you have proper sources marked).

---

### Post by ajgreeny on 2018-10-17
> **monkeybrain20122 said:**
> Install synaptic and use it to manage your package, you will find all packages. the Software Center only lists a small fractions of packages available in the normal repositories.
```

sudo apt install synaptic
```
Or use the command line to install packages.
```
sudo apt install ubuntu-restricted-extras
```

I can not, however, comment on the sense (or not) of adding specific Mint repos to a Ubuntu system; I know in the past certain things have worked without a problem but I suspect there could be some that might either interfere with Ubuntu's system, or may simply not work.

It may be worth searching and asking at the [Mint Forum]("https://forums.linuxmint.com/index.php") where they may know more than we do here.

---

### Post by Dennis N on 2018-10-17
Some of the default Mint applications aren't in Ubuntu repositories, like the **Xaps: xed, pix, xreader, xplayer, xviewer**. If you like them, you can install them in Ubuntu from a PPA and they work fine.

---

### Post by oldos2er on 2018-10-17
There can be differences in package versions and names across distros; this is normal. If you look at the package descriptions, they should match closely though. I wouldn't be mixing repositories from another distro into whichever one you're running, you may break APT.

---

