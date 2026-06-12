---
title: "Updates problem"
date: 2011-09-03
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by vpharry on 2011-09-03
I did a partial update. when I tried to update again this came up.[ATTACH]201328[/ATTACH] 
When I checked for the updates through the update manager. This came up [ATTACH]201329[/ATTACH]
It said 
W:Failed to fetch [http://ppa.launchpad.net/alexeftimie/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/alexeftimie/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/alexeftimie/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/alexeftimie/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
So I tried using the terminal but that did not solve the problem. Here is wat I did
varun@Varun:~$ sudo apt-get update
[sudo] password for varun: 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric InRelease                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric InRelease                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates InRelease                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports InRelease                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security InRelease                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release.gpg                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release.gpg                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports Release.gpg                    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free Sources                         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security Release.gpg                     
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Sources                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main amd64 Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release                          
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner amd64 Packages                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports Release                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Sources                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main amd64 Packages                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free amd64 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted amd64 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe amd64 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse amd64 Packages                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main amd64 Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted amd64 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe amd64 Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse amd64 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/main Sources                   
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                    
  404  Not Found
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/restricted Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/universe Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/multiverse Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/main amd64 Packages            
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages                       
  404  Not Found
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/restricted amd64 Packages      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/multiverse amd64 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main amd64 Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted amd64 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe amd64 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse amd64 Packages       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main TranslationIndex                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/main TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/restricted TranslationIndex    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/universe TranslationIndex      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main TranslationIndex           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse TranslationIndex     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe TranslationIndex
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free TranslationIndex
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free TranslationIndex
W: Failed to fetch [http://ppa.launchpad.net/alexeftimie/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/alexeftimie/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/alexeftimie/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/alexeftimie/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


WHAT SHOULD I DO 2 ENABLE UPDATES?

---

### Post by garvinrick4 on 2011-09-03
Open software sources to other software tab in and uncheck mark the offending .ppa's
and then:
```
sudo apt-get update; sudo apt-get upgrade
```

---

### Post by coffeecat on 2011-09-03
> **vpharry said:**
> I did a partial update. 

Don't do partial updates. Read this sticky for the reasons why:

[http://ubuntuforums.org/showthread.php?t=1751299](http://ubuntuforums.org/showthread.php?t=1751299)

While Oneiric is in Beta it is safer to avoid using Update Manager. Install Synaptic and use that for updates. (It's now not in the list of default applications.) Or from the terminal, use:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

The dist-upgrade option does intelligent dependency resolution and is to be preferred during the testing cycle when the repositories are more likely to be inconsistent.

Some testers prefer to install aptitude instead and:

```
sudo aptitude update
sudo aptitude safe-upgrade
```

**EDIT**: oops, missed the PPAs. garvinrick4 is right - disable the PPAs. But don't do partial upgrades - they will cause problems.

---

### Post by garvinrick4 on 2011-09-03
Fix this tab also you have it not to check for updates, in software sources.
As coffee cat posted use command line and do not use partials in update manager in Devolpment release's (oneiric now)

---

### Post by NightwishFan on 2011-09-03
A dist upgrade is probably similar to what the update manager does. You probably just want apt-get upgrade which is the equiv of aptitude safe-upgrade. A dist-upgrade tries to 'break things'. (Good for upgrades to a new version)

Just do not run the partial upgrade and it will only upgrade safe packages.

---

### Post by coffeecat on 2011-09-03
> **NightwishFan said:**
> A dist upgrade is probably similar to what the update manager does. You probably just want apt-get upgrade which is the equiv of aptitude safe-upgrade. A dist-upgrade tries to 'break things'.

So, dist-upgrade tries to "break things". By design? Curious idea. Not in my experience. I find it to be safer than upgrade in the testing period and it is certainly different from what update manager tries to do.

---

### Post by NightwishFan on 2011-09-03
> **coffeecat said:**
> So, dist-upgrade tries to "break things". By design? Curious idea. Not in my experience. I find it to be safer than upgrade in the testing period and it is certainly different from what update manager tries to do.

Well it isn't quite the same method but the difference is one way removes packages the other doesnt. I am not on a rocky system or I would try to test this out and see exactly how the package selection differs.

> **"Apt-Get Man Page]dist-upgrade in addition to performing the function of upgrade,
           also intelligently handles changing dependencies with new versions
           of packages said:**
> So, dist-upgrade
           command may remove some packages.[/U] The /etc/apt/sources.list file
           contains a list of locations from which to retrieve desired package
           files. See also apt_preferences(5) for a mechanism for overriding
           the general settings for individual packages.

---

### Post by coffeecat on 2011-09-03
@NightwishFan, the fact that dist-upgrade occasionally removes packages is not necessarily evidence that it breaks things. The need to remove packages occurs frequently during the testing cycle. Also, the quote from the update-manager manual that you posted (and then edited out!) simply shows that you can run the dist-upgrade option with update-manager if you run update-manager from the command line, not that update-manager routinely runs dist-upgrade when in GUI mode.

Does update-manager run dist-upgrade when it offers to do a partial upgrade? I don't know. All I can say is that in previous testing cycles, when I've compared the list of packages to be removed by Update-Manager's partial upgrade and by dist-upgrade, they have been different. Whereas Synaptic and apt-get dist-upgrade always seem to want to do the same thing. Which makes me think that Synaptic is running dist-upgrade routinely and there seems to be a consensus that using Synaptic for upgrades (during the testing cycle) is safer than using Update-Manager.

Whatever, I hope you can agree that the advice to the OP is two-fold:

1 - Don't allow Update-Manager to do a partial upgrade.

2 - Whatever method you use for upgrading, check which packages are due to be removed and delay the upgrade if you have any doubts.

---

### Post by lucazade on 2011-09-03
@coffeecat
as usual I tend to agree with you ;)

---

### Post by NightwishFan on 2011-09-03
> **coffeecat said:**
> @NightwishFan, the fact that dist-upgrade occasionally removes packages is not necessarily evidence that it breaks things.
Indeed.


> The need to remove packages occurs frequently during the testing cycle.
Obviously.

> Also, the quote from the update-manager manual that you posted (and then edited out!) simply shows that you can run the dist-upgrade option with update-manager if you run update-manager from the command line, not that update-manager routinely runs dist-upgrade when in GUI mode.
I edited it out because it does not do exactly what I assumed so it had no relevence.

> Does update-manager run dist-upgrade when it offers to do a partial upgrade? I don't know.
Of course you don't.

> All I can say is that in previous testing cycles, when I've compared the list of packages to be removed by Update-Manager's partial upgrade and by dist-upgrade, they have been different.
Citation needed.

 > Whereas Synaptic and apt-get dist-upgrade always seem to want to do the same thing. Which makes me think that Synaptic is running dist-upgrade routinely and there seems to be a consensus that using Synaptic for upgrades (during the testing cycle) is safer than using Update-Manager.
I never heard of Synaptic using apt-get.

> Whatever, I hope you can agree that the advice to the OP is two-fold:

1 - Don't allow Update-Manager to do a partial upgrade.

2 - Whatever method you use for upgrading, check which packages are due to be removed and delay the upgrade if you have any doubts.
I agree.

> **lucazade said:**
> @coffeecat
as usual I tend to agree with you ;)
You like being wrong?

---

### Post by lucazade on 2011-09-03
> **NightwishFan said:**
> 
You like being wrong?
 
:-#

---

### Post by coffeecat on 2011-09-03
> **lucazade said:**
> :-#

:)

---

### Post by vpharry on 2011-09-03
Ya i removd d .ppa s causing the problem. Thanks a lot guys. Sorry for the late post. Internet problems.....

---

### Post by jakieahmed on 2011-10-02
> **garvinrick4 said:**
> Fix this tab also you have it not to check for updates, in software sources.
As coffee cat posted use command line and do not use partials in update manager in Devolpment release's (oneiric now)

Your a life saver. It is very strange that those boxes you ticked on attached image are not ticked by default on the ubuntu 11.10

hmm
thanks anyways

---

