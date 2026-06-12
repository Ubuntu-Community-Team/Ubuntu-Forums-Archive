---
title: "[SOLVED] trying to get codecs for media players"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by misswham on 2008-11-07
i have tried and tried.  if i play some movies in vlc i will get the video but no audio, if i try to play in totum i will get the audio but no video.  i just reinstalled ubuntu and it worked fine for a week and then all of a sudden i started having this problem.  i have done all of the updates through the terminal but this is the outcome of the last one i tried

sudo apt-get update
[sudo] password for aretha: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US        
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg [189B]         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources              
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release [9335B]                      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Fetched 190B in 1s (95B/s)
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
aretha@aretha-desktop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory


what can i do

---

### Post by n9uib on 2008-11-07
sudo apt-get update

that should get it

    steve

---

### Post by misswham on 2008-11-07
that is what i ran in the initial post.  that is the outcome of it.  there is an error message at the bottom of the post i keep getting.

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

i still cant get the codecs and i am having the same problem with sound and video that wasnt happening 2 days ago

---

### Post by jolx on 2008-11-07
> **misswham said:**
> that is what i ran in the initial post.  that is the outcome of it.  there is an error message at the bottom of the post i keep getting.

im pretty sure what steve was talking about is that you ran apt-get update without sudo permissions, hence the error "Permission Denied"

---

### Post by Crafty Kisses on 2008-11-07
Try running the following commands:
```
sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get update

```

---

### Post by tangibleorange on 2008-11-07
you can stop the medibuntu key error by doing this:

```
sudo apt-get install medibuntu-keyring
```

---

### Post by nothingspecial on 2008-11-07
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

---

### Post by mapes12 on 2008-11-07
These may help:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

[http://linuxondesktop.blogspot.com/2008/04/things-to-do-on-your-new-ubuntu-804.html](http://linuxondesktop.blogspot.com/2008/04/things-to-do-on-your-new-ubuntu-804.html)

---

### Post by misswham on 2008-11-07
I have done everything.  Everything was working fine 3 days ago and now it isnt working.  Vlc pic no sound, movie player sound no video.  I have done everything in the suggestions above and it still isnt working.  I am at wits end.

---

### Post by philinux on 2008-11-07
> **misswham said:**
> I have done everything.  Everything was working fine 3 days ago and now it isnt working.  Vlc pic no sound, movie player sound no video.  I have done everything in the suggestions above and it still isnt working.  I am at wits end.

Close vlc if it's running. Go to your home folder and hit ctrl h this will show hidden config files. Locate .vlc and delete it then run vlc. It will recreate the folder again with it's default settings. Try it and see if it works.

Have you installed ubuntu-restricted-extras?

---

### Post by mapes12 on 2008-11-07
Have you changed anything on your system since 3 days ago? inc updates and any new packages??

---

### Post by misswham on 2008-11-07
When the update sign comes at the top I always update.  I thought I was supposed to and yes I have deleted vlc and reinstalled it and the same thing even with movie player.

---

### Post by mdpalow on 2008-11-07
Try QuickStart in my signature below. It installs all the necessary codecs/DVD files for you. Ignore that it says 'backup/restore' and just click the link and read. :)

Good luck

---

### Post by misswham on 2008-11-11
Just started working today.  I dont know what happened.  I hope it lasts.  Thanks for all of your help everyone.

---

