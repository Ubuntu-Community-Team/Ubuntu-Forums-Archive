---
title: "Cartes du Ceil Installation?"
date: 2017-04-21
forum: New to Ubuntu
---

### Post by Daveski17 on 2017-04-21
Hello,

I tried running this in the Terminal (as in the link below)

sudo apt-add-repository 'deb [http://www.ap-i.net/apt](http://www.ap-i.net/apt) stable main'

but nothing installed. Am I dong something wrong?

Thanks.


Link: [http://www.ap-i.net/skychart/en/documentation/installation_on_linux_ubuntu](http://www.ap-i.net/skychart/en/documentation/installation_on_linux_ubuntu)

---

### Post by howefield on 2017-04-21
Please post the output of 

```
sudo apt update
```

---

### Post by Daveski17 on 2017-04-21
Output..
```
david@Davebuntu:~$ sudo apt update
[sudo] password for david: 
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty InRelease                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates InRelease                      
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports InRelease                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-security InRelease                     
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty Release.gpg                            
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/main Sources                   
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/restricted Sources             
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/universe Sources               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/multiverse Sources             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/main amd64 Packages            
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/restricted amd64 Packages      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/universe amd64 Packages        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_GB                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/main i386 Packages             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/restricted i386 Packages       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/universe i386 Packages      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/multiverse i386 Packages    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/main Translation-en         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/universe Translation-en        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/main Sources                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/restricted Sources        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/universe Sources          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/multiverse Sources           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/main amd64 Packages          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/restricted amd64 Packages 
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/universe amd64 Packages   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages 
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/main i386 Packages        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/restricted i386 Packages  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/multiverse Translation-en
Get:1 [http://www.ap-i.net](http://www.ap-i.net) stable InRelease [2,877 B]                           
Ign [http://www.ap-i.net](http://www.ap-i.net) stable InRelease                                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/universe Translation-en 
Ign [http://www.ap-i.net](http://www.ap-i.net) stable/main amd64 Packages/DiffIndex              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty Release                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-security/main Sources                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-security/restricted Sources       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-security/universe Sources         
Ign [http://www.ap-i.net](http://www.ap-i.net) stable/main i386 Packages/DiffIndex               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-security/multiverse Sources       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-security/main amd64 Packages      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-security/restricted amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-security/universe amd64 Packages       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-security/multiverse amd64 Packages     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-security/main i386 Packages       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-security/restricted i386 Packages 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-security/universe i386 Packages   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-security/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-security/main Translation-en     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-security/multiverse Translation-en     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-security/restricted Translation-en     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-security/universe Translation-en       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main Sources                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe Sources            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse Sources          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main amd64 Packages         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted amd64 Packages   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe amd64 Packages     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse amd64 Packages   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main i386 Packages          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted i386 Packages  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse i386 Packages               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main Translation-en               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse Translation-en_GB      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted Translation-en_GB      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted Translation-en         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe Translation-en_GB        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe Translation-en                
Hit [http://www.ap-i.net](http://www.ap-i.net) stable/main amd64 Packages                             
Hit [http://www.ap-i.net](http://www.ap-i.net) stable/main i386 Packages
Ign [http://www.ap-i.net](http://www.ap-i.net) stable/main Translation-en_GB
Ign [http://www.ap-i.net](http://www.ap-i.net) stable/main Translation-en
Fetched 2,877 B in 3s (721 B/s) 
Reading package lists... Done
W: GPG error: [http://www.ap-i.net](http://www.ap-i.net) stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8B8B57C1AA716FC2
david@Davebuntu:~$
```

---

### Post by howefield on 2017-04-21
Use this command in terminal..

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8B8B57C1AA716FC2
```

Press enter, let it do its things and then do another

```
sudo apt-get update
```

does the update complete without error this time ?

---

### Post by Daveski17 on 2017-04-21
> **howefield said:**
> Use this command in terminal..

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8B8B57C1AA716FC2
```

Press enter, let it do its things and then do another

```
sudo apt-get update
```

does the update complete without error this time ?

There's no error now. Thanks. I've tried to install again but no success.

---

### Post by howefield on 2017-04-21
So what's the name of the package that you want from that source, is it skychart ?

It is contained in the source..
```
apt-cache policy skychart
skychart:
  Installed: (none)
  Candidate: 4.0-3575b
  Version table:
     4.0-3575b 500
        500 http://www.ap-i.net/apt stable/main amd64 Packages
```
and appears to install just fine..
```
sudo apt install -s skychart
[sudo] password for hugh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  espeak espeak-data indi-bin libcfitsio5 libespeak1 libgsl2 libindi-data libindi-plugins libindialignmentdriver1 libindidriver1
  libnova-0.16-0 libpango1.0-0 libpangox-1.0-0 libpasastro skychart-data-dso skychart-data-pictures skychart-data-stars xplanet
  xplanet-images
Suggested packages:
  gsl-ref-psdoc | gsl-doc-pdf | gsl-doc-info | gsl-ref-html
Recommended packages:
  indistarter
The following NEW packages will be installed
  espeak espeak-data indi-bin libcfitsio5 libespeak1 libgsl2 libindi-data libindi-plugins libindialignmentdriver1 libindidriver1
  libnova-0.16-0 libpango1.0-0 libpangox-1.0-0 libpasastro skychart skychart-data-dso skychart-data-pictures skychart-data-stars xplanet
  xplanet-images
0 to upgrade, 20 to newly install, 0 to remove and 14 not to upgrade.
Inst libpangox-1.0-0 (0.0.2-5 Ubuntu:17.04/zesty [amd64])
Inst espeak-data (1.48.04+dfsg-5 Ubuntu:17.04/zesty [amd64])
Inst libespeak1 (1.48.04+dfsg-5 Ubuntu:17.04/zesty [amd64])
Inst espeak (1.48.04+dfsg-5 Ubuntu:17.04/zesty [amd64])
Inst libindi-data (1.2.0-2~ubuntu4 Ubuntu:17.04/zesty [all])
Inst libcfitsio5 (3.410-1 Ubuntu:17.04/zesty [amd64])
Inst libnova-0.16-0 (0.16-2 Ubuntu:17.04/zesty [amd64])
Inst libindidriver1 (1.2.0-2~ubuntu4 Ubuntu:17.04/zesty [amd64])
Inst libindi-plugins (1.2.0-2~ubuntu4 Ubuntu:17.04/zesty [amd64])
Inst libgsl2 (2.3+dfsg-1 Ubuntu:17.04/zesty [amd64])
Inst libindialignmentdriver1 (1.2.0-2~ubuntu4 Ubuntu:17.04/zesty [amd64])
Inst indi-bin (1.2.0-2~ubuntu4 Ubuntu:17.04/zesty [amd64])
Inst libpango1.0-0 (1.40.4-1 Ubuntu:17.04/zesty [amd64])
Inst libpasastro (1.1-14 ap-i.net:www.ap-i.net [amd64])
Inst xplanet (1.3.0-4 Ubuntu:17.04/zesty [amd64])
Inst skychart (4.0-3575b ap-i.net:www.ap-i.net [amd64])
Inst skychart-data-dso (4.0-3431 ap-i.net:www.ap-i.net [all])
Inst skychart-data-pictures (4.0-3421 ap-i.net:www.ap-i.net [all])
Inst skychart-data-stars (4.0-3421 ap-i.net:www.ap-i.net [all])
Inst xplanet-images (1.3.0-4 Ubuntu:17.04/zesty [all])
Conf libpangox-1.0-0 (0.0.2-5 Ubuntu:17.04/zesty [amd64])
Conf espeak-data (1.48.04+dfsg-5 Ubuntu:17.04/zesty [amd64])
Conf libespeak1 (1.48.04+dfsg-5 Ubuntu:17.04/zesty [amd64])
Conf espeak (1.48.04+dfsg-5 Ubuntu:17.04/zesty [amd64])
Conf libindi-data (1.2.0-2~ubuntu4 Ubuntu:17.04/zesty [all])
Conf libcfitsio5 (3.410-1 Ubuntu:17.04/zesty [amd64])
Conf libnova-0.16-0 (0.16-2 Ubuntu:17.04/zesty [amd64])
Conf libindidriver1 (1.2.0-2~ubuntu4 Ubuntu:17.04/zesty [amd64])
Conf libindi-plugins (1.2.0-2~ubuntu4 Ubuntu:17.04/zesty [amd64])
Conf libgsl2 (2.3+dfsg-1 Ubuntu:17.04/zesty [amd64])
Conf libindialignmentdriver1 (1.2.0-2~ubuntu4 Ubuntu:17.04/zesty [amd64])
Conf indi-bin (1.2.0-2~ubuntu4 Ubuntu:17.04/zesty [amd64])
Conf libpango1.0-0 (1.40.4-1 Ubuntu:17.04/zesty [amd64])
Conf libpasastro (1.1-14 ap-i.net:www.ap-i.net [amd64])
Conf xplanet (1.3.0-4 Ubuntu:17.04/zesty [amd64])
Conf skychart (4.0-3575b ap-i.net:www.ap-i.net [amd64])
Conf skychart-data-dso (4.0-3431 ap-i.net:www.ap-i.net [all])
Conf skychart-data-pictures (4.0-3421 ap-i.net:www.ap-i.net [all])
Conf skychart-data-stars (4.0-3421 ap-i.net:www.ap-i.net [all])
Conf xplanet-images (1.3.0-4 Ubuntu:17.04/zesty [all])
```

---

### Post by Daveski17 on 2017-04-21
Yes, Skychart aka Cartes du Ceil. I don't know why it isn't running for me. I installed it on my old computer (I don't now have) that ran Trusty.

---

### Post by howefield on 2017-04-21
> **Daveski17 said:**
> Yes, Skychart aka Cartes du Ceil. I don't know why it isn't running for me. I installed it on my old computer (I don't now have) that ran Trusty.

Well, first thing is to check it is there.. run (if you haven't already done it)

```
apt-cache policy skychart
```

and post the output, thanks.

---

### Post by Daveski17 on 2017-04-21
```
david@Davebuntu:~$ apt-cache policy skychart
skychart:
  Installed: (none)
  Candidate: 4.0-3575b
  Version table:
     4.0-3575b 0
        500 [http://www.ap-i.net/apt/](http://www.ap-i.net/apt/) stable/main amd64 Packages
david@Davebuntu:~$ 
```

I'm pretty sure it isn't there.

---

### Post by howefield on 2017-04-21
> **Daveski17 said:**
> I'm pretty sure it isn't there.

Well, it is, the output from apt-cache is telling you that you don't have it installed but that there is a version available. Were it not available to install there would be no entry against the Candidate field.

So, what's the output of..

```
sudo apt-get install skychart
```

---

### Post by Daveski17 on 2017-04-21
OK thanks, it's installed. I'd post a screenshot but PhotoBucket are in a maintenance cycle. Thanks for all the help. If I wish to uninstall it what sudo command will I need?

---

### Post by howefield on 2017-04-21
> **Daveski17 said:**
> OK thanks, it's installed. I'd post a screenshot but PhotoBucket are in a maintenance cycle. Thanks for all the help. If I wish to uninstall it what sudo command will I need?

Cool, feel free to mark the thread as solved.

To simply uninstall the application you could use..

```
sudo apt-get remove skychart
```

or use the purge option to also remove application configuration files..

```
sudo apt-get purge skychart
```

---

### Post by Daveski17 on 2017-04-21
Excellent, thanks for all the help.

---

### Post by vasa1 on 2017-04-21
> **Daveski17 said:**
> ... I'd post a screenshot but PhotoBucket are in a maintenance cycle. ...
There were problems a few months ago, but now the forum's image attachment facility is working properly.

If you don't see the paperclip icon, click on *Go Advanced* below the posting area.

---

### Post by Daveski17 on 2017-04-22
> **vasa1 said:**
> There were problems a few months ago, but now the forum's image attachment facility is working properly.

If you don't see the paperclip icon, click on *Go Advanced* below the posting area.

OK thanks Vasa.

[ATTACH=CONFIG]274702[/ATTACH]

---

