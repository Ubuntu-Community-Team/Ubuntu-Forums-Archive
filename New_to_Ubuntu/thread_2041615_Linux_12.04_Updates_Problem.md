---
title: "Linux 12.04 Updates Problem"
date: 2012-08-13
forum: New to Ubuntu
---

### Post by hithamalkashif on 2012-08-13
Hi , i'm new to Ubuntu Linux and i searched for the problem for 5-6 days and couldn't found the solution.

My result in Terminal when i set the update code 

- Sudo apt-get update 


[PHP]

hithamalkashif@hithamalkashif-HP-ProBook-4520s:~$ sudo su
[sudo] password for hithamalkashif: 
root@hithamalkashif-HP-ProBook-4520s:/home/hithamalkashif# sudo apt-get update
Ign http://extras.ubuntu.com quantal InRelease
Ign http://us.archive.ubuntu.com quantal InRelease                             
Ign http://ppa.launchpad.net precise InRelease                                 
Hit http://extras.ubuntu.com quantal Release.gpg                               
Ign http://archive.canonical.com oneiric InRelease                   
Ign http://ppa.launchpad.net quantal InRelease                       
Hit http://extras.ubuntu.com quantal Release                         
Ign http://us.archive.ubuntu.com quantal-updates InRelease                     
Hit http://archive.canonical.com oneiric Release.gpg                           
Ign http://ppa.launchpad.net quantal InRelease                       
Hit http://extras.ubuntu.com quantal/main Sources                    
Hit http://archive.canonical.com oneiric Release                     
Ign http://us.archive.ubuntu.com quantal-backports InRelease                   
Ign http://ppa.launchpad.net quantal InRelease                       
Hit http://extras.ubuntu.com quantal/main i386 Packages              
Hit http://archive.canonical.com oneiric/partner Sources                       
Ign http://ppa.launchpad.net quantal InRelease                                 
Ign http://us.archive.ubuntu.com quantal-security InRelease          
Hit http://archive.canonical.com oneiric/partner i386 Packages       
Ign http://ppa.launchpad.net quantal InRelease                       
Hit http://ppa.launchpad.net precise Release.gpg                     
Ign http://us.archive.ubuntu.com quantal-proposed InRelease          
Hit http://ppa.launchpad.net quantal Release.gpg                     
Hit http://us.archive.ubuntu.com quantal Release.gpg                 
Ign http://ppa.launchpad.net quantal Release.gpg                     
Hit http://ppa.launchpad.net quantal Release.gpg                     
Hit http://us.archive.ubuntu.com quantal-updates Release.gpg         
Ign http://ppa.launchpad.net quantal Release.gpg                               
Hit http://us.archive.ubuntu.com quantal-backports Release.gpg                 
Ign http://ppa.launchpad.net quantal Release.gpg                     
Hit http://ppa.launchpad.net precise Release                         
Ign http://extras.ubuntu.com quantal/main Translation-en_US                    
Hit http://us.archive.ubuntu.com quantal-security Release.gpg                  
Hit http://ppa.launchpad.net quantal Release                         
Ign http://extras.ubuntu.com quantal/main Translation-en                       
Ign http://archive.canonical.com oneiric/partner Translation-en_US             
Ign http://ppa.launchpad.net quantal Release                         
Hit http://us.archive.ubuntu.com quantal-proposed Release.gpg
Ign http://archive.canonical.com oneiric/partner Translation-en
Hit http://ppa.launchpad.net quantal Release   
Hit http://us.archive.ubuntu.com quantal Release                      
Ign http://ppa.launchpad.net quantal Release                          
Ign http://ppa.launchpad.net quantal Release   
Hit http://us.archive.ubuntu.com quantal-updates Release
Hit http://us.archive.ubuntu.com quantal-backports Release            
Hit http://ppa.launchpad.net precise/main Sources                     
Hit http://ppa.launchpad.net precise/main i386 Packages               
Hit http://us.archive.ubuntu.com quantal-security Release
Hit http://us.archive.ubuntu.com quantal-proposed Release             
Hit http://ppa.launchpad.net quantal/main Sources                     
Hit http://us.archive.ubuntu.com quantal/restricted Sources
Hit http://ppa.launchpad.net quantal/main i386 Packages
Hit http://us.archive.ubuntu.com quantal/main Sources
Hit http://us.archive.ubuntu.com quantal/multiverse Sources
Hit http://us.archive.ubuntu.com quantal/universe Sources
Hit http://ppa.launchpad.net quantal/main Sources
Hit http://us.archive.ubuntu.com quantal/main i386 Packages
Hit http://ppa.launchpad.net quantal/main i386 Packages
Hit http://us.archive.ubuntu.com quantal/restricted i386 Packages
Hit http://us.archive.ubuntu.com quantal/universe i386 Packages
Hit http://us.archive.ubuntu.com quantal/multiverse i386 Packages
Hit http://us.archive.ubuntu.com quantal/main Translation-en
Hit http://us.archive.ubuntu.com quantal/multiverse Translation-en
Hit http://us.archive.ubuntu.com quantal/restricted Translation-en
Hit http://us.archive.ubuntu.com quantal/universe Translation-en
Hit http://us.archive.ubuntu.com quantal-updates/restricted Sources
Hit http://us.archive.ubuntu.com quantal-updates/main Sources
Hit http://us.archive.ubuntu.com quantal-updates/multiverse Sources
Hit http://us.archive.ubuntu.com quantal-updates/universe Sources
Hit http://us.archive.ubuntu.com quantal-updates/main i386 Packages
Hit http://us.archive.ubuntu.com quantal-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com quantal-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com quantal-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com quantal-updates/main Translation-en
Hit http://us.archive.ubuntu.com quantal-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com quantal-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com quantal-updates/universe Translation-en
Hit http://us.archive.ubuntu.com quantal-backports/main Sources
Hit http://us.archive.ubuntu.com quantal-backports/restricted Sources
Hit http://us.archive.ubuntu.com quantal-backports/universe Sources
Hit http://us.archive.ubuntu.com quantal-backports/multiverse Sources
Hit http://us.archive.ubuntu.com quantal-backports/main i386 Packages
Hit http://us.archive.ubuntu.com quantal-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com quantal-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com quantal-backports/multiverse i386 Packages
Ign http://ppa.launchpad.net precise/main Translation-en_US
Hit http://us.archive.ubuntu.com quantal-backports/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Hit http://us.archive.ubuntu.com quantal-backports/multiverse Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en
Err http://ppa.launchpad.net quantal/main Sources
  404  Not Found
Err http://ppa.launchpad.net quantal/main i386 Packages
  404  Not Found
Hit http://us.archive.ubuntu.com quantal-backports/restricted Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Hit http://us.archive.ubuntu.com quantal-backports/universe Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en
Hit http://us.archive.ubuntu.com quantal-security/restricted Sources
Err http://ppa.launchpad.net quantal/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Hit http://us.archive.ubuntu.com quantal-security/main Sources
Ign http://ppa.launchpad.net quantal/main Translation-en
Hit http://us.archive.ubuntu.com quantal-security/multiverse Sources
Err http://ppa.launchpad.net quantal/main Sources
  404  Not Found
Err http://ppa.launchpad.net quantal/main i386 Packages
  404  Not Found
Hit http://us.archive.ubuntu.com quantal-security/universe Sources
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Hit http://us.archive.ubuntu.com quantal-security/main i386 Packages
Hit http://us.archive.ubuntu.com quantal-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com quantal-security/universe i386 Packages
Hit http://us.archive.ubuntu.com quantal-security/multiverse i386 Packages
Hit http://us.archive.ubuntu.com quantal-security/main Translation-en
Hit http://us.archive.ubuntu.com quantal-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com quantal-security/restricted Translation-en
Hit http://us.archive.ubuntu.com quantal-security/universe Translation-en
Hit http://us.archive.ubuntu.com quantal-proposed/restricted Sources
Hit http://us.archive.ubuntu.com quantal-proposed/main Sources
Hit http://us.archive.ubuntu.com quantal-proposed/multiverse Sources
Hit http://us.archive.ubuntu.com quantal-proposed/universe Sources
Hit http://us.archive.ubuntu.com quantal-proposed/restricted i386 Packages
Hit http://us.archive.ubuntu.com quantal-proposed/main i386 Packages
Hit http://us.archive.ubuntu.com quantal-proposed/multiverse i386 Packages
Hit http://us.archive.ubuntu.com quantal-proposed/universe i386 Packages
Hit http://us.archive.ubuntu.com quantal-proposed/main Translation-en
Hit http://us.archive.ubuntu.com quantal-proposed/multiverse Translation-en
Hit http://us.archive.ubuntu.com quantal-proposed/restricted Translation-en
Hit http://us.archive.ubuntu.com quantal-proposed/universe Translation-en
Ign http://us.archive.ubuntu.com quantal/main Translation-en_US
Ign http://us.archive.ubuntu.com quantal/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com quantal/restricted Translation-en_US
Ign http://us.archive.ubuntu.com quantal/universe Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com quantal-security/main Translation-en_US
Ign http://us.archive.ubuntu.com quantal-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com quantal-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com quantal-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com quantal-proposed/main Translation-en_US
Ign http://us.archive.ubuntu.com quantal-proposed/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com quantal-proposed/restricted Translation-en_US
Ign http://us.archive.ubuntu.com quantal-proposed/universe Translation-en_US
W: Failed to fetch http://ppa.launchpad.net/satyajit-happy/themes/ubuntu/dists/quantal/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/satyajit-happy/themes/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/upubuntu-com/gnome3/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/webupd8team/gnome3/ubuntu/dists/quantal/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/webupd8team/gnome3/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

[/PHP]

---

### Post by NikTh on 2012-08-13
Hi , 
first of all , this is not 12.04 (Presice) , but 12.10 (quantal). 
Ubuntu 12.10 is on development state and early development state (Alpha version) that means no support can be stable. 
These problems I can see you have , are from external repositories. You must open the software sources , and remove ALL the repositories you have in there. 
From terminal 
```
gksudo software-properties-gtk
``` go to "Other Software" and remove ALL external PPAs . (those PPAs you added by your self)

I assume you did a mistake or something and you upgrade to 12.10 ? 
or for some reason , you had mix up the Official repositories from Percise (12.04) with Quantal(12.10). 
If you want to clear up the repos and go back to primary state , tell us.
I don't know if you are able now to downgrade to 12.04 , but we can remove all sources.list and replace them with Official sources of 12.04 and... will see.
Thanks

---

### Post by hithamalkashif on 2012-08-13
i think i did the Upgrade to 12.10 i was on 11.10 

thanks i want to go back to 12.04 , i don't know how and the CD i have is 11.10 

anyway this is a print screen to the my software sources 

[IMG]http://i47.tinypic.com/21lmws9.png[/IMG]

---

### Post by 2F4U on 2012-08-13
My understanding is that you can't downgrade from 12.10 to 12.04, so you would have to do a fresh installation.

---

### Post by NikTh on 2012-08-13
> **2F4U said:**
> My understanding is that you can't downgrade from 12.10 to 12.04, so you would have to do a fresh installation.
Hi,
Yes , I have to agree with that. 

OP you can try below commands and see what happen. 

```
sudo wget "http://pastebin.com/raw.php?i=aDE6mdsP" -O /etc/apt/sources.list 
sudo rm /etc/apt/sources.list.d/*.list 
sudo apt-get update ; sudo apt-get dist-upgrade
``` 

**Warning**: Above commands will delete all your sources.list file and replace it with Original Ubuntu from U.S server. Also will delete all of your repositories and last command will attempt to do an upgrade with new repositories. (of 12.04)

The most probably thing  is to stack with packages from 12.10 , but you have nothing to lose if you try. 

My suggest is to backup all your important data and prepare for a new installation of 12.04.
Thanks

---

