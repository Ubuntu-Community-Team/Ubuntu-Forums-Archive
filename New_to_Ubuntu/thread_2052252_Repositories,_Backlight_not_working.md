---
title: "Repositories, Backlight not working"
date: 2012-09-02
forum: New to Ubuntu
---

### Post by 3v3rgr33n on 2012-09-02
Hi

I'm having problems with adjusting my backlight. I use a Samsung RV 510.
I've been googling around and according to a thread at AskUbuntu, I'm supposed to just add "Linux On My samsung" repo and everything will be fine.

I went to the terminal with excitement of actually being able to adjust the brightness; I typed ```
sudo add-apt-repository ppa:voria/ppa
```This is the reply I got from the terminal
```
You are about to add the following PPA to your system:
 Linux On My Samsung
 Official repository of the "Linux On My Samsung" project.
It provides fixed and new packages for a better Ubuntu experience on Samsung laptops.
Visit http://www.voria.org/forum for more informations.
 More info: https://launchpad.net/~voria/+archive/ppa
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.m8xpp8PvBw --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv A6E348801F28F6B59D308A6036960FC31E5F36F0
gpg: requesting key 1E5F36F0 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
```What am i doing wrong, someone please help

---

### Post by 3v3rgr33n on 2012-09-03
Can someone please help, I'm desperate here

---

### Post by nyamina on 2012-09-03
> **3v3rgr33n said:**
> Can someone please help, I'm desperate here
I had problems with the backlight on my old laptop and it drove me up the wall. I actually just added the repository just to see, and it did add okay, so give it a shot again, maybe it was down or something. I actually googled it, and got this webpage [http://www.voria.org/forum/](http://www.voria.org/forum/) so it looks like there's something of a community of people working on Linux on Samsungs. You could give them a shot too.

(I guess I should note that you can't just add a repository, you also have to do a quick ```
sudo apt-get update
``` (you can copy and paste it in to the terminal with ctrl+shift+v to paste it in there) and then install whatever backlight tools they've come up with.)

---

### Post by Toz on 2012-09-03
> gpg: keyserver timed out

Maybe the server was unavailable? I just checked and it appears to be working. Can you try running that command again?

---

### Post by 3v3rgr33n on 2012-09-03
Hi

Thanks for the reply. I tried getting updates again. This is what I got

```
Ign http://ftp.leg.uct.ac.za oneiric InRelease
Ign http://ftp.leg.uct.ac.za oneiric-updates InRelease                
Ign http://ftp.leg.uct.ac.za oneiric-security InRelease               
Ign http://ftp.leg.uct.ac.za oneiric-proposed InRelease                
Ign http://ftp.leg.uct.ac.za oneiric-backports InRelease               
Hit http://ftp.leg.uct.ac.za oneiric Release.gpg                       
Hit http://ftp.leg.uct.ac.za oneiric-updates Release.gpg                       
Hit http://ftp.leg.uct.ac.za oneiric-security Release.gpg                      
Get:1 http://ftp.leg.uct.ac.za oneiric-proposed Release.gpg [198 B]            
Get:2 http://ftp.leg.uct.ac.za oneiric-backports Release.gpg [198 B]           
Hit http://ftp.leg.uct.ac.za oneiric Release                                   
Hit http://ftp.leg.uct.ac.za oneiric-updates Release                           
Hit http://ftp.leg.uct.ac.za oneiric-security Release                          
Get:3 http://ftp.leg.uct.ac.za oneiric-proposed Release [40.8 kB]              
Get:4 http://ftp.leg.uct.ac.za oneiric-backports Release [40.8 kB]             
Hit http://ftp.leg.uct.ac.za oneiric/main Sources                              
Hit http://ftp.leg.uct.ac.za oneiric/restricted Sources                        
Hit http://ftp.leg.uct.ac.za oneiric/multiverse Sources                        
Hit http://ftp.leg.uct.ac.za oneiric/universe Sources                          
Hit http://ftp.leg.uct.ac.za oneiric/main i386 Packages                        
Hit http://ftp.leg.uct.ac.za oneiric/restricted i386 Packages                  
Hit http://ftp.leg.uct.ac.za oneiric/universe i386 Packages                    
Hit http://ftp.leg.uct.ac.za oneiric/multiverse i386 Packages                  
Hit http://ftp.leg.uct.ac.za oneiric/main TranslationIndex                     
Hit http://ftp.leg.uct.ac.za oneiric/multiverse TranslationIndex               
Hit http://ftp.leg.uct.ac.za oneiric/restricted TranslationIndex               
Hit http://ftp.leg.uct.ac.za oneiric/universe TranslationIndex                 
Hit http://ftp.leg.uct.ac.za oneiric-updates/restricted Sources                
Hit http://ftp.leg.uct.ac.za oneiric-updates/main Sources                      
Hit http://ftp.leg.uct.ac.za oneiric-updates/multiverse Sources                
Hit http://ftp.leg.uct.ac.za oneiric-updates/universe Sources                  
Hit http://ftp.leg.uct.ac.za oneiric-updates/main i386 Packages                
Hit http://ftp.leg.uct.ac.za oneiric-updates/restricted i386 Packages          
Hit http://ftp.leg.uct.ac.za oneiric-updates/universe i386 Packages            
Hit http://ftp.leg.uct.ac.za oneiric-updates/multiverse i386 Packages          
Hit http://ftp.leg.uct.ac.za oneiric-updates/main TranslationIndex             
Hit http://ftp.leg.uct.ac.za oneiric-updates/multiverse TranslationIndex       
Hit http://ftp.leg.uct.ac.za oneiric-updates/restricted TranslationIndex       
Hit http://ftp.leg.uct.ac.za oneiric-updates/universe TranslationIndex         
Hit http://ftp.leg.uct.ac.za oneiric-security/restricted Sources               
Hit http://ftp.leg.uct.ac.za oneiric-security/main Sources                     
Hit http://ftp.leg.uct.ac.za oneiric-security/multiverse Sources               
Hit http://ftp.leg.uct.ac.za oneiric-security/universe Sources                 
Hit http://ftp.leg.uct.ac.za oneiric-security/main i386 Packages               
Hit http://ftp.leg.uct.ac.za oneiric-security/restricted i386 Packages         
Hit http://ftp.leg.uct.ac.za oneiric-security/universe i386 Packages           
Hit http://ftp.leg.uct.ac.za oneiric-security/multiverse i386 Packages         
Hit http://ftp.leg.uct.ac.za oneiric-security/main TranslationIndex            
Hit http://ftp.leg.uct.ac.za oneiric-security/multiverse TranslationIndex      
Hit http://ftp.leg.uct.ac.za oneiric-security/restricted TranslationIndex      
Hit http://ftp.leg.uct.ac.za oneiric-security/universe TranslationIndex        
Get:5 http://ftp.leg.uct.ac.za oneiric-proposed/restricted i386 Packages [14 B]
Get:6 http://ftp.leg.uct.ac.za oneiric-proposed/main i386 Packages [157 kB]    
Get:7 http://ftp.leg.uct.ac.za oneiric-proposed/multiverse i386 Packages [1,044 B]
Get:8 http://ftp.leg.uct.ac.za oneiric-proposed/universe i386 Packages [15.8 kB]
Hit http://ftp.leg.uct.ac.za oneiric-proposed/main TranslationIndex            
Hit http://ftp.leg.uct.ac.za oneiric-proposed/multiverse TranslationIndex      
Hit http://ftp.leg.uct.ac.za oneiric-proposed/restricted TranslationIndex      
Hit http://ftp.leg.uct.ac.za oneiric-proposed/universe TranslationIndex        
Get:9 http://ftp.leg.uct.ac.za oneiric-backports/restricted i386 Packages [14 B]
Get:10 http://ftp.leg.uct.ac.za oneiric-backports/main i386 Packages [3,296 B] 
Get:11 http://ftp.leg.uct.ac.za oneiric-backports/multiverse i386 Packages [14 B]
Get:12 http://ftp.leg.uct.ac.za oneiric-backports/universe i386 Packages [13.4 kB]
Hit http://ftp.leg.uct.ac.za oneiric-backports/main TranslationIndex           
Hit http://ftp.leg.uct.ac.za oneiric-backports/multiverse TranslationIndex     
Hit http://ftp.leg.uct.ac.za oneiric-backports/restricted TranslationIndex     
Hit http://ftp.leg.uct.ac.za oneiric-backports/universe TranslationIndex       
Hit http://ftp.leg.uct.ac.za oneiric/main Translation-en                       
Hit http://ftp.leg.uct.ac.za oneiric/multiverse Translation-en                 
Hit http://ftp.leg.uct.ac.za oneiric/restricted Translation-en                 
Hit http://ftp.leg.uct.ac.za oneiric/universe Translation-en                   
Hit http://ftp.leg.uct.ac.za oneiric-updates/main Translation-en               
Hit http://ftp.leg.uct.ac.za oneiric-updates/multiverse Translation-en         
Hit http://ftp.leg.uct.ac.za oneiric-updates/restricted Translation-en         
Hit http://ftp.leg.uct.ac.za oneiric-updates/universe Translation-en           
Hit http://ftp.leg.uct.ac.za oneiric-security/main Translation-en              
Hit http://ftp.leg.uct.ac.za oneiric-security/multiverse Translation-en        
Hit http://ftp.leg.uct.ac.za oneiric-security/restricted Translation-en        
Hit http://ftp.leg.uct.ac.za oneiric-security/universe Translation-en          
Hit http://ftp.leg.uct.ac.za oneiric-proposed/main Translation-en              
Hit http://ftp.leg.uct.ac.za oneiric-proposed/multiverse Translation-en        
Hit http://ftp.leg.uct.ac.za oneiric-proposed/restricted Translation-en        
Hit http://ftp.leg.uct.ac.za oneiric-proposed/universe Translation-en          
Hit http://ftp.leg.uct.ac.za oneiric-backports/main Translation-en             
Hit http://ftp.leg.uct.ac.za oneiric-backports/multiverse Translation-en       
Hit http://ftp.leg.uct.ac.za oneiric-backports/restricted Translation-en       
Hit http://ftp.leg.uct.ac.za oneiric-backports/universe Translation-en         
Err http://ppa.launchpad.net oneiric InRelease                                                                                                        
  
Err http://extras.ubuntu.com oneiric InRelease                                                       
  
Err http://ppa.launchpad.net oneiric InRelease      
  
Err http://ppa.launchpad.net oneiric InRelease      
  
Err http://ppa.launchpad.net oneiric InRelease      
  
Err http://extras.ubuntu.com oneiric Release.gpg    
  Unable to connect to extras.ubuntu.com:http:
Err http://ppa.launchpad.net oneiric Release.gpg
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net oneiric Release.gpg
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net oneiric Release.gpg
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net oneiric Release.gpg
  Unable to connect to ppa.launchpad.net:http:
Fetched 273 kB in 2min 0s (2,264 B/s)
Reading package lists... Done
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/InRelease  

W: Failed to fetch http://ppa.launchpad.net/voria/ppa/ubuntu/dists/oneiric/InRelease  

W: Failed to fetch http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/oneiric/InRelease  

W: Failed to fetch http://ppa.launchpad.net/bisigi/dev/ubuntu/dists/oneiric/InRelease  

W: Failed to fetch http://ppa.launchpad.net/satyajit-happy/themes/ubuntu/dists/oneiric/InRelease  

W: Failed to fetch http://ppa.launchpad.net/voria/ppa/ubuntu/dists/oneiric/Release.gpg  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/Release.gpg  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/oneiric/Release.gpg  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch http://ppa.launchpad.net/bisigi/dev/ubuntu/dists/oneiric/Release.gpg  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch http://ppa.launchpad.net/satyajit-happy/themes/ubuntu/dists/oneiric/Release.gpg  Unable to connect to ppa.launchpad.net:http:

W: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by Toz on 2012-09-03
> Unable to connect to ppa.launchpad.net:http:
Are you behind a proxy?

Can you post back the contents of your /etc/apt/sources.list file and the results of the following command:
```
ls -l /etc/apt/sources.list.d
```

---

### Post by 3v3rgr33n on 2012-09-03
> **Toz said:**
> Are you behind a proxy?


Yes.

This is the output
```
-rw-r--r-- 1 root root 206 2012-08-02 20:12 alecive-antigone-natty.list.distUpgrade
-rw-r--r-- 1 root root 206 2012-08-01 15:25 alecive-antigone-natty.list.save
-rw-r--r-- 1 root root 206 2012-09-04 01:21 alecive-antigone-oneiric.list
-rw-r--r-- 1 root root 206 2012-09-04 01:21 alecive-antigone-oneiric.list.save
-rw-r--r-- 1 root root 204 2012-08-02 20:12 awn-testing-ppa-natty.list.distUpgrade
-rw-r--r-- 1 root root 204 2012-08-01 15:25 awn-testing-ppa-natty.list.save
-rw-r--r-- 1 root root 204 2012-09-04 01:21 awn-testing-ppa-oneiric.list
-rw-r--r-- 1 root root 204 2012-09-04 01:21 awn-testing-ppa-oneiric.list.save
-rw-r--r-- 1 root root 124 2012-09-04 01:21 bisigi-dev-oneiric.list
-rw-r--r-- 1 root root 124 2012-09-04 01:21 bisigi-dev-oneiric.list.save
-rw-r--r-- 1 root root 194 2012-08-02 20:12 bisigi-ppa-natty.list.distUpgrade
-rw-r--r-- 1 root root 194 2012-08-01 15:25 bisigi-ppa-natty.list.save
-rw-r--r-- 1 root root 194 2012-09-04 01:21 bisigi-ppa-oneiric.list
-rw-r--r-- 1 root root 194 2012-09-04 01:21 bisigi-ppa-oneiric.list.save
-rw-r--r-- 1 root root 204 2012-08-02 20:12 deluge-team-ppa-natty.list.distUpgrade
-rw-r--r-- 1 root root 204 2012-08-01 15:25 deluge-team-ppa-natty.list.save
-rw-r--r-- 1 root root 204 2012-09-04 01:21 deluge-team-ppa-oneiric.list
-rw-r--r-- 1 root root 204 2012-09-04 01:21 deluge-team-ppa-oneiric.list.save
-rw-r--r-- 1 root root 215 2012-09-04 01:21 google-talkplugin.list
-rw-r--r-- 1 root root 215 2012-08-02 20:12 google-talkplugin.list.distUpgrade
-rw-r--r-- 1 root root 215 2012-09-04 01:21 google-talkplugin.list.save
-rw-r--r-- 1 root root 222 2012-08-02 20:12 mefrio-g-plymouthmanager-natty.list.distUpgrade
-rw-r--r-- 1 root root 222 2012-08-01 15:25 mefrio-g-plymouthmanager-natty.list.save
-rw-r--r-- 1 root root 222 2012-09-04 01:21 mefrio-g-plymouthmanager-oneiric.list
-rw-r--r-- 1 root root 222 2012-09-04 01:21 mefrio-g-plymouthmanager-oneiric.list.save
-rw-r--r-- 1 root root 214 2012-08-02 20:12 nikount-orta-desktop-natty.list.distUpgrade
-rw-r--r-- 1 root root 214 2012-08-01 15:25 nikount-orta-desktop-natty.list.save
-rw-r--r-- 1 root root 214 2012-09-04 01:21 nikount-orta-desktop-oneiric.list
-rw-r--r-- 1 root root 214 2012-09-04 01:21 nikount-orta-desktop-oneiric.list.save
-rw-r--r-- 1 root root 146 2012-09-04 01:21 satyajit-happy-themes-oneiric.list
-rw-r--r-- 1 root root 146 2012-09-04 01:21 satyajit-happy-themes-oneiric.list.save
-rw-r--r-- 1 root root 202 2012-08-02 20:12 screenlets-ppa-natty.list.distUpgrade
-rw-r--r-- 1 root root 202 2012-08-01 15:25 screenlets-ppa-natty.list.save
-rw-r--r-- 1 root root 202 2012-09-04 01:21 screenlets-ppa-oneiric.list
-rw-r--r-- 1 root root 202 2012-09-04 01:21 screenlets-ppa-oneiric.list.save
-rw-r--r-- 1 root root 212 2012-08-02 20:12 sevenmachines-flash-natty.list.distUpgrade
-rw-r--r-- 1 root root 212 2012-08-01 15:25 sevenmachines-flash-natty.list.save
-rw-r--r-- 1 root root 212 2012-09-04 01:21 sevenmachines-flash-oneiric.list
-rw-r--r-- 1 root root 212 2012-09-04 01:21 sevenmachines-flash-oneiric.list.save
-rw-r--r-- 1 root root 202 2012-08-02 20:12 tiheum-equinox-natty.list.distUpgrade
-rw-r--r-- 1 root root 202 2012-08-01 15:25 tiheum-equinox-natty.list.save
-rw-r--r-- 1 root root 202 2012-09-04 01:21 tiheum-equinox-oneiric.list
-rw-r--r-- 1 root root 202 2012-09-04 01:21 tiheum-equinox-oneiric.list.save
-rw-r--r-- 1 root root 248 2012-08-02 20:12 tualatrix-ppa-natty.list.distUpgrade
-rw-r--r-- 1 root root 248 2012-08-01 15:25 tualatrix-ppa-natty.list.save
-rw-r--r-- 1 root root 248 2012-09-04 01:21 tualatrix-ppa-oneiric.list
-rw-r--r-- 1 root root 248 2012-09-04 01:21 tualatrix-ppa-oneiric.list.save
-rw-r--r-- 1 root root 122 2012-09-04 01:21 voria-ppa-oneiric.list
-rw-r--r-- 1 root root 122 2012-09-04 01:21 voria-ppa-oneiric.list.save
-rw-r--r-- 1 root root 204 2012-08-02 20:12 xorg-edgers-ppa-natty.list.distUpgrade
-rw-r--r-- 1 root root 204 2012-08-01 15:25 xorg-edgers-ppa-natty.list.save
-rw-r--r-- 1 root root 204 2012-09-04 01:21 xorg-edgers-ppa-oneiric.list
-rw-r--r-- 1 root root 204 2012-09-04 01:21 xorg-edgers-ppa-oneiric.list.save

```

---

### Post by 3v3rgr33n on 2012-09-04
...Close to giving up now, I've been patiently waiting for a reply

---

### Post by Toz on 2012-09-04
> ...Close to giving up now, I've been patiently waiting for a reply
ummmm, yeah.

Anyways.....

You're not connecting to the PPAs through your proxy. How have you configured your proxy?

Maybe try this to see if it works:
```
sudo bash
export http_proxy="<your_proxy_info>"
export https_proxy="<your_proxy_info>"
apt-get update

```
...and post back the results of the last command.

*Make sure you change <your_proxy_info> to your actual proxy server info.

---

### Post by 3v3rgr33n on 2012-09-05
I did set the proxy settings through the gui but I did what you said and this is what I got

```
Ign http://ftp.leg.uct.ac.za oneiric InRelease
Ign http://ftp.leg.uct.ac.za oneiric-updates InRelease                                              
Ign http://ftp.leg.uct.ac.za oneiric-security InRelease                                             
Ign http://ftp.leg.uct.ac.za oneiric-proposed InRelease                                                                    
Ign http://ftp.leg.uct.ac.za oneiric-backports InRelease                                                                   
Hit http://ftp.leg.uct.ac.za oneiric Release.gpg                                                     
Hit http://ftp.leg.uct.ac.za oneiric-updates Release.gpg                                                                   
Hit http://ftp.leg.uct.ac.za oneiric-security Release.gpg                                                                  
Hit http://ftp.leg.uct.ac.za oneiric-proposed Release.gpg                                                                  
Hit http://ftp.leg.uct.ac.za oneiric-backports Release.gpg                                                                 
Hit http://ftp.leg.uct.ac.za oneiric Release                                                                               
Hit http://ftp.leg.uct.ac.za oneiric-updates Release                                                                                              
Hit http://ftp.leg.uct.ac.za oneiric-security Release                                                                      
Hit http://ftp.leg.uct.ac.za oneiric-proposed Release                                                                      
Hit http://ftp.leg.uct.ac.za oneiric-backports Release                                                                                            
Hit http://ftp.leg.uct.ac.za oneiric/main Sources                                                                                                 
Hit http://ftp.leg.uct.ac.za oneiric/restricted Sources                                                                                           
Hit http://ftp.leg.uct.ac.za oneiric/multiverse Sources                                                                                           
Hit http://ftp.leg.uct.ac.za oneiric/universe Sources                                                                      
Hit http://ftp.leg.uct.ac.za oneiric/main i386 Packages                                                                    
Hit http://ftp.leg.uct.ac.za oneiric/restricted i386 Packages                                                              
Hit http://ftp.leg.uct.ac.za oneiric/universe i386 Packages                                                                
Hit http://ftp.leg.uct.ac.za oneiric/multiverse i386 Packages                                                              
Hit http://ftp.leg.uct.ac.za oneiric/main TranslationIndex                                                                 
Hit http://ftp.leg.uct.ac.za oneiric/multiverse TranslationIndex                                                           
Hit http://ftp.leg.uct.ac.za oneiric/restricted TranslationIndex                                                           
Hit http://ftp.leg.uct.ac.za oneiric/universe TranslationIndex                                                             
Hit http://ftp.leg.uct.ac.za oneiric-updates/restricted Sources                                      
Hit http://ftp.leg.uct.ac.za oneiric-updates/main Sources                                                                  
Hit http://ftp.leg.uct.ac.za oneiric-updates/multiverse Sources                                                            
Hit http://ftp.leg.uct.ac.za oneiric-updates/universe Sources                                                              
Hit http://ftp.leg.uct.ac.za oneiric-updates/main i386 Packages                                                            
Hit http://ftp.leg.uct.ac.za oneiric-updates/restricted i386 Packages                                                      
Hit http://ftp.leg.uct.ac.za oneiric-updates/universe i386 Packages                                                        
Hit http://ftp.leg.uct.ac.za oneiric-updates/multiverse i386 Packages                                                      
Hit http://ftp.leg.uct.ac.za oneiric-updates/main TranslationIndex                                                         
Hit http://ftp.leg.uct.ac.za oneiric-updates/multiverse TranslationIndex                                                   
Hit http://ftp.leg.uct.ac.za oneiric-updates/restricted TranslationIndex                                                   
Hit http://ftp.leg.uct.ac.za oneiric-updates/universe TranslationIndex                                                     
Hit http://ftp.leg.uct.ac.za oneiric-security/restricted Sources                                                           
Hit http://ftp.leg.uct.ac.za oneiric-security/main Sources                                           
Hit http://ftp.leg.uct.ac.za oneiric-security/multiverse Sources                                                           
Hit http://ftp.leg.uct.ac.za oneiric-security/universe Sources                                                             
Hit http://ftp.leg.uct.ac.za oneiric-security/main i386 Packages                                                           
Hit http://ftp.leg.uct.ac.za oneiric-security/restricted i386 Packages                                                     
Hit http://ftp.leg.uct.ac.za oneiric-security/universe i386 Packages                                                       
Hit http://ftp.leg.uct.ac.za oneiric-security/multiverse i386 Packages                                                     
Hit http://ftp.leg.uct.ac.za oneiric-security/main TranslationIndex                                                        
Hit http://ftp.leg.uct.ac.za oneiric-security/multiverse TranslationIndex                                                  
Hit http://ftp.leg.uct.ac.za oneiric-security/restricted TranslationIndex                                                  
Hit http://ftp.leg.uct.ac.za oneiric-security/universe TranslationIndex                                                    
Hit http://ftp.leg.uct.ac.za oneiric-proposed/restricted i386 Packages                                                     
Hit http://ftp.leg.uct.ac.za oneiric-proposed/main i386 Packages                                                           
Hit http://ftp.leg.uct.ac.za oneiric-proposed/multiverse i386 Packages                                                     
Hit http://ftp.leg.uct.ac.za oneiric-proposed/universe i386 Packages                                                       
Hit http://ftp.leg.uct.ac.za oneiric-proposed/main TranslationIndex                                                        
Hit http://ftp.leg.uct.ac.za oneiric-proposed/multiverse TranslationIndex                                                  
Hit http://ftp.leg.uct.ac.za oneiric-proposed/restricted TranslationIndex                                                  
Hit http://ftp.leg.uct.ac.za oneiric-proposed/universe TranslationIndex                                                    
Hit http://ftp.leg.uct.ac.za oneiric-backports/restricted i386 Packages                                                    
Hit http://ftp.leg.uct.ac.za oneiric-backports/main i386 Packages                                                          
Hit http://ftp.leg.uct.ac.za oneiric-backports/multiverse i386 Packages                                                    
Hit http://ftp.leg.uct.ac.za oneiric-backports/universe i386 Packages                                                      
Hit http://ftp.leg.uct.ac.za oneiric-backports/main TranslationIndex                                                       
Hit http://ftp.leg.uct.ac.za oneiric-backports/multiverse TranslationIndex                                                 
Hit http://ftp.leg.uct.ac.za oneiric-backports/restricted TranslationIndex                                                 
Hit http://ftp.leg.uct.ac.za oneiric-backports/universe TranslationIndex                                                   
Hit http://ftp.leg.uct.ac.za oneiric/main Translation-en                                                                   
Hit http://ftp.leg.uct.ac.za oneiric/multiverse Translation-en                                                             
Hit http://ftp.leg.uct.ac.za oneiric/restricted Translation-en                                                             
Hit http://ftp.leg.uct.ac.za oneiric/universe Translation-en                                                               
Hit http://ftp.leg.uct.ac.za oneiric-updates/main Translation-en                                                           
Hit http://ftp.leg.uct.ac.za oneiric-updates/multiverse Translation-en                                                     
Hit http://ftp.leg.uct.ac.za oneiric-updates/restricted Translation-en                                                     
Hit http://ftp.leg.uct.ac.za oneiric-updates/universe Translation-en                                                       
Hit http://ftp.leg.uct.ac.za oneiric-security/main Translation-en                                                          
Hit http://ftp.leg.uct.ac.za oneiric-security/multiverse Translation-en                                                    
Hit http://ftp.leg.uct.ac.za oneiric-security/restricted Translation-en                                                    
Hit http://ftp.leg.uct.ac.za oneiric-security/universe Translation-en                                                      
Hit http://ftp.leg.uct.ac.za oneiric-proposed/main Translation-en                                                          
Hit http://ftp.leg.uct.ac.za oneiric-proposed/multiverse Translation-en                                                    
Hit http://ftp.leg.uct.ac.za oneiric-proposed/restricted Translation-en                                                    
Hit http://ftp.leg.uct.ac.za oneiric-proposed/universe Translation-en                                                      
Hit http://ftp.leg.uct.ac.za oneiric-backports/main Translation-en                                                         
Hit http://ftp.leg.uct.ac.za oneiric-backports/multiverse Translation-en                                                   
Hit http://ftp.leg.uct.ac.za oneiric-backports/restricted Translation-en                                                   
Hit http://ftp.leg.uct.ac.za oneiric-backports/universe Translation-en                                                     
Err http://extras.ubuntu.com oneiric InRelease                                                                             
  
Err http://ppa.launchpad.net oneiric InRelease                                                       
  
Err http://ppa.launchpad.net oneiric InRelease                                                       
  
Err http://ppa.launchpad.net oneiric InRelease                                                       
  
Err http://ppa.launchpad.net oneiric InRelease                                                       
  
Err http://extras.ubuntu.com oneiric Release.gpg                                                     
  Unable to connect to extras.ubuntu.com:http:
Err http://ppa.launchpad.net oneiric Release.gpg
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net oneiric Release.gpg
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net oneiric Release.gpg
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net oneiric Release.gpg
  Unable to connect to ppa.launchpad.net:http:
Reading package lists... Done
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/InRelease  

W: Failed to fetch http://ppa.launchpad.net/voria/ppa/ubuntu/dists/oneiric/InRelease  

W: Failed to fetch http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/oneiric/InRelease  

W: Failed to fetch http://ppa.launchpad.net/bisigi/dev/ubuntu/dists/oneiric/InRelease  

W: Failed to fetch http://ppa.launchpad.net/satyajit-happy/themes/ubuntu/dists/oneiric/InRelease  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/Release.gpg  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch http://ppa.launchpad.net/voria/ppa/ubuntu/dists/oneiric/Release.gpg  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/oneiric/Release.gpg  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch http://ppa.launchpad.net/bisigi/dev/ubuntu/dists/oneiric/Release.gpg  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch http://ppa.launchpad.net/satyajit-happy/themes/ubuntu/dists/oneiric/Release.gpg  Unable to connect to ppa.launchpad.net:http:

W: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by Toz on 2012-09-05
Can you post back contents of /etc/apt/sources.list and /etc/apt/sources.list.d/tiheum-equinox-oneiric.list?

Whats interesting is that all of the sites that begin with ftp work fine, but the others don't. Do you have any other problems surfing the net? Can you, with your browser, connect to [http://extras.ubuntu.com?](http://extras.ubuntu.com?)

---

### Post by 3v3rgr33n on 2012-09-05
> **Toz said:**
> /etc/apt/sources.list[]("http://extras.ubuntu.com?")

```
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted
deb-src http://ftp.leg.uct.ac.za/ubuntu/ oneiric main restricted #Added by software-properties

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ftp.leg.uct.ac.za/ubuntu/ oneiric main restricted
deb-src http://ftp.leg.uct.ac.za/ubuntu/ oneiric multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ftp.leg.uct.ac.za/ubuntu/ oneiric-updates main restricted
deb-src http://ftp.leg.uct.ac.za/ubuntu/ oneiric-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ftp.leg.uct.ac.za/ubuntu/ oneiric universe
deb http://ftp.leg.uct.ac.za/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ftp.leg.uct.ac.za/ubuntu/ oneiric multiverse
deb http://ftp.leg.uct.ac.za/ubuntu/ oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://za.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://za.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://ftp.leg.uct.ac.za/ubuntu/ oneiric-security main restricted
deb-src http://ftp.leg.uct.ac.za/ubuntu/ oneiric-security restricted main multiverse universe #Added by software-properties
deb http://ftp.leg.uct.ac.za/ubuntu/ oneiric-security universe
deb http://ftp.leg.uct.ac.za/ubuntu/ oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main
deb http://ftp.leg.uct.ac.za/ubuntu/ oneiric-proposed restricted main multiverse universe

#bisigi themes
# deb http://ppa.lauchpad.net/bisigi/ppa/ubuntu oneiric main # disabled on upgrade to oneiric
# deb http://ftp.leg.uct.ac.za/medibuntu oneiric free non-free # disabled on upgrade to oneiric
# deb-src http://ftp.leg.uct.ac.za/medibuntu oneiric free non-free # disabled on upgrade to oneiric
# deb http://ftp.leg.uct.ac.za/medibuntu oneiric free non-free # disabled on upgrade to oneiric
# deb-src http://ftp.leg.uct.ac.za/medibuntu oneiric free non-free # disabled on upgrade to oneiric
deb http://ppa.launchpad.net/voria/ppa/ubuntu oneiric main
deb-src http://ppa.launchpad.net/voria/ppa/ubuntu oneiric main
deb http://ppa.launchpad.net/voria/ppa/ubuntu oneiric main
deb-src http://ppa.launchpad.net/voria/ppa/ubuntu oneiric main
deb http://ppa.launchpad.net/voria/ppa/ubuntu oneiric main
deb-src http://ppa.launchpad.net/voria/ppa/ubuntu oneiric main
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu oneiric main
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu oneiric main
deb http://ftp.leg.uct.ac.za/ubuntu/ oneiric-backports restricted main multiverse universe
```

> **Toz said:**
> 
 /etc/apt/sources.list.d/tiheum-equinox-oneiric.list


```
# deb http://ppa.launchpad.net/tiheum/equinox/ubuntu oneiric main # disabled on upgrade to oneiric
# deb-src http://ppa.launchpad.net/tiheum/equinox/ubuntu oneiric main # disabled on upgrade to oneiric
```

> **Toz said:**
> 
 Do you have any other problems surfing the net? Can you, with your browser, connect to [http://extras.ubuntu.com?](http://extras.ubuntu.com?)


No, I have no problem whatsover accessing the internet and I can connect to the website.

You are getting me worried now

---

### Post by Toz on 2012-09-05
Okay, lets try this. Go to the Software Sources app and on the "Other Software" tab disable (uncheck) all of the sources that are listed. Then run:
```
sudo apt-get update
```
...again and post back the results. 

If there are no errors, go back and start enabling them one at a time and running the update command again to see if and when you get an error.

---

### Post by 3v3rgr33n on 2012-09-05
When I disable them, there are no errors.
I tried enabling just one (The Linux on My Samsung ppa) and this is what I got

```
Err http://ppa.launchpad.net oneiric Release.gpg    
  Unable to connect to ppa.launchpad.net:http:
Reading package lists... Done
W: Failed to fetch http://ppa.launchpad.net/voria/ppa/ubuntu/dists/oneiric/InRelease  

W: Failed to fetch http://ppa.launchpad.net/voria/ppa/ubuntu/dists/oneiric/Release.gpg  Unable to connect to ppa.launchpad.net:http:

W: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by Toz on 2012-09-05
Try deleting it from the Software Sources, then re-add it from the command line again:
```
sudo add-apt-repository ppa:voria/ppa
```

Post back any error messages.

---

### Post by 3v3rgr33n on 2012-09-06
```
You are about to add the following PPA to your system:
 Linux On My Samsung
 Official repository of the "Linux On My Samsung" project.
It provides fixed and new packages for a better Ubuntu experience on Samsung laptops.
Visit http://www.voria.org/forum for more informations.
 More info: https://launchpad.net/~voria/+archive/ppa
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.p7oVkaxQ72 --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv A6E348801F28F6B59D308A6036960FC31E5F36F0
gpg: requesting key 1E5F36F0 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

```

I don't think this will ever be fixed, thnx for your help. I quit

---

### Post by Toz on 2012-09-06
For some reason you are not connecting to the keyserver. Is it possible that your proxy is preventing this connection or do you have a firewall in place that's stopping it?

Maybe try this instead:
```
sudo gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 1E5F36F0
```

---

### Post by 3v3rgr33n on 2012-09-07
I don't have a firewall.

Here's the result from the command
```
gpg: WARNING: unsafe ownership on configuration file `/home/zola/.gnupg/gpg.conf'
gpg: Invalid option "--rec-keys"
```

---

### Post by Toz on 2012-09-08
> gpg: Invalid option "--rec-keys"
You mispelled the parameter. The command should be:
```
sudo gpg --keyserver hkp://keyserver.ubuntu.com:80 --[COLOR="Red"]recv-keys [/COLOR]1E5F36F0
```

---

### Post by raja.genupula on 2012-09-08
you tried with server changing ?

---

### Post by 3v3rgr33n on 2012-09-08
> **Toz said:**
> You mispelled the parameter. The command should be:
```
sudo gpg --keyserver hkp://keyserver.ubuntu.com:80 --[COLOR=Red]recv-keys [/COLOR]1E5F36F0
```
Lol, sorry. I tried entering it correctly this time and the result is almost the same
```
gpg: WARNING: unsafe ownership on configuration file `/home/zola/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
```

> **raja.genupula said:**
> you tried with server changing ?
I was not aware that you can do that, how can I do that?

Thanks
Adeeb

---

### Post by Toz on 2012-09-09
What is the result of the following commands:
```
ls -al ~ | grep gnupg
ls -al ~/.gnupg
```

Maybe try it this way:
```

gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 1E5F36F0
gpg -a --export 1E5F36F0 | sudo apt-key add -
```

---

### Post by 3v3rgr33n on 2012-09-10
```

zola@5R33N:~$ ls -al ~ | grep gnupg
drwx------  3 zola zola      4096 2012-09-08 05:07 .gnupg
zola@5R33N:~$ ls -al ~/.gnupg
total 128
drwx------  3 zola zola  4096 2012-09-08 05:07 .
drwx------ 90 zola zola 24576 2012-09-10 13:05 ..
-rw-r--r--  1 zola zola    50 2012-09-10 13:05 gpg-agent-info-5R33N
-rw-------  1 zola zola  9398 2012-02-20 23:55 gpg.conf
drwx------  2 zola zola  4096 2012-02-21 07:12 private-keys-v1.d
-rw-------  1 zola zola  1770 2012-03-22 23:15 pubring.gpg
-rw-------  1 zola zola  1204 2012-03-22 23:12 pubring.gpg~
-rw-------  1 zola zola   600 2012-03-22 23:15 random_seed
-rw-------  1 zola zola  3837 2012-03-22 23:15 secring.gpg
-rw-------  1 zola zola  1280 2012-03-22 23:12 trustdb.gpg

```

---

### Post by Toz on 2012-09-10
Have you tried the second set of commands?
```
gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 1E5F36F0
gpg -a --export 1E5F36F0 | sudo apt-key add -
```

Then:
```
sudo apt-get update
```
...and post back the results.

---

### Post by 3v3rgr33n on 2012-09-14
> **Toz said:**
> Have you tried the second set of commands? 
```
gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 1E5F36F0 
```

```
zola@5R33N:~$ gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 1E5F36F0gpg: requesting key 1E5F36F0 from hkp server keyserver.ubuntu.com
?: keyserver.ubuntu.com: Connection timed out
gpgkeys: HTTP fetch error 7: couldn't connect: Connection timed out
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

```

```
gpg -a --export 1E5F36F0 | sudo apt-key add -
```Then:

```
zola@5R33N:~$ gpg -a --export 1E5F36F0 | sudo apt-key add -
gpg: WARNING: nothing exported
[sudo] password for zola: 
gpg: no valid OpenPGP data found.
```

---

### Post by Toz on 2012-09-14
> gpgkeys: HTTP fetch error 7: couldn't connect: Connection timed out

You are having problems with your proxy. You should talk to the person who administers the proxy to see why these commands are not going through.

---

### Post by 3v3rgr33n on 2012-10-12
Lol, you were right. It turns out it really was the proxy. Thank you very much for your spirit and assistance.

---

