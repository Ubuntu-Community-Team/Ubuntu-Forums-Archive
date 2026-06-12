---
title: "unable to open Synaptic Manager"
date: 2012-02-20
forum: New to Ubuntu
---

### Post by leilton on 2012-02-20
I am sorry to seem to be always on line asking for help.   I do try my upmost to find solutions before I ask here.

I see this has been asked before, but cannot find where the answer was supplied.

I cannot get Synaptic Manager to open.   I know it has been loaded, because if I go to Software Centre, it shows it installed, but when I select it to open, nothing happens.

Any help appreciated, and again sorry to always seem to be here with problems.

:confused:

---

### Post by arochester on 2012-02-20
You can only use one Package Manager at time e.g. dpkg, apt, aptitude, synaptic, gdebi, software center.

Make sure, as far a possible, that everything is closed first - then try synaptic

---

### Post by ajgreeny on 2012-02-20
> **arochester said:**
> You can only use one Package Manager at time e.g. dpkg, apt, aptitude, synaptic, gdebi, software center.

Make sure, as far a possible, that everything is closed first - then try synaptic
That does not usually stop it opening; it just stops you using it to install anything, etc etc.

@OP  Make sure that the update-manager is not running in the background, which used to be a problem, and if necessary try ```
sudo apt-get purge synaptic
```followed by ```
sudo apt-get install synaptic
```

---

### Post by leilton on 2012-02-20
> **arochester said:**
> You can only use one Package Manager at time e.g. dpkg, apt, aptitude, synaptic, gdebi, software center.

Make sure, as far a possible, that everything is closed first - then try synaptic

Sorry, did not make myself very clear.   Only checked with Software Centre to ensure that Synaptic was loaded, had nothing else running.

Have followed suggestion by ajgreeny, and that has not worked either.

Would it help if I was to remove Lubuntu, (have Kubuntu on Laptop I have both, backing up each other), but not sure if you just remove or remove completely?

Bit of a pain ain't I

---

### Post by leilton on 2012-02-20
> **ajgreeny said:**
> That does not usually stop it opening; it just stops you using it to install anything, etc etc.

@OP  Make sure that the update-manager is not running in the background, which used to be a problem, and if necessary try ```
sudo apt-get purge synaptic
```followed by ```
sudo apt-get install synaptic
```
Thank you for that.   As you will see from my reply above, that did not work.

Waiting on advise re completely removing and then reinstalling same.

---

### Post by arochester on 2012-02-20
If you open a Terminal and issue the commands: > sudo apt-get update 
sudo apt-get upgradeWhat messages do you get?

---

### Post by philinux on 2012-02-20
> **leilton said:**
> I am sorry to seem to be always on line asking for help.   I do try my upmost to find solutions before I ask here.

I see this has been asked before, but cannot find where the answer was supplied.

I cannot get Synaptic Manager to open.   I know it has been loaded, because if I go to Software Centre, it shows it installed, but when I select it to open, nothing happens.

Any help appreciated, and again sorry to always seem to be here with problems.

:confused:

Open a terminal and use 

```
gksu synaptic
```

Are any errors produced.

---

### Post by leilton on 2012-02-20
> **arochester said:**
> If you open a Terminal and issue the commands: What messages do you get?
e
[sudo] password for edward: 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric InRelease
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_GB
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates InRelease
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-backports InRelease
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric Release.gpg                           
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates Release.gpg                   
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-backports Release.gpg                 
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric Release                               
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates Release
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-backports Release
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/main Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/restricted Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/universe Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/multiverse Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/main i386 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/restricted i386 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/universe i386 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/multiverse i386 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/main TranslationIndex
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/multiverse TranslationIndex
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/restricted TranslationIndex
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/universe TranslationIndex
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates/main Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates/restricted Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates/universe Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates/multiverse Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates/main i386 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates/restricted i386 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates/universe i386 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates/main TranslationIndex
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates/universe TranslationIndex
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-backports/main Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-backports/restricted Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-backports/universe Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-backports/multiverse Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-backports/main i386 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-backports/restricted i386 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-backports/universe i386 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-backports/main TranslationIndex
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-backports/universe TranslationIndex
Get:2 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/main Translation-en_GB [69.0 kB]
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/main Translation-en
Get:3 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/multiverse Translation-en_GB [68.5 kB]
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/multiverse Translation-en             
Get:4 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/restricted Translation-en_GB [1,937 B]
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/restricted Translation-en             
Get:5 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/universe Translation-en_GB [4,365 B]
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/universe Translation-en               
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates/main Translation-en           
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates/multiverse Translation-en     
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates/restricted Translation-en     
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates/universe Translation-en       
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-backports/main Translation-en
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-backports/multiverse Translation-en
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-backports/restricted Translation-en
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-backports/universe Translation-en
Fetched 144 kB in 2min 28s (972 B/s)
Reading package lists... Done
edward@edward:~$ 

That is from get update

edward@edward:~$ sudo apt-get upgrade
[sudo] password for edward: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
edward@edward:~$ 

That is from upgrade

Does that help?

---

### Post by leilton on 2012-02-20
> **philinux said:**
> Open a terminal and use 

```
gksu synaptic
```

Are any errors produced.
Hi,

No just took me directly to Synaptic.

Any help?

---

### Post by Penguin360 on 2012-02-20
> **leilton said:**
> Hi,

No [COLOR=Red]just took me directly to Synaptic.[/COLOR]

Any help?

Does it mean it opened Synaptic Manager?

---

### Post by leilton on 2012-02-20
> **CodingBeaver said:**
> Does it mean it opened Synaptic Manager?
Hi

Very sorry, yes should have said went directly to Synaptic Manager.

My apologies.

Does this mean I have to do this each time I want to open the Package Manager?

---

