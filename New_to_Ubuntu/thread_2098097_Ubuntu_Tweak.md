---
title: "Ubuntu Tweak?"
date: 2012-12-25
forum: New to Ubuntu
---

### Post by Yezinki on 2012-12-25
How is Ubuntu tweak installed, from Software center or from some other site & which version works with 12.04 LTS?

Thanks.

---

### Post by Pjotr123 on 2012-12-25
Do NOT use Ubuntu Tweak:
[https://sites.google.com/site/easylinuxtipsproject/fatalmistakes](https://sites.google.com/site/easylinuxtipsproject/fatalmistakes)

You should *really* avoid things like that, if you want a stable system. :)

---

### Post by ashwinrao on 2012-12-25
You'll get required info at [http://ubuntu-tweak.com/downloads/](http://ubuntu-tweak.com/downloads/) . However, be cautious while adding third party software sources and PPA's using Ubuntu tweak.

---

### Post by NikTh on 2012-12-25
Hi ,
Ubuntu Tweak is not in main Ubuntu repositories. You have to add an external repository to install Ubuntu Tweak. 

Here is the repository : [https://launchpad.net/~tualatrix/+archive/ppa](https://launchpad.net/~tualatrix/+archive/ppa)
Below is Ubuntu's warning about almost all external repositories 
> You can update your system with unsupported packages from           this untrusted PPA.....You have to now that , so Ubuntu informs you. 

The commands to add the repository and install Ubuntu Tweak are 
```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update 
sudo apt-get install ubuntu-tweak
```Thanks

---

