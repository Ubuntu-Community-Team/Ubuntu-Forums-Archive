---
title: "Updating problem"
date: 2012-10-28
forum: New to Ubuntu
---

### Post by SchrodingerCat on 2012-10-28
Hi all, i am new of this Forum. I have a problem in Ubuntu 12.04.
I can see a red triangle on the top of my screen and when i click on it it says that there are problems with the uploads. I already read other posts about the same problem but nothing seem to work.. can you help me? I am not able either to upload by terminal and by upload manager. Thank you

---

### Post by twipley on 2012-10-28
Hello, catsie.

I am assuming you mean "update" by "upload."

The problem has arisen to me because I had installed software in an "unofficial" manner. When I upgraded to fresh 12.10 installation, the problem went away, though.

Precise error message and tried terminal commands would be of use. ;)

---

### Post by deadflowr on 2012-10-28
Please open up a terminal and enter the commands:

```
sudo apt-get update && sudo apt-get upgrade
```

then select all and copy, and in the reply box paste them in the code tags (#).
This will give us more relevant information on your problem.

---

### Post by SchrodingerCat on 2012-10-28
Sorry, this is my first time on this Forum and i really can't find the code(#) tag, i don't know how to insert it. BTW..i will paste my code here, sorry if it will create problems.




Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                      
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/ InRelease                               
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Trovato [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                
Scaricamento di:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]          
Trovato [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                       
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/ Release.gpg                             
Trovato [http://dl.google.com](http://dl.google.com) stable Release.gpg                                
Trovato [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                               
Trovato [http://archive.canonical.com](http://archive.canonical.com) precise Release                           
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                               
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise InRelease                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/ Release                                 
Trovato [http://dl.google.com](http://dl.google.com) stable Release                                    
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise InRelease                             
Trovato [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                          
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-updates InRelease                     
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-backports InRelease                   
Trovato [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages            
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                          
Trovato [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                    
Trovato [http://linux.dropbox.com](http://linux.dropbox.com) precise Release.gpg                           
Trovato [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                        
Trovato [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                   
Trovato [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                    
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise Release.gpg                       
Trovato [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages             
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                   
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Trovato [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Trovato [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                         
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Scaricamento di:2 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-updates Release.gpg [198 B]
Trovato [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources         
Trovato [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources           
Trovato [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources         
Trovato [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages        
Trovato [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages  
Trovato [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages    
Trovato [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages  
Trovato [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages         
Trovato [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages   
Trovato [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages     
Trovato [http://linux.dropbox.com](http://linux.dropbox.com) precise Release                               
Trovato [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages   
Trovato [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex      
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-backports Release.gpg             
Trovato [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex
Trovato [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Trovato [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex  
Trovato [http://linux.dropbox.com](http://linux.dropbox.com) precise/main amd64 Packages                   
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise Release                           
Scaricamento di:3 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-updates Release [49,6 kB]
Trovato [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en        
Trovato [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en  
Trovato [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en  
Trovato [http://linux.dropbox.com](http://linux.dropbox.com) precise/main i386 Packages                    
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main TranslationIndex                     
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-backports Release                 
Trovato [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en    
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise/main Sources                      
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise/restricted Sources                
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise/universe Sources                  
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise/multiverse Sources                
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise/main amd64 Packages               
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise/restricted amd64 Packages         
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise/universe amd64 Packages           
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise/multiverse amd64 Packages         
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise/main i386 Packages                
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise/restricted i386 Packages          
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise/universe i386 Packages            
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise/multiverse i386 Packages          
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise/main TranslationIndex             
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise/multiverse TranslationIndex       
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise/restricted TranslationIndex       
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise/universe TranslationIndex         
Scaricamento di:4 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-updates/main Sources [182 kB]
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-it_IT             
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-it                
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/ Sources                                 
  404  Not Found [IP: 91.189.92.176 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/ Packages                                
  404  Not Found [IP: 91.189.92.176 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/ Translation-it_IT                       
Scaricamento di:5 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-updates/restricted Sources [4395 B]
Scaricamento di:6 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-updates/universe Sources [60,7 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-it_IT                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-it_IT                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/ Translation-it                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/ Translation-en                          
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-it_IT                         
Scaricamento di:7 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-updates/multiverse Sources [4745 B]
Scaricamento di:8 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-updates/main amd64 Packages [417 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-it                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-it                       
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-it                            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Scaricamento di:9 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-updates/restricted amd64 Packages [8215 B]
Scaricamento di:10 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-updates/universe amd64 Packages [151 kB]
Scaricamento di:11 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [8948 B]
Scaricamento di:12 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-updates/main i386 Packages [425 kB]
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main Translation-it_IT                    
Scaricamento di:13 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-updates/restricted i386 Packages [8218 B]
Scaricamento di:14 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-updates/universe i386 Packages [151 kB]
Scaricamento di:15 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-updates/multiverse i386 Packages [9930 B]
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-updates/main TranslationIndex     
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-updates/restricted TranslationIndex
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-updates/universe TranslationIndex
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-backports/main Sources           
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-backports/restricted Sources     
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-backports/universe Sources       
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main Translation-it                      
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-backports/multiverse Sources      
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main Translation-en                       
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-backports/main amd64 Packages     
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-backports/restricted amd64 Packages
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-backports/universe amd64 Packages 
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-backports/multiverse amd64 Packages
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-backports/main i386 Packages      
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-backports/restricted i386 Packages
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-backports/universe i386 Packages  
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-backports/multiverse i386 Packages
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-backports/main TranslationIndex   
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-backports/universe TranslationIndex
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise/main Translation-it               
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise/main Translation-en               
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise/multiverse Translation-it         
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise/multiverse Translation-en         
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise/restricted Translation-it         
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise/restricted Translation-en         
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise/universe Translation-it           
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise/universe Translation-en           
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-updates/main Translation-it       
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-updates/main Translation-en       
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-updates/multiverse Translation-it 
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-updates/multiverse Translation-en 
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-updates/restricted Translation-it 
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-updates/restricted Translation-en 
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-updates/universe Translation-it   
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-updates/universe Translation-en   
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-backports/main Translation-en     
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-backports/multiverse Translation-en
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-backports/restricted Translation-en
Trovato [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) precise-backports/universe Translation-en 
Recuperati 1481 kB in 10s (143 kB/s)                                           
W: Impossibile recuperare [http://archive.ubuntu.com/bin/linux/ubuntu/precise/Sources](http://archive.ubuntu.com/bin/linux/ubuntu/precise/Sources)  404  Not Found [IP: 91.189.92.176 80]

W: Impossibile recuperare [http://archive.ubuntu.com/bin/linux/ubuntu/precise/Packages](http://archive.ubuntu.com/bin/linux/ubuntu/precise/Packages)  404  Not Found [IP: 91.189.92.176 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
giuliano@metropolis:~$ 




Thank you

---

### Post by Immolatus on 2012-10-28
[http://ubuntuforums.org/archive/index.php/t-1879295.html](http://ubuntuforums.org/archive/index.php/t-1879295.html)

:popcorn:

---

### Post by SchrodingerCat on 2012-10-29
Hi Immolatus thank you but unfortunately it did'nt work!!
If i try to run the Update manager this is the exit code....


W:Failed to fetch [http://archive.ubuntu.com/bin/linux/ubuntu/precise/Sources](http://archive.ubuntu.com/bin/linux/ubuntu/precise/Sources)  404  Not Found [IP: 91.........]
, W:Failed to fetch [http://archive.ubuntu.com/bin/linux/ubuntu/precise/Packages](http://archive.ubuntu.com/bin/linux/ubuntu/precise/Packages)  404  Not Found [IP: 91........]
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by newb85 on 2012-10-29
Please give the output of

```
cat /etc/apt/sources.list
```

You can put the output in code tags by manually adding them like this:

[noparse]```
Output
Here
```[/noparse]

Or, you can highlight the output and click the icon above the composition frame marked with a "#".

---

### Post by SchrodingerCat on 2012-10-29
Here it is. Thank you

```
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://it.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://it.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://it.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://it.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://it.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://it.archive.ubuntu.com/ubuntu/ precise universe
deb http://it.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://it.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://it.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://it.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://it.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://archive.ubuntu.com/bin/linux/ubuntu precise/
deb-src http://archive.ubuntu.com/bin/linux/ubuntu precise/
```

---

### Post by NikTh on 2012-10-29
Hi , 

these two lines are wrong 

```
deb http://archive.ubuntu.com/bin/linux/ubuntu precise/ 
deb-src http://archive.ubuntu.com/bin/linux/ubuntu precise/
```

remove them and should be fine. 

Check with ```
sudo apt-get update
```

---

### Post by SchrodingerCat on 2012-10-29
How can i remove them?:)

---

### Post by NikTh on 2012-10-29
Open a terminal and run this command 

```
gksudo gedit /etc/apt/sources.list
``` 

Remove lines or add at the begin of each line this symbol # (almost same thing as remove them). 

Save the file and run in terminal 
```
sudo apt-get update
```

Thanks

---

### Post by SchrodingerCat on 2012-10-30
How can i delete those 2 lines?

```
deb http://archive.ubuntu.com/bin/linux/ubuntu precise/ 
deb-src http://archive.ubuntu.com/bin/linux/ubuntu precise/
```

I have problems with updating and i have been told to delete this two line. Tanks for your help

---

### Post by Impavidus on 2012-10-30
I don't know by heart where the file is that contains those lines, but open it in your favorite text editor *with root permissions*, navigate to those lines, delete them and save the file. (Alternatively, you may want to comment them out using a #. This allows for easier restore if it doesn't work.)

---

### Post by newb85 on 2012-10-30
Those lines are probably in the file /etc/apt/sources.list.  From the terminal

```
sudo gedit /etc/apt/sources.list
```

Find those lines.  You can simply delete them.  You can also comment them out so they don't do anything by simply putting a "#" symbol at the beginning of each line.  And if you want, you can make a note right above them explaining why you commented them out, just for future reference.  (Just make sure you start that line with "#", as well.)

Whichever you choose, save the file and close it when you're done.

---

### Post by NikTh on 2012-10-30
Hi , 
I have already answered to you in this thread 
[http://ubuntuforums.org/showthread.php?t=2077501](http://ubuntuforums.org/showthread.php?t=2077501)

Thanks

---

### Post by coffeecat on 2012-10-30
Threads merged.

@SchrodingerCat, please don't start a new thread with a question that is already being dealt with in a previous thread of yours. This dilutes community effort.

---

### Post by SchrodingerCat on 2012-10-30
Hi all and thank you for your answers. I am sorry for posting twice a Thread..i am new of this Forum but next time i'll remember it!
Btw i deleted that two lines but i still have the same prooblem..here is the exit copde of ```
sudo-apt get update
```

```
Ign http://security.ubuntu.com precise-security InRelease
Ign http://archive.canonical.com precise InRelease                             
Ign http://extras.ubuntu.com precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://archive.ubuntu.com precise/ InRelease                               
Scaricamento di:1 http://security.ubuntu.com precise-security Release.gpg [198 B]
Ign http://dl.google.com stable InRelease                                      
Trovato http://archive.canonical.com precise Release.gpg                       
Trovato http://ppa.launchpad.net precise Release.gpg                           
Scaricamento di:2 http://extras.ubuntu.com precise Release.gpg [72 B]          
Ign http://archive.ubuntu.com precise/ Release.gpg                             
Scaricamento di:3 http://security.ubuntu.com precise-security Release [49,6 kB]
Trovato http://dl.google.com stable Release.gpg                                
Trovato http://archive.canonical.com precise Release                           
Trovato http://extras.ubuntu.com precise Release                               
Trovato http://ppa.launchpad.net precise Release                               
Ign http://archive.ubuntu.com precise/ Release                                 
Trovato http://dl.google.com stable Release                                    
Trovato http://archive.canonical.com precise/partner amd64 Packages            
Trovato http://extras.ubuntu.com precise/main Sources                          
Trovato http://ppa.launchpad.net precise/main Sources                          
Trovato http://dl.google.com stable/main amd64 Packages                        
Trovato http://archive.canonical.com precise/partner i386 Packages             
Ign http://archive.canonical.com precise/partner TranslationIndex              
Trovato http://extras.ubuntu.com precise/main amd64 Packages                   
Trovato http://dl.google.com stable/main i386 Packages                         
Trovato http://extras.ubuntu.com precise/main i386 Packages                    
Trovato http://ppa.launchpad.net precise/main amd64 Packages                   
Trovato http://ppa.launchpad.net precise/main i386 Packages                    
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Scaricamento di:4 http://security.ubuntu.com precise-security/main Sources [51,1 kB]
Ign http://it.archive.ubuntu.com precise-updates InRelease                     
Ign http://dl.google.com stable/main TranslationIndex                          
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Ign http://it.archive.ubuntu.com precise InRelease                             
Ign http://it.archive.ubuntu.com precise-backports InRelease                   
Scaricamento di:5 http://security.ubuntu.com precise-security/restricted Sources [1950 B]
Scaricamento di:6 http://security.ubuntu.com precise-security/universe Sources [14,5 kB]
Scaricamento di:7 http://security.ubuntu.com precise-security/multiverse Sources [1379 B]
Scaricamento di:8 http://security.ubuntu.com precise-security/main amd64 Packages [180 kB]
Scaricamento di:9 http://it.archive.ubuntu.com precise-updates Release.gpg [198 B]
Trovato http://it.archive.ubuntu.com precise Release.gpg                       
Scaricamento di:10 http://it.archive.ubuntu.com precise-backports Release.gpg [198 B]
Scaricamento di:11 http://it.archive.ubuntu.com precise-updates Release [49,6 kB]
Err http://archive.ubuntu.com precise/ Sources                                 
  404  Not Found [IP: 91.189.92.156 80]
Scaricamento di:12 http://security.ubuntu.com precise-security/restricted amd64 Packages [3969 B]
Ign http://linux.dropbox.com precise InRelease                                 
Ign http://archive.canonical.com precise/partner Translation-it_IT             
Scaricamento di:13 http://security.ubuntu.com precise-security/universe amd64 Packages [48,6 kB]
Err http://archive.ubuntu.com precise/ Packages                                
  404  Not Found [IP: 91.189.92.156 80]
Ign http://archive.canonical.com precise/partner Translation-it                
Scaricamento di:14 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2188 B]
Scaricamento di:15 http://security.ubuntu.com precise-security/main i386 Packages [186 kB]
Ign http://archive.ubuntu.com precise/ Translation-it_IT                       
Ign http://archive.ubuntu.com precise/ Translation-it                          
Ign http://archive.ubuntu.com precise/ Translation-en                          
Ign http://ppa.launchpad.net precise/main Translation-it_IT                    
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://ppa.launchpad.net precise/main Translation-it                       
Ign http://ppa.launchpad.net precise/main Translation-en                       
Trovato http://it.archive.ubuntu.com precise Release                           
Scaricamento di:16 http://it.archive.ubuntu.com precise-backports Release [49,6 kB]
Ign http://extras.ubuntu.com precise/main Translation-it_IT                    
Scaricamento di:17 http://security.ubuntu.com precise-security/restricted i386 Packages [3968 B]
Scaricamento di:18 http://security.ubuntu.com precise-security/universe i386 Packages [48,7 kB]
Ign http://extras.ubuntu.com precise/main Translation-it                       
Ign http://dl.google.com stable/main Translation-it_IT                         
Trovato http://linux.dropbox.com precise Release.gpg                           
Scaricamento di:19 http://security.ubuntu.com precise-security/multiverse i386 Packages [2357 B]
Scaricamento di:20 http://security.ubuntu.com precise-security/main TranslationIndex [73 B]
Scaricamento di:21 http://security.ubuntu.com precise-security/multiverse TranslationIndex [71 B]
Scaricamento di:22 http://security.ubuntu.com precise-security/restricted TranslationIndex [71 B]
Scaricamento di:23 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://dl.google.com stable/main Translation-it                            
Scaricamento di:24 http://it.archive.ubuntu.com precise-updates/main Sources [182 kB]
Ign http://dl.google.com stable/main Translation-en                            
Trovato http://security.ubuntu.com precise-security/main Translation-en        
Trovato http://security.ubuntu.com precise-security/multiverse Translation-en  
Trovato http://security.ubuntu.com precise-security/restricted Translation-en  
Trovato http://security.ubuntu.com precise-security/universe Translation-en    
Scaricamento di:25 http://it.archive.ubuntu.com precise-updates/restricted Sources [4395 B]
Scaricamento di:26 http://it.archive.ubuntu.com precise-updates/universe Sources [60,7 kB]
Trovato http://linux.dropbox.com precise Release                               
Scaricamento di:27 http://it.archive.ubuntu.com precise-updates/multiverse Sources [4745 B]
Scaricamento di:28 http://it.archive.ubuntu.com precise-updates/main amd64 Packages [417 kB]
Trovato http://linux.dropbox.com precise/main amd64 Packages                   
Scaricamento di:29 http://it.archive.ubuntu.com precise-updates/restricted amd64 Packages [8215 B]
Scaricamento di:30 http://it.archive.ubuntu.com precise-updates/universe amd64 Packages [151 kB]
Scaricamento di:31 http://it.archive.ubuntu.com precise-updates/multiverse amd64 Packages [8948 B]
Scaricamento di:32 http://it.archive.ubuntu.com precise-updates/main i386 Packages [425 kB]
Trovato http://linux.dropbox.com precise/main i386 Packages                    
Ign http://linux.dropbox.com precise/main TranslationIndex                     
Scaricamento di:33 http://it.archive.ubuntu.com precise-updates/restricted i386 Packages [8218 B]
Scaricamento di:34 http://it.archive.ubuntu.com precise-updates/universe i386 Packages [151 kB]
Scaricamento di:35 http://it.archive.ubuntu.com precise-updates/multiverse i386 Packages [9930 B]
Scaricamento di:36 http://it.archive.ubuntu.com precise-updates/main TranslationIndex [3564 B]
Scaricamento di:37 http://it.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2605 B]
Scaricamento di:38 http://it.archive.ubuntu.com precise-updates/restricted TranslationIndex [2461 B]
Scaricamento di:39 http://it.archive.ubuntu.com precise-updates/universe TranslationIndex [2850 B]
Trovato http://it.archive.ubuntu.com precise/universe Sources   
Trovato http://it.archive.ubuntu.com precise/multiverse Sources
Trovato http://it.archive.ubuntu.com precise/universe amd64 Packages
Trovato http://it.archive.ubuntu.com precise/multiverse amd64 Packages
Trovato http://it.archive.ubuntu.com precise/universe i386 Packages
Trovato http://it.archive.ubuntu.com precise/multiverse i386 Packages
Trovato http://it.archive.ubuntu.com precise/multiverse TranslationIndex
Trovato http://it.archive.ubuntu.com precise/universe TranslationIndex
Scaricamento di:40 http://it.archive.ubuntu.com precise-backports/main Sources [2422 B]
Scaricamento di:41 http://it.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Scaricamento di:42 http://it.archive.ubuntu.com precise-backports/universe Sources [17,2 kB]
Scaricamento di:43 http://it.archive.ubuntu.com precise-backports/multiverse Sources [2669 B]
Scaricamento di:44 http://it.archive.ubuntu.com precise-backports/main amd64 Packages [1945 B]
Scaricamento di:45 http://it.archive.ubuntu.com precise-backports/restricted amd64 Packages [14 B]
Scaricamento di:46 http://it.archive.ubuntu.com precise-backports/universe amd64 Packages [14,9 kB]
Scaricamento di:47 http://it.archive.ubuntu.com precise-backports/multiverse amd64 Packages [2489 B]
Scaricamento di:48 http://it.archive.ubuntu.com precise-backports/main i386 Packages [1941 B]
Scaricamento di:49 http://it.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Scaricamento di:50 http://it.archive.ubuntu.com precise-backports/universe i386 Packages [14,9 kB]
Scaricamento di:51 http://it.archive.ubuntu.com precise-backports/multiverse i386 Packages [2504 B]
Scaricamento di:52 http://it.archive.ubuntu.com precise-backports/main TranslationIndex [72 B]
Scaricamento di:53 http://it.archive.ubuntu.com precise-backports/multiverse TranslationIndex [72 B]
Scaricamento di:54 http://it.archive.ubuntu.com precise-backports/restricted TranslationIndex [70 B]
Scaricamento di:55 http://it.archive.ubuntu.com precise-backports/universe TranslationIndex [73 B]
Trovato http://it.archive.ubuntu.com precise-updates/main Translation-it
Trovato http://it.archive.ubuntu.com precise-updates/main Translation-en
Trovato http://it.archive.ubuntu.com precise-updates/multiverse Translation-it
Trovato http://it.archive.ubuntu.com precise-updates/multiverse Translation-en
Trovato http://it.archive.ubuntu.com precise-updates/restricted Translation-it
Trovato http://it.archive.ubuntu.com precise-updates/restricted Translation-en
Trovato http://it.archive.ubuntu.com precise-updates/universe Translation-it
Trovato http://it.archive.ubuntu.com precise-updates/universe Translation-en
Trovato http://it.archive.ubuntu.com precise/multiverse Translation-it
Trovato http://it.archive.ubuntu.com precise/multiverse Translation-en
Trovato http://it.archive.ubuntu.com precise/universe Translation-it
Trovato http://it.archive.ubuntu.com precise/universe Translation-en
Trovato http://it.archive.ubuntu.com precise-backports/main Translation-en
Trovato http://it.archive.ubuntu.com precise-backports/multiverse Translation-en
Trovato http://it.archive.ubuntu.com precise-backports/restricted Translation-en
Trovato http://it.archive.ubuntu.com precise-backports/universe Translation-en
Ign http://linux.dropbox.com precise/main Translation-it_IT
Ign http://linux.dropbox.com precise/main Translation-it
Ign http://linux.dropbox.com precise/main Translation-en
Recuperati 2199 kB in 4s (476 kB/s)
W: Impossibile recuperare http://archive.ubuntu.com/bin/linux/ubuntu/precise/Sources  404  Not Found [IP: 91.189.92.156 80]

W: Impossibile recuperare http://archive.ubuntu.com/bin/linux/ubuntu/precise/Packages  404  Not Found [IP: 91.189.92.156 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by SchrodingerCat on 2012-10-30
Oh sorry i was deleting the wrong files! now is working. thank you!

---

### Post by newb85 on 2012-10-30
[s]Those two sources are incorrect.  I have no idea where they came from.  Remove them, as well.[/s]

Edit: removed

---

### Post by NikTh on 2012-10-30
```
Impossibile recuperare
``` means ```
Failed to fetch
```Google translate :P 

You still have those lines.. you didn't delete them properly ? or maybe listed under the /etc/apt/sources.list.d/ ? 
```
deb http://archive.ubuntu.com/bin/linux/ubuntu precise/ 
deb-src http://archive.ubuntu.com/bin/linux/ubuntu precise/
```

Edited due to 
> **SchrodingerCat said:**
> Oh sorry i was deleting the wrong files! now is working. thank you!

Thanks

---

