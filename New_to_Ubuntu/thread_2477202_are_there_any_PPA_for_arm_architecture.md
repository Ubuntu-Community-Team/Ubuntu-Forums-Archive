---
title: "are there any PPA for arm architecture"
date: 2022-07-17
forum: New to Ubuntu
---

### Post by jindam-vani on 2022-07-17
are there any PPA for arm architecture? is it possible to search packages for ppa?

---

### Post by deadflowr on 2022-07-18
Sure, there are arm supported PPAs, a few.
You can search Launchpad here for PPAs: [https://launchpad.net/ubuntu/+ppas]("https://launchpad.net/ubuntu/+ppas")
Though there is no guarantee the PPAs built will have arm versions.
That is entirely up to the PPA maintainers.

---

### Post by sudodus on 2022-07-18
If the PPA contains only interpreted code, for example bash shellscripts (but no compiled code), I think it should work for different architectures, for example amd64 and arm.

I have never tested 'my' **[FONT=Courier New][ppa:mkusb/ppa](https://help.ubuntu.com/community/mkusb)[/FONT]** (with bash shellscripts) in a computer with arm architecture, but I would be happy if you test if it works and let me know the result :-P

---

### Post by ActionParsnip on 2022-07-19
Duckduckgo has a PPA bang. It searches all PPAs for the term. Just type into the search bar
```

!PPA Firefox

```
For example. Remember to filter the PPA for your release of Ubuntu. Not all PPAs support all releases of Ubuntu. You should also check that they support your architecture.
PPAs are not official package sources so we have no way of knowing what is in each package. Be careful

---

### Post by MAFoElffen on 2022-07-24
Why PPA's? I do both Amd64 and Arch64, and most all packages are there for ARM is in the ARM Repo's...
```

---------- Repository Information from '/etc/apt/sources.list and etc/apt/sources.list.d/':

Sources List:
deb http://ports.ubuntu.com/ubuntu-ports focal main restricted
deb http://ports.ubuntu.com/ubuntu-ports focal-updates main restricted
deb http://ports.ubuntu.com/ubuntu-ports focal universe
deb http://ports.ubuntu.com/ubuntu-ports focal-updates universe
deb http://ports.ubuntu.com/ubuntu-ports focal multiverse
deb http://ports.ubuntu.com/ubuntu-ports focal-updates multiverse
deb http://ports.ubuntu.com/ubuntu-ports focal-backports main restricted universe multiverse
deb http://ports.ubuntu.com/ubuntu-ports focal-security main restricted
deb http://ports.ubuntu.com/ubuntu-ports focal-security universe
deb http://ports.ubuntu.com/ubuntu-ports focal-security multiverse

Sources List from SourcesD:
/etc/apt/sources.list.d/github-cli.list:
deb [arch=arm64 signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main
/etc/apt/sources.list.d/yktooo-ubuntu-ppa-focal.list:
deb http://ppa.launchpad.net/yktooo/ppa/ubuntu focal main

```
The PPA's I'm using there address things I needed and/or use...

Are you looking for something specific?

---

