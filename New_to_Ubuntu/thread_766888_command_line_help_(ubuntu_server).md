---
title: "command line help (ubuntu server)"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by jdix123 on 2008-04-25
Pretty much just need to know how to do two things non-graphically:

1) Mount the dvd drive and copy the entire contents to a specific directory

2) How to upgrade from 7.1 server to the new 8.04 LTS  I'm thinking something along the lines of sudo apt-get dist-upgrade or something but I'm blanking on the specific.

---

### Post by Kilz on 2008-04-25
> **jdix123 said:**
> 

2) How to upgrade from 7.1 server to the new 8.04 LTS  I'm thinking something along the lines of sudo apt-get dist-upgrade or something but I'm blanking on the specific.

sudo apt-get update
sudo apt-get dist-upgrade

should work.

---

### Post by Oldsoldier2003 on 2008-04-25
> **jdix123 said:**
> Pretty much just need to know how to do two things non-graphically:

1) Mount the dvd drive and copy the entire contents to a specific directory

2) How to upgrade from 7.1 server to the new 8.04 LTS  I'm thinking something along the lines of sudo apt-get dist-upgrade or something but I'm blanking on the specific.

[http://ubuntujourney.wordpress.com/2008/04/06/upgrade-gutsy-server-to-hardy-via-ssh/](http://ubuntujourney.wordpress.com/2008/04/06/upgrade-gutsy-server-to-hardy-via-ssh/)
```

sudo apt-get update
sudo apt-get upgrade
sudo aptitude install update-manager-core
sudo do-release-upgrade
```

---

### Post by jdix123 on 2008-04-25
Tried that first, but then I found this at the website:


sudo aptitude install update-manager-core
sudo do-release-upgrade


Maybe I should have looked harder before posting that one :)

---

### Post by jdix123 on 2008-04-25
And the first question?

---

