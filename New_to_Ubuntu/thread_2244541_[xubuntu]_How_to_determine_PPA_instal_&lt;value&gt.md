---
title: "[xubuntu] How to determine PPA instal &lt;value&gt; if not posted (odd PPA not showing)"
date: 2014-09-17
forum: New to Ubuntu
---

### Post by whereismymindat2 on 2014-09-17
Question. How can you determine what install command to run after  ppa created?  (if it is not posted with the PPA)
---Also "odd" behavior if I run $ sudo apt-get update (multiple times in a row)

"odd" because each time the KB's found will go up in size/down in size/back up/finally won't show any "left"


Example-Installed this PPA
VLC media player: Backported from Ubuntu/Debian
[https://launchpad.net/~n-muench/+archive/ubuntu/vlc](https://launchpad.net/~n-muench/+archive/ubuntu/vlc)

```
sudo add-apt-repository ppa:n-muench/vlc
```



PPA installed/no error
```

Press [ENTER] to continue or ctrl-c to cancel adding it
gpg: keyring `/tmp/tmp9s7sg01g/secring.gpg' created
gpg: keyring `/tmp/tmp9s7sg01g/pubring.gpg' created
gpg: requesting key EAE0D85C from hkp server keyserver.ubuntu.com
gpg: /tmp/tmp9s7sg01g/trustdb.gpg: trustdb created
gpg: key EAE0D85C: public key "Launchpad PPA for Nate Muench" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
bender@DAWG:~$ 

```



Where I feel "Odd" happened
_____________________________
Perform Update as Required

```

bender@DAWG:~$ sudo apt-get update
Ign http://us.archive.ubuntu.com trusty InRelease
Ign http://us.archive.ubuntu.com trusty-updates InRelease                      

[-----REMOVED LONG list of urls (without KB) && only included a url of a PPA was attached---]


bender@DAWG:~$ sudo apt-get update
Ign http://ppa.launchpad.net trusty InRelease                       
Ign http://ppa.launchpad.net trusty InRelease                        
Get:1 http://security.ubuntu.com trusty-security Release.gpg [933 B]           
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:2 http://security.ubuntu.com trusty-security Release [59.7 kB]             
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:3 http://security.ubuntu.com trusty-security/main Sources [44.3 kB]        
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease
Get:4 http://security.ubuntu.com trusty-security/restricted Source [14 B]                                       
Get:5 http://security.ubuntu.com trusty-security/universe Sources [10.8 kB]    
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:6 http://security.ubuntu.com trusty-security/multiverse Sources [700 B]    
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:7 http://security.ubuntu.com trusty-security/main i386 Packages [133 kB]
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty Release.gpg                            
Hit http://ppa.launchpad.net trusty Release.gpg                                
Get:8 http://security.ubuntu.com trusty-security/restricted i386 Packages [14 B]
Hit http://ppa.launchpad.net trusty Release.gpg                                
Get:9 http://security.ubuntu.com trusty-security/universe i386 Packages [47.0 kB]
Hit http://ppa.launchpad.net trusty Release.gpg                                
Get:10 http://security.ubuntu.com trusty-security/multiverse i386 Packages [1,398 B]
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty Release.gpg                   
Get:11 http://ppa.launchpad.net trusty Release.gpg [316 B]
Hit http://ppa.launchpad.net trusty Release 
Hit http://ppa.launchpad.net trusty Release                        
Hit http://ppa.launchpad.net trusty Release                        
Hit http://ppa.launchpad.net trusty Release                        
Hit http://ppa.launchpad.net trusty Release   
Hit http://ppa.launchpad.net trusty Release                          
Hit http://ppa.launchpad.net trusty Release                          
Hit http://ppa.launchpad.net trusty Release                          
Hit http://ppa.launchpad.net trusty Release                          
Get:12 http://ppa.launchpad.net trusty Release [14.6 kB]             
Hit http://ppa.launchpad.net trusty Release                            
Hit http://ppa.launchpad.net trusty/main i386 Packages              
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:13 http://ppa.launchpad.net trusty/main i386 Packages [16.0 kB]            
Get:14 http://ppa.launchpad.net trusty/main Translation-en [8,819 B]           
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Fetched 338 kB in 15s (21.6 kB/s)                                              
Reading package lists... Done
bender@DAWG:~$ 

```




Thus first "udate" run, showed: 
1st:  Fetched 338 kB in 15s (21.6 kB/s) Total Get:14

Then 2,3,4....
2nd: Fetched 1,139 kB in 15s (74.6 kB/s) Total Get:24
3rd: Fetched 1,099 kB in 15s (69.4 kB/s)  Total Get:20
4th:Fetched 1,139 kB in 15s (74.6 kB/s)  Total Get: 24

Then 5,6
5th $ sudo apt-get update  (none)= Reading package lists... Done  
6th $ sudo apt-get update  (none)= Reading package lists... Done 


_____________________________



Therefore---
1st: Still Original Question. 
How do I determine the sudo apt-get install <value> as per original above, no instal" <value> supplied. 

_____________________________

2nd 


(new question)---Why did each update jump around on sizes (up/down) then "disapper" with no more to do
*AND*
original question---since it's showing no updates, did my package install?

Thanks!

---

### Post by mc4man on 2014-09-17
> original question---since it's showing no updates, did my package install?
No, you've only updated your sources (list
Either 
sudo apt-get upgrade
or for that ppa
sudo apt-get install vlc
to test either first add a simulate (does nothing), ex.
sudo apt-get -s install vlc

if ok then rerun command without the -s

---

### Post by ibjsb4 on 2014-09-17
Install Synaptic Package Manager, makes it easier to see whats going on :)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9)

---

### Post by whereismymindat2 on 2014-09-22
Thank you kindly to both!

---

