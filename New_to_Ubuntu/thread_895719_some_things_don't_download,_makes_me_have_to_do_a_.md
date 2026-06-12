---
title: "some things don't download, makes me have to do a partial update."
date: 2008-08-20
forum: New to Ubuntu
---

### Post by alfiefarley on 2008-08-20
I have Ubuntu Hardy Heron, i've installed quite a bit of stuff like kismet and aircrack.ng and i think it could be these that are messing up my updates, it's the last few lines that have the problems.
Anyway this is what i get when i type sudo apt-get update into terminal:


Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Translation-en_GB          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Translation-en_GB                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Translation-en_GB    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Translation-en_GB      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Translation-en_GB    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_GB       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_GB           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_GB     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Translation-en_GB              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Translation-en_GB                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Translation-en_GB              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_GB     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Translation-en_GB          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Translation-en_GB    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Translation-en_GB      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Translation-en_GB    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_GB                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_GB                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_GB               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_GB               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release.gpg                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Translation-en_GB       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Translation-en_GB           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Translation-en_GB     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Translation-en_GB     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_GB         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_GB             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_GB       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_GB       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed Release.gpg                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/universe Translation-en_GB        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/main Translation-en_GB            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/restricted Translation-en_GB      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/multiverse Translation-en_GB      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed Release                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Sources                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/universe Sources                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/main Sources                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/restricted Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/multiverse Sources                
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg                         
  Could not connect to packages.freecontrib.org:80 (34.52.53.34), connection timed out
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Translation-en_GB
  Unable to connect to packages.freecontrib.org http:
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Translation-en_GB
  Unable to connect to packages.freecontrib.org http:
Reading package lists... Done                             
W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg)  Could not connect to packages.freecontrib.org:80 (34.52.53.34), connection timed out

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/i18n/Translation-en_GB.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/i18n/Translation-en_GB.bz2)  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/i18n/Translation-en_GB.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/i18n/Translation-en_GB.bz2)  Unable to connect to packages.freecontrib.org http:

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems


i had already tried to run it again and nothing different happened.
sorry it's so long, basically i was wondering what i could do to prevent getting these 'failed' error messages.

thanks in advance
alfie.

---

### Post by Elfy on 2008-08-20
Have you updated from dapper? You have repos for both dapper and hardy

---

### Post by LowSky on 2008-08-20
not to mention many of the same repos are listed twice

and these
> Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Translation-en_GB
Unable to connect to packages.freecontrib.org http:
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Translation-en_GB
Unable to connect to packages.freecontrib.org http:

probably dont work anymore or you need to update them to Hardy Repos

---

### Post by alfiefarley on 2008-08-23
how do i update to hardy repos?

---

### Post by Elfy on 2008-08-23
Remove all the dapper entries from the sources list - from what I can gather freecontrib is gone, so you can lose them as well - medibuntu does the same things

```
gksudo gedit /etc/apt/sources.list
```

You should be left with just hardy references in the file; if you're not sure post the list here. 

Once that is all done you can add medibuntu with these

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by alfiefarley on 2008-09-02
hmm did all that but it's still saying i have to do a partial update.
ps sorry i take soo long to respond, i'm afraid i just don't have the time, and when i do i don't remember to lol.

---

### Post by Elfy on 2008-09-03
Can you do ```
ls /etc/apt
``` and ```
cat /etc/apt/sources.list
``` and post both of the outputs here please.

---

### Post by zipperback on 2008-09-03
> **alfiefarley said:**
> Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages 



Take all the references out of your updates that aren't for your distribution level.

You have both Dapper and Hardy repositories.

Fix it, so that you only have hardy, and then launch synaptic, click the Reload button, and then click the mark all updates, and then click apply.

- zipperback
:popcorn:

---

### Post by alfiefarley on 2008-09-04
alfie@alfie-laptop:~$ ls /etc/apt
apt.conf.d    sources.list~        sources.list.d     trusted.gpg
secring.gpg   sources.list_backup  sources.list.save  trusted.gpg~
sources.list  sources.list_BACKUP  trustdb.gpg

alfie@alfie-laptop:~$ cat /etc/apt/sources.list
    ## Add comments (##) in front of any line to remove it from being checked.
    ## Use the following sources.list at your own risk.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

    ## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

    ## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse


there you go forest pixie

and zipperback, how do i take all the references out?

i believe my problem is sorted out, i did the gksudo gedit /etc/apt/sources.list
i then deleted everything, because it was all dapper and none was hardy.
i also then did sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
which i have no idea what they do.
and now when i try to update it all seems fine and doesn't do the partial update thing.

however now when i go to gksudo gedit /etc/apt/sources.list
there is nothing there. Is this ok??
thanks for all the help

---

### Post by Elfy on 2008-09-04
Ok - it doesn't look like you have any other source lists

Is that all of your sources list now - or only the dapper lines? If that is just the dapper lines then you can delete them from the file, save and close then run

```
sudo apt-get update
```

If, however, that is all you have in the file then we'll haveto start again :)

---

### Post by alfiefarley on 2008-09-04
well i did that and this happened:

alfie@alfie-laptop:~$ sudo apt-get update
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_GB
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_GB
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Reading package lists... Done
alfie@alfie-laptop:~$ 

then i did:

gksudo gedit /etc/apt/sources.list

and theres still nothing on the list, don't know whether there is supposed to be.
but other than that all is solved as far as i can tell.
can someone confirm the confirmation or is the list not being there wrong?
thanks

---

### Post by Elfy on 2008-09-05
Open software sources in the system admin menu.

On the 1st tab - enable , universe, main, multiverse and restricted
On the 2nd tab - enable ubuntu partners and medibuntu if it is there
On the 3rd tab - enable security and updates, _not_ backports and proposed

Close and reload when prompted, the sources should now be set up.

Run ```
sudo apt-get update
``` and it should show a lot more than before, if it still isn't working post back here and I'll post my sources for you.

---

