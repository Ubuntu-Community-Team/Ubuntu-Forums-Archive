---
title: "Newbie Here..."
date: 2012-02-02
forum: New to Ubuntu
---

### Post by CollegeLad on 2012-02-02
Hello People of Ubuntu, 

I've just installed the latest version of Ubuntu onto my Computer and I need flash player would anyone be able to advise on how i would over come this little problem.


(Quick Story)
according to the programs on the computer already, it already has Adobe flash player 10. but it wont let me get onto a friends website. Ive tried UN-installing the flash but it says that I also need to un-istall "GTK+ control panel for adobe flash player plugin version 11" So i say remove all but it wont let me.
This is the error ---> > There seems to be a programming error in aptdaemon. This is the software that allows you to install/remove software and to perform other package management related tasks.

Tried showing for "There seems to be a programming error in aptdaemon" on Google and people have posted saying that, if i do command line. sudo apt-get install ttf-mscorefonts-installer this should work, well it does upto a point where the license agreement but then it wont let me accept .

Plz help.

Thank You.

---

### Post by androssofer on 2012-02-02
> **CollegeLad said:**
> Hello People of Ubuntu, 

I've just installed the latest version of Ubuntu onto my Computer and I need flash player would anyone be able to advise on how i would over come this little problem.


(Quick Story)
according to the programs on the computer already, it already has Adobe flash player 10. but it wont let me get onto a friends website. Ive tried UN-installing the flash but it says that I also need to un-istall "GTK+ control panel for adobe flash player plugin version 11" So i say remove all but it wont let me.
This is the error ---> > There seems to be a programming error in aptdaemon. This is the software that allows you to install/remove software and to perform other package management related tasks.

Tried showing for "There seems to be a programming error in aptdaemon" on Google and people have posted saying that, if i do command line. sudo apt-get install ttf-mscorefonts-installer this should work, well it does upto a point where the license agreement but then it wont let me accept .

Plz help.

Thank You.

good day sir!

so the first part.. did you try to install flash via the software center? or synaptic package manager?

have you tried chrome ([download here]("http://www.google.co.jp/chrome/index.html?platform=linux&hl=en")) google ships it with flash built in.. (or so i was lead to believe)


when it gets to the license agreement bit, what exactly happens?

---

### Post by lechien73 on 2012-02-02
A repeat of the good day, sir...and welcome to the Ubuntu forums.

To solve your apt-get problem, you could try opening a window and doing the following:

```
sudo dpkg --configure -a
sudo apt-get purge ttf-mscorefonts-installer
sudo apt-get install ttf-mscorefonts-installer
sudo apt-get update
```

Hopefully that will allow you to install the ttf-mscorefonts. Flash is a thorny problem, so even when you've got your aptdaemon working properly, you may still have issues :eek: but that's what the forums are here for :D

---

### Post by CollegeLad on 2012-02-02
sudo dpkg --configure -a 
dpkg: error: dpkg status database is locked by another process

sudo apt-get purge ttf-mscorefonts-installer 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
alex@Alex:~$ sudo apt-get install ttf-mscorefonts-installer
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

sudo apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric InRelease                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                       
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates InRelease           
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports InRelease         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg          
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric Release.gpg                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates Release.gpg         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports Release.gpg       
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources             
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric Release                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex           
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates Release             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports Release           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted Sources          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main Sources                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse Sources                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main i386 Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted i386 Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe i386 Packages      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse i386 Packages    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main TranslationIndex       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse TranslationIndex 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted TranslationIndex 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe TranslationIndex   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main Sources                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse Sources            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe Sources    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main i386 Packages  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/main Sources      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/universe Sources  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/main TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/universe TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse Translation-en   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted Translation-en   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/universe Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_GB
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_GB
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Does this mean anything to you .....

---

### Post by CollegeLad on 2012-02-02
> **androssofer said:**
> good day sir!

so the first part.. did you try to install flash via the software center? or synaptic package manager?

have you tried chrome ([download here]("http://www.google.co.jp/chrome/index.html?platform=linux&hl=en")) google ships it with flash built in.. (or so i was lead to believe)


when it gets to the license agreement bit, what exactly happens?


I get this when trying to donwload the Synaptic package manger.... 
An unhandled error occured
There seems to be a programming error in aptdaemon. This is the software that allows you to install/remove software and to perform other package management related tasks.

---

### Post by lechien73 on 2012-02-02
Ok, before running the dpkg code I gave you, make sure that you have quit from Synaptic, the Update Manager, or the Software Centre.

You could try rebooting, and making sure that all these programs are closed and then try the code again :)

---

### Post by 3rdalbum on 2012-02-02
When you get to the license agreement thingy, you need to press Tab to activate the buttons, and Spacebar to "press" the highlighted one.

---

### Post by CollegeLad on 2012-02-03
> **lechien73 said:**
> Ok, before running the dpkg code I gave you, make sure that you have quit from Synaptic, the Update Manager, or the Software Centre.

You could try rebooting, and making sure that all these programs are closed and then try the code again :)

Morning, 

I turn my computer off last night and this morning tryied to run the dpkg command again and this is the error message:-> dpkg: error: dpkg status database is locked by another process...... I have nothing open just the terminal.

---

### Post by CollegeLad on 2012-02-03
Never mind people. I dont know whats happen but now its all working fine (flash player i mean) 

This forums are great.

---

### Post by goofey24 on 2012-02-03
> **CollegeLad said:**
> Never mind people. I dont know whats happen but now its all working fine (flash player i mean) 

This forums are great.

Glad to hear you have it sorted out.
Welcome to the forums:p
At the top of your thread you will see 'Thread Tools', please click that and you may mark thread'Solved'

---

