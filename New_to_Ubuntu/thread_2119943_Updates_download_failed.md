---
title: "Updates download failed"
date: 2013-02-25
forum: New to Ubuntu
---

### Post by mamugian on 2013-02-25
When i open download manager and i try to check for updates, it fail and says me: downloading repository failed and to check my internet connection. I'm sure i am connected (tested too) and that's what it appear behind:

"W:GPG error: [http://dl.dropbox.com](http://dl.dropbox.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY BACCFCFB98DB2EDC, W:Failed to fetch [http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/precise/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead."

help please ):P

---

### Post by TheFu on 2013-02-25
It seems that a dropbox repository has been added to your system.  I do not use dropbox (to me "cloud" means "someone elses computer"), so I can only guess that during the install process that tool modified your /etc/apt/sources* in some way that is failing now.

I believe that only the dropbox repository is impacted, so doing other updates should work fine still.

Try running these 2 commands and posting any errors:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by mamugian on 2013-02-25
root@TheMamugian:/home/tommy# sudo apt-get update
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise InRelease                                
Trovato [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg                          
Trovato [http://archive.canonical.com](http://archive.canonical.com) precise Release                          
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                  
Trovato [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages            
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                    
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex             
Ign [http://dl.dropbox.com](http://dl.dropbox.com) stable InRelease                                    
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages              
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex               
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex           
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-it                 
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en                 
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-it             
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en              
Scaricamento di:1 [http://dl.dropbox.com](http://dl.dropbox.com) stable Release.gpg [490 B]             
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
  404  Not Found
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-it_IT            
Scaricamento di:2 [http://dl.dropbox.com](http://dl.dropbox.com) stable Release [2412 B]               
Ign [http://dl.dropbox.com](http://dl.dropbox.com) stable Release                                       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-it               
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-it_IT
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-it
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://dl.dropbox.com](http://dl.dropbox.com) stable/main i386 Packages/DiffIndex
Ign [http://dl.dropbox.com](http://dl.dropbox.com) stable/main TranslationIndex
Scaricamento di:3 [http://dl.dropbox.com](http://dl.dropbox.com) stable/main i386 Packages [1709 B]
Ign [http://dl.dropbox.com](http://dl.dropbox.com) stable/main Translation-it_IT
Ign [http://dl.dropbox.com](http://dl.dropbox.com) stable/main Translation-it
Ign [http://dl.dropbox.com](http://dl.dropbox.com) stable/main Translation-en
Recuperati 4611 B in 5s (786 B/s)
W: Errore GPG: [http://dl.dropbox.com](http://dl.dropbox.com) stable Release: Le seguenti firme non sono state verificate perché la chiave pubblica non è disponibile: NO_PUBKEY BACCFCFB98DB2EDC
W: Impossibile recuperare [http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Impossibile recuperare [http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Impossibile scaricare alcuni file di indice: saranno ignorati o verranno usati quelli vecchi.

----Lasts error are in my language (italian) they mean that it's impossible to download some summary files, they will be ignored or some old will be used instead 
For the second command it says that I have 0 packet to remove, intall or upgrade

---

### Post by audiomick on 2013-02-25
> **mamugian said:**
> 
W: Errore GPG: [http://dl.dropbox.com](http://dl.dropbox.com) stable Release: Le seguenti firme non sono state verificate perché la chiave pubblica non è disponibile: NO_PUBKEY BACCFCFB98DB2EDC

That is a missing authentification for the dropbox source.


These two
> 
W: Impossibile recuperare [http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Impossibile recuperare [http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

Are just not there anymore. That looks to be a PPA for some battery status tool. I would just remove that from your software sources. No point having it there if the source has disappeared.

I'm not sure how to get the GPG key back for the dropbox thing.

---

### Post by TheFu on 2013-02-25
a) I **love** Italy!  I'm always looking for an excuse to visit.

b) I think you are fine.  All the important repositories are refreshed and the system doesn't need any updates.

If you want to clean up the messages - I would - then determine which packages the system was getting from the dl.dropbox.com locations and find where the current stable versions are located.  Either through Canonical's repos or 3rd party PPA.

[http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/](http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/) exists, but there is no Precise directory.  Could it be that you upgraded this system and just need to remove that PPA?
There is probably another battery-status tool somewhere else.

Good luck.

---

### Post by mamugian on 2013-02-25
So i should remove dropbox from my pc ?

---

### Post by audiomick on 2013-02-25
> **mamugian said:**
> So i should remove dropbox from my pc ?

There is no urgent need to do so. Are you using it?

---

### Post by mamugian on 2013-02-25
The problem is that at the end of all it doesn't download the upgrade, in fact if i check it says that the alst update were checked 112 days ago

---

### Post by mamugian on 2013-02-25
Well maybe i solved it. I went to the repository info and the only active were the dropbox one and not the official ubuntu and other.
I runned verify again and the error message was the same, to check the ocnnection, but it downloaded anyway 674 update for the first time!

---

### Post by audiomick on 2013-02-25
Ok, it might have sorted itself out. Keep an eye on it, but it it doesn't give you any more error messages, I think you are right.

---

