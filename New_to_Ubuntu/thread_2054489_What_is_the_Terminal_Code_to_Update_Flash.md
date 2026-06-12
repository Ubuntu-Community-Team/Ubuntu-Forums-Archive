---
title: "What is the Terminal Code to Update Flash"
date: 2012-09-07
forum: New to Ubuntu
---

### Post by balkrish999 on 2012-09-07
So what is the Terminal Code to Update, Firefox to the latest version NOT BETA and Update Flash Player?

---

### Post by pqwoerituytrueiwoq on 2012-09-07
```
sudo apt-get update;sudo apt-get upgrade
```
or are you using a EOLed version of ubuntu

---

### Post by jerome1232 on 2012-09-07
In Ubuntu the package manager updates every package with the latest versions in the repositories you have. For the most part the official Ubuntu repositories only patch in security updates, one exception is firefox is updated with new versions.


Generally if you want bleeding edge versions, the way to do this is by adding ppa's (personal pacakge archives), ppa's are just repositories maintained by individuals, usually used for software not available in the official repo's or for bleeding edge versions not in the official repo's.

---

### Post by balkrish999 on 2012-09-07
Im Using Ubuntu 10.04 LTS 


ALl i want it Firefox to be updated, i DONT WANT TO Do it via,  package manager, because i dont want all the other useless updates, 

Isnt there a Terminal Code JUST FOR Firefox?

---

### Post by vasa1 on 2012-09-07
> **balkrish999 said:**
> Im Using Ubuntu 10.04 LTS 


ALl i want it Firefox to be updated, i DONT WANT TO Do it via,  package manager, because i dont want all the other useless updates, 

Isnt there a Terminal Code JUST FOR Firefox?
There's no need for CAPS. Your first post didn't have enough information and so people asked for more.

---

### Post by newb85 on 2012-09-07
> **balkrish999 said:**
> Im Using Ubuntu 10.04 LTS 


ALl i want it Firefox to be updated, i DONT WANT TO Do it via,  package manager, because i dont want all the other useless updates, 

Isnt there a Terminal Code JUST FOR Firefox?

I don't know about a CLI command, but you could open Update Manager, un-check the updates you consider  useless, and then hit Update.

---

### Post by mastablasta on 2012-09-07
> **balkrish999 said:**
> 

ALl i want it Firefox to be updated, i DONT WANT TO Do it via,  package manager, because i dont want all the other useless updates, 

Isnt there a Terminal Code JUST FOR Firefox?

no there is no code just fpor firefox i believe. however in package manager Synaptic you can lock other packages so they never upgrade. also you can in default package manager deselect all other updates and only select firefox to be upgraded.

---

### Post by jerome1232 on 2012-09-07
> **balkrish999 said:**
> Im Using Ubuntu 10.04 LTS 


ALl i want it Firefox to be updated, i DONT WANT TO Do it via,  package manager, because i dont want all the other useless updates, 


Useless? They are security updates, that fix security related vulnerabilities in your programs. Nonetheless you can check the package manager to see if an update for firefox is avaible, then simply install it to upgrade it and only it. install always installs the latest version.

ie if there was and update available for firefox, the below would upgrade firefox. Otherwise it will just tell you it's already installed.

```
sudo apt-get install firefox
```Note failure to install security updates will leave your system vulnerable to known security threats. Do so at your own risk.

---

### Post by balkrish999 on 2012-09-07
> **jerome1232 said:**
> Useless? They are security updates, that fix security related vulnerabilities in your programs. Nonetheless you can check the package manager to see if an update for firefox is avaible, then simply install it to upgrade it and only it. install always installs the latest version.

ie if there was and update available for firefox, the below would upgrade firefox. Otherwise it will just tell you it's already installed.

```
sudo apt-get install firefox
```Note failure to install security updates will leave your system vulnerable to known security threats. Do so at your own risk.

Thanks! it works , I meant that the Useless Updates like "office" etc, which i never use.  should really uninstall them but, use them once now and then, Thanks

---

### Post by deadflowr on 2012-09-07
I would just run the update manager and peruse the listed updates, looking for both firefox and flash.
However, beforehand, Check firefox's plugins and see what version flash you have now.
If the version is 11.2.202.238, then your flash is as up to date as it will ever ever be.

---

