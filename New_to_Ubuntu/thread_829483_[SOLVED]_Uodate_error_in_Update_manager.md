---
title: "[SOLVED] Uodate error in Update manager"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by dnaga57 on 2008-06-14
In 8.04, when I click on Check in Update Manager I get the following error message. What should I do:(


W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

---

### Post by Rocket2DMn on 2008-06-14
The chances are that the medibuntu repository is just down or unavailable at the moment.  I suggest running
```
sudo apt-get update
sudo apt-get upgrade
```
from terminal.  If you get the same error, just wait awhile and try again.

---

### Post by dnaga57 on 2008-06-14
On running the command, I keep getting the following error only. How do I correct it?
Thanks for helping me


dnubuntu@dnubuntu-laptop:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg [189B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release                         
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release [5590B]            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Fetched 190B in 1s (147B/s)
Reading package lists... Done
[SIZE="5"]W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
dnubuntu@dnubuntu-laptop:~$ 

[/SIZE]

---

### Post by drs305 on 2008-06-14
You can try running this to make sure the key isn't causing the problem:
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```


[Medibuntu Repository Instructions]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by Rocket2DMn on 2008-06-14
If you are updating from Gutsy, go to System->Administration->Software Sources and hit the Thiry-Party Software tab.  Uncheck the boxes for Medibuntu (they may still be for Gutsy).  Close, you can allow it to update if you want.
Now go to [https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f) and follow the directions for Hardy (two lines of commands).  You should then be able to proceed with what you were doing before.

---

### Post by Najand on 2008-06-14
I think other solutions have already worked for you, but as reference for other similar questions, have a look at ubuntu help pages and you will find all information needed for downloading packages from repositories.

[https://help.ubuntu.com](https://help.ubuntu.com)

---

### Post by Najand on 2008-06-14
In your special case:
[https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f)

---

### Post by dnaga57 on 2008-06-14
Thanks that did it

---

### Post by dnaga57 on 2008-06-15
How do I thank you all?

---

### Post by drs305 on 2008-06-15
If you find a post particularly useful you can go to that post and then click on the gold star in the lower right of the post.

Maybe more importantly, once your problem has been solved it is helpful to mark the thread solved if you made the original post. You can mark it solved by going to the top right of the original post, selecting Thread Tools, and the Mark as solved.

---

