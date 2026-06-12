---
title: "update manager crashes"
date: 2015-02-07
forum: New to Ubuntu
---

### Post by lila on 2015-02-07
Hi,

My update manager has been telling me every day for over a week that I need to install the same updates, and everytime I try it just crashes.  I managed to update just the internet-related ones (firefox etc.), but not the rest.  I searched here, but couldn't find a solution.  I did however find that I should run 
sudo apt-get update
which I did.  This is the result.  Sorry it's in French, tell me if you need help... ;)  The last paragraph looks like the most important to my non-expert eyes, it reads after "Release": "the following signatures are not valid" 

```
orla@orla-desktop:~$ sudo apt-get update
[sudo] password for orla: 
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty-updates InRelease
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg
Réception de*: 1 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty Release.gpg [933 B]
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release       
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty-updates Release.gpg
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty Release                            
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty Release                                
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources          
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty-updates Release                    
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources            
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty/main Sources/DiffIndex                 
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources          
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty/restricted Sources/DiffIndex           
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages   
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty/universe Sources/DiffIndex             
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages    
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty/multiverse Sources/DiffIndex           
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages      
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty/main i386 Packages/DiffIndex           
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages    
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty/restricted i386 Packages/DiffIndex     
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en  
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty/universe i386 Packages/DiffIndex       
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en   
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty/multiverse i386 Packages/DiffIndex     
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty/main Translation-fr                
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en     
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty/main Translation-en                
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty/multiverse Translation-fr
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty/multiverse Translation-en
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty/restricted Translation-fr
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty/restricted Translation-en
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty/universe Translation-fr
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty/universe Translation-en
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty-updates/main Sources
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty-updates/restricted Sources
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty-updates/universe Sources
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty-updates/multiverse Sources
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty-updates/main i386 Packages
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty-updates/restricted i386 Packages
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty-updates/universe i386 Packages
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty-updates/multiverse i386 Packages
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty-updates/main Translation-en
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty-updates/multiverse Translation-en
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty-updates/restricted Translation-en
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty-updates/universe Translation-en
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty/main Sources       
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty/restricted Sources 
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty/universe Sources   
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty/multiverse Sources 
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty/main i386 Packages 
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty/restricted i386 Packages
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty/universe i386 Packages
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty/multiverse i386 Packages
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty/main Translation-fr_FR                 
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty/multiverse Translation-fr_FR           
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty/restricted Translation-fr_FR           
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty/universe Translation-fr_FR             
933 o réceptionnés en 10s (91 o/s)                                             
Lecture des listes de paquets... Fait
W: Erreur de GPG*:*[http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) trusty Release*:*Les signatures suivantes ne sont pas valables*: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
orla@orla-desktop:~$
```

---

### Post by lila on 2015-02-07
I forgot to add: everytime I try to update, it tells me this requires using unverified sources, and I only have the option to click "ok".  Then it crashes.  Even when I select only "basic ubuntu components" to be updated, it wants those unverified sources.  This feels dodgy to me! :(

---

### Post by newb85 on 2015-02-07
Try this from the command line:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
```
That should do it.

---

### Post by lila on 2015-02-07
Hi, 
thanks, but no, it didn't fix it.  It did something and said soemthing about 27 new keys, but then the update behaved just the same, and when I did sudo apt-get update again, I got the exact same text as before.

---

### Post by lila on 2015-02-07
I tried your code lien again, now I get:
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --homedir /tmp/tmp.Id8gbMbx7Y --no-auto-check-trustdb --trust-model always --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
gpg: demande de la clef 437D05B5 sur le serveur hkp keyserver.ubuntu.com
gpg: clef 437D05B5*: «*Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>*» n'est pas modifiée
gpg: Quantité totale traitée*: 1
gpg:              non modifiées*: 1
orla@orla-desktop:~$

---

### Post by newb85 on 2015-02-07
All right, then try this approach:

```
sudo apt-get clean
sudo mv /var/lib/apt/lists /var/lib/apt/lists.old
sudo mkdir -p /var/lib/apt/lists/partial
sudo apt-get clean
sudo apt-get update
```

---

### Post by lila on 2015-02-07
erm... I just re-read a sticky that really spooked me out about source code which one doesn't understand.  The first one, I did kind of understand, but this second one talks about cleaning things... no offence, I'm not trying to be rude, just safe... so I'll wait until I get at least one other person saying that that is a good idea and ok to do.  Better safe than sorry, this is my business and personal computer, it would seriously inconvience me to have a major problem with it.  Hey, I guess that's why I use ubuntu in the first place! :-)

---

### Post by newb85 on 2015-02-07
No offence taken at all.  You're right to be cautious.

If you check the man page for apt-get
```
man apt-get
```
running apt-get clean clears out the contents of /var/cache/apt/archives.  This only contains downloaded package files.  Once you install a package, you don't need the package file again.  If you end up needing one again (for reinstallation), the system will automatically download it again if you don't have it.

The directory in the second command, /var/lib/apt/lists, is just a list of what packages are available in the repositories.  Using mv is a non-destructive way of clearing out that list.  In reality, the list will be automatically re-populated the next time you run apt-get update.  The only thing that won't be re-populated is the /var/lib/apt/lists/partial directory.  Hence the third command.

If you want to wait for someone else to confirm, that's no problem at all.

---

### Post by lila on 2015-02-07
Thanks!
Right now the kids are watching a movie on the affected computer.  I'll try it later tonight, and check out that man  page meanwhile.

---

### Post by newb85 on 2015-02-07
Great!  F.Y.I., there should be a man page for every CLI command you have available explaining the command and its options.

---

### Post by lila on 2015-02-07
Yesss!!! That did it! Thank you very much! :p
I'll mark this solved.

---

### Post by newb85 on 2015-02-09
Happy Ubuntuing!

---

