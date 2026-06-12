---
title: "System corruption after mount sda drivers and edit sources list"
date: 2018-05-30
forum: New to Ubuntu
---

### Post by milazg on 2018-05-30
Hello, i am new to ubuntu and linux and I am coming to you guys because i read this forum alerts and the forum seems to be serious and committed to help and i really need instructions that i can trust because searching at stackoverflow and google random answers made me almost ruin my computer. 

I am always getting a message saying "system problem , report problem"
and my ubuntu started to disconnect from the internet. Somethimes pages doesnt load and then i disconnect and reconnet and then they start to work again. 

The problem started when i tried to unmount an SDA and **well i did it with the wrong sda, of course**, the one that was using my system). Ok i fixed it but everytime i start it appears a black terminal prompt for advanced options and Ubuntu is one of the options (**it doesnt mount and starts up directly as before**). 
After choosing the option i load and run terminal commands that appears /sda2/

After that i tried to install a software called pinguybuilder and edited my sources.list . Also i added some ppas. 

Then now i am not able to update and the system problem window started to appear sometimes and system is now locking from time to time. I have a i7 Dell notebook and the only thing installed is my ubuntu 17.04  + softwares i use. 

**The ACTUAL SDA config is here: **
[IMG]https://image.ibb.co/dze6Nd/sda_drivers2.png[/IMG]

[IMG]https://ibb.co/nNvP8J[/IMG]

**UPDATE ISSUES **

```
Failed to fetch http://55.archive.ubuntu.com/ubuntu/dists/trusty-security/InRelease  Unable to find expected entry 'restrited/source/Sources' in Release file (Wrong sources.list entry or malformed file)
E: Some index files failed to download. They have been ignored, or old ones used instead.






```

[B]MY SOURCES.LIST 
[/B]
```

 deb cdrom:[Ubuntu 17.04 _Zesty Zapus_ - Release amd64 (20170412)]/ zesty main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://55.archive.ubuntu.com/ubuntu/ trusty main restricted universe multiverse
deb-src http://55.archive.ubuntu.com/ubuntu/ trusty main restricted universe multiverse


## ubuntu update repo 
deb http://55.archive.ubuntu.com/ubuntu trusty-security main restricted universe multiverse
deb http://55.archive.ubuntu.com/ubuntu trusty-updates main restricted universe multiverse
deb-src http://55.archive.ubuntu.com/ubuntu trusty-security main restrited universe multiverse
deb-src htpp://55.archive.ubuntu.com/ubuntu trusty-updates main restricted universe multiverse


## Major bug fix updates produced after the final release of the
## distribution.
# deb http://br.archive.ubuntu.com/ubuntu/ zesty-updates main restricted
# deb-src http://br.archive.ubuntu.com/ubuntu/ zesty-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb http://br.archive.ubuntu.com/ubuntu/ zesty universe
# deb-src http://br.archive.ubuntu.com/ubuntu/ zesty universe
# deb http://br.archive.ubuntu.com/ubuntu/ zesty-updates universe
# deb-src http://br.archive.ubuntu.com/ubuntu/ zesty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb http://br.archive.ubuntu.com/ubuntu/ zesty multiverse
# deb-src http://br.archive.ubuntu.com/ubuntu/ zesty multiverse
# deb http://br.archive.ubuntu.com/ubuntu/ zesty-updates multiverse
# deb-src http://br.archive.ubuntu.com/ubuntu/ zesty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://br.archive.ubuntu.com/ubuntu/ zesty-backports main restricted universe multiverse
# deb-src http://br.archive.ubuntu.com/ubuntu/ zesty-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu zesty partner
# deb-src http://archive.canonical.com/ubuntu zesty partner


# deb http://security.ubuntu.com/ubuntu zesty-security main restricted
# deb-src http://security.ubuntu.com/ubuntu zesty-security main restricted
# deb http://security.ubuntu.com/ubuntu zesty-security universe
# deb-src http://security.ubuntu.com/ubuntu zesty-security universe
# deb http://security.ubuntu.com/ubuntu zesty-security multiverse
# deb-src http://security.ubuntu.com/ubuntu zesty-security multiverse
# deb-src http://archive.canonical.com/ zesty partner







```



Thank you in advance for the help.

---

### Post by deadflowr on 2018-05-30
```
sudo sed -i 's/restrited/restricted/g' /etc/apt/sources.list
```
this will run an in-line replacement for the error.
The error being you forgot to add a c.

I really have no idea what you're doing, as you have both mentions of zesty and trusty in your sources.
And trusty is enabled.
Was this originally 17.04 and you've tried downgrading to 14.04?
Confusing.

Also
> I am always getting a message saying "system problem , report problem"
Does it tell you anything if you click on it?
(Or is it clickable, as in it has an Okay or send button.)

---

### Post by milazg on 2018-05-31
Hello deadflowr thank you for that. such stupid. 

Yes its clickable, its the report system window is the one **generated by the Apport but it asks me my root pass before sending the report. **i want to correct it not only disable it cuz i think this is the problem that is getting me disconnect and locking from time to time but its only a hunch. 

The problem i am getting is with the CUPS package. acessing VAR/CRASH  i can find the report 
```

_usr_sbin_cups-browsed.0.crash


``` 



thank you for the help!

---

### Post by deadflowr on 2018-05-31
It's more likely cups is not the cause but side effect of networking woes.
It crashes because the network is down/wonky.
This gives a fairly reasonable explanation:
[https://askubuntu.com/questions/828315/ubuntu-16-04-has-experienced-an-internal-error-cups-filter-hpps]("https://askubuntu.com/questions/828315/ubuntu-16-04-has-experienced-an-internal-error-cups-filter-hpps")
> The printer driver crashes if it runs into a network problem. To quote the issue description: "As Linux distributions have automatic crash handling/reporting systems this causes annoying pop-ups which irritate the users giving the impression of a more severe problem."

I would think you might look into resetting network manager settings.
(If I'm not mistaken that really means create a new network connection and remove the old one)


I'm still wondering if this was some kind of downgrade from 17.04 to 14.04...

---

