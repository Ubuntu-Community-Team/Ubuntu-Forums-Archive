---
title: "Unmet dependencies"
date: 2015-05-16
forum: New to Ubuntu
---

### Post by Avishek_Das on 2015-05-16
Whenever i am tryin gto install any package like this one
```
sudo apt-get install vsftpd
```

terminal shows me an error.

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 audacity-dbg : Depends: audacity (= 1.3.12-2) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).




can't i get rid of this???
I need you Expert guys to help

---

### Post by coffeecat on 2015-05-16
Two things:

Did you try running *sudo apt-get -f install* as the error message recommends? If you haven't, run it and post the output

Audacity version 1.3.12-2 is an old one, possibly the one used in Ubuntu 10.04. What version of Ubuntu are you using? If you are running 10.04, you are running an obsolete, unsupported version of Ubuntu.

---

### Post by Avishek_Das on 2015-05-16
i ran it 
```
*sudo apt-get -f install*
```
and now it's working fine :D ... thanks buddy

---

### Post by coffeecat on 2015-05-16
Did you see this?

> **coffeecat said:**
> 
Audacity version 1.3.12-2 is an old one, possibly the one used in Ubuntu 10.04. What version of Ubuntu are you using? If you are running 10.04, you are running an obsolete, unsupported version of Ubuntu.

If you are running an obsolete version of Ubuntu your package management won't be working fine for long. You won't be able to install new apps, there will be no security updates, and your system will be vulnerable. What version of Ubuntu are you running?

---

