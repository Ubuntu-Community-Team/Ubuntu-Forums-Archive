---
title: "Unsure about software sources"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by dizzy1kenobi on 2008-11-12
I am unsure about two sources are they safe?

deb [http://ppa.launchpad.net/hexmode/ubuntu](http://ppa.launchpad.net/hexmode/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/hexmode/ubuntu](http://ppa.launchpad.net/hexmode/ubuntu) hardy main

---

### Post by CLomax on 2008-11-12
They're from launchpad. Look OK to me.

---

### Post by ubuntu27 on 2008-11-12
Personal Package Archives or PPA are personal or TEAMS repository, it is not an official ubuntu or canonical repository, as such you have to trust the people behind the PPA about their quality of packaging and software (if they made it). 

PPA is a provides a nice way for people to form a team and package a software that it is not in the official repositories. Example being, openoffice.org 3

You can install OpenOffice.org 3 by adding those volunteers repositories (PPA).

Most of the time you can trust them :)

But, be aware in the future. It has not happen yet, but it is possible theoretically that someone could use PPA to propagate malicious software.

Fortunately, People are looking forward to how to help and provide benefit to the community. I don't see any reason for someone to miss use PPA. That's my opinion. We are co-operating with the Ubuntu's spirit.


Here are some official words about PPA:

"Personal Package Archives (PPA) allow you to upload Ubuntu source packages to be built and published as an apt repository by Launchpad. You can find out more about PPAs and how to use them in [LaunchPad]("https://launchpad.net/")'s [help page]("https://help.launchpad.net/Packaging/PPA")." 1)

"Important: when you install software from a PPA, Ubuntu will warn you that it is unsigned. PPA packages are unsigned because they are not official Ubuntu packages. You should make sure that you're confident in the PPA owner's abilities before you install their packages. We're working to fix this and enable you to sign your packages in the near future." 2)

1) [https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)

2) [https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)

---

