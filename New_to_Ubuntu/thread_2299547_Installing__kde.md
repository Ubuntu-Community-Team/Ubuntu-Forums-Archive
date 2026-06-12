---
title: "Installing  kde"
date: 2015-10-19
forum: New to Ubuntu
---

### Post by Hakan__Venderlof on 2015-10-19
Hello
I am trying  to install kde  from  gnome  15.4-


i did
sudo apt-get update
sudo apt-get install kubuntu-deskto

and this was returned:


```
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) vivid InRelease
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) vivid-updates InRelease                      
Hit [http://archive.canonical.com](http://archive.canonical.com) vivid InRelease                              
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) vivid-backports InRelease                    
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) vivid-proposed InRelease                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security InRelease                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) vivid InRelease                                  
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) vivid/main Sources                     
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) vivid/restricted Sources                     
Hit [http://archive.canonical.com](http://archive.canonical.com) vivid/partner Sources                        
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) vivid/multiverse Sources           
Hit [http://archive.canonical.com](http://archive.canonical.com) vivid/partner i386 Packages                  
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) vivid/main i386 Packages                     
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) vivid/restricted i386 Packages               
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) vivid/multiverse i386 Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/main Sources                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) vivid/main i386 Packages                         
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) vivid/main Translation-en                    
Ign [http://archive.canonical.com](http://archive.canonical.com) vivid/partner Translation-en                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) vivid/main Translation-en                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/restricted Sources              
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) vivid/multiverse Translation-en  
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) vivid/restricted Translation-en  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/multiverse Sources  
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) vivid-updates/main Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/main i386 Packages  
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) vivid-updates/restricted Sources 
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) vivid-updates/multiverse Sources 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/restricted i386 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) vivid-updates/main i386 Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/multiverse i386 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) vivid-updates/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/multiverse Translation-en
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) vivid-updates/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/restricted Translation-en
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) vivid-updates/main Translation-en  
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) vivid-updates/multiverse Translation-en
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) vivid-updates/restricted Translation-en
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) vivid-backports/main Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) vivid-backports/restricted Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) vivid-backports/multiverse Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) vivid-backports/main i386 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) vivid-backports/restricted i386 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) vivid-backports/multiverse i386 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) vivid-backports/main Translation-en
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) vivid-backports/multiverse Translation-en
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) vivid-backports/restricted Translation-en
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) vivid-proposed/multiverse i386 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) vivid-proposed/main i386 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) vivid-proposed/restricted i386 Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) vivid-proposed/main Translation-en
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) vivid-proposed/multiverse Translation-en
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) vivid-proposed/restricted Translation-en
Reading package lists
```



I am not sure what all that means lol....
what is next step?


greeting   zdubair

---

### Post by vasa1 on 2015-10-19
Please don't post partial output.

And include the commands you issued to generate the output. There's nothing like "kubuntu-deskto". Typing correctly in the terminal is important.

---

### Post by deadflowr on 2015-10-19
What does it mean?

The output you posted is the output of your systems connection to the Ubuntu repository archives.
The archives get updated everyday, and so should you too, or else you can end of with mismatching package listing, which in turn can cause upgrade and installation errors.

But...
two things.

+1 to posting the full output.

and,
Please open an app called Software and Updates.
In software and updates, go to the tab marked Updates.
In the Updates tab uncheck the Box for the *Pre-Release* Updates.
And then close the software and updates window; it should automatic run an updater when you close.

(Those are unstable packages which still need testing.)
You can almost guarantee eventual system breakage when that is enabled.

---

### Post by SeijiSensei on 2015-10-19
If you have enough room on your hard drive, I'd just install Kubuntu 14.04LTS alongside regular Ubuntu.  If you create a separate partition for /home, you can share it between the two installations.

---

### Post by NathanRodriguez on 2015-10-20
Beware of mixing DE's like Gnome and KDE, unfortunately they could conflict.

---

