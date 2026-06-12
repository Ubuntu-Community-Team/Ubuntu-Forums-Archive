---
title: "ubuntu 12.04 software-center crash after installing ica-client"
date: 2013-04-03
forum: New to Ubuntu
---

### Post by knoeterich on 2013-04-03
Hi all,

I have some trouble with the software-center on my ubuntu 12.04 64bit. While I was installing the citrix receiver for Linux ([http://www.citrix.com/downloads/citrix-receiver/receivers-by-platform/receiver-for-linux-121.html](http://www.citrix.com/downloads/citrix-receiver/receivers-by-platform/receiver-for-linux-121.html), .deb file) I shut down the PC by accident and the installation could not finish. After I started the PC again, the software-center does not open anymore.

It says:
E: The package icaclient needs to be reinstalled, but I can't find an archive for it.

When I type in the terminal

```
software-center
```

it gives me:
The application »software-center« is not installed. You can install it by typing:
sudo apt-get install software-center

When I type in

```
sudo apt-get install software-center
```

Lista are read...ready
Tree is built   
Information on status is read...ready
E: The package icaclient has to be reinstalled, but there is no archive for it

(I translated this into English)

This is I can neither open, remove or reinstall the software-center.

Any help is appreciated!:KS

---

### Post by schragge on 2013-04-03
Try
```

sudo apt-get clean
sudo apt-get update
sudo apt-get --reinstall install icaclient

```

---

### Post by knoeterich on 2013-04-03
Thanks for your help! Unfortunately, it did not do any better. This is the output:

```

sudo apt-get clean

```
no output

```

sudo apt-get update

```
W: GPG-error: [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) ./ Release: Die following signatures could not be proven because there is no public key: NO_PUBKEY 300229ECEA82E6EA

```
sudo apt-get --reinstall install icaclient
```
Lists are read...ready
Tree is built   
Information on status is read...ready
E: The package icaclient has to be reinstalled, but there is no archive for it

---

### Post by schragge on 2013-04-03
One of your software sources [post=12529430]points to sourceforge.net[/post]. Is it [Ubuntuzilla](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation)? Remove it, then repeat the last two commands.

---

### Post by knoeterich on 2013-04-04
Still no better :(

> **schragge said:**
> One of your software sources [post=12529430]points to sourceforge.net[/post]. Is it [Ubuntuzilla]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation")? Remove it,

```
sudo apt-get remove ubuntuzilla

```
Lists are read...ready
Tree is built   
Information on status is read...ready
E: The package icaclient has to be reinstalled, but there is no archive for it

 > then repeat the last two commands.
```
sudo apt-get update
```
OK   [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg
OK   [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                  
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise Release.gpg                          
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates Release.gpg                  
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports Release.gpg                
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise Release                              
OK   [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                             
OK   [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                   
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates Release                      
OK   [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                      
OK   [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports Release                    
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/main amd64 Packages                  
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/restricted amd64 Packages            
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/universe amd64 Packages              
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/multiverse amd64 Packages            
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/main i386 Packages                   
OK   [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                       
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/restricted i386 Packages             
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/universe i386 Packages           
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/multiverse i386 Packages             
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/main TranslationIndex                
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/multiverse TranslationIndex      
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/restricted TranslationIndex      
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/universe TranslationIndex        
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/main amd64 Packages      
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/restricted amd64 Packages
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/universe amd64 Packages      
OK   [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages           
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/multiverse amd64 Packages
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/main i386 Packages       
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/restricted i386 Packages 
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/universe i386 Packages   
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/multiverse i386 Packages 
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/main TranslationIndex        
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/multiverse TranslationIndex  
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/restricted TranslationIndex  
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/universe TranslationIndex    
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/main amd64 Packages    
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/restricted amd64 Packages
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/universe amd64 Packages    
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/multiverse amd64 Packages  
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/main i386 Packages     
OK   [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages     
OK   [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages       
OK   [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages 
OK   [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages            
OK   [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages      
OK   [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages        
OK   [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages      
OK   [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex         
OK   [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex   
OK   [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex   
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/restricted i386 Packages   
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/universe i386 Packages     
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/multiverse i386 Packages
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/main TranslationIndex      
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/restricted TranslationIndex
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/universe TranslationIndex  
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/main Translation-de                  
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/main Translation-en                  
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/multiverse Translation-de            
OK   [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex     
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/multiverse Translation-en            
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/restricted Translation-de            
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/restricted Translation-en            
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/universe Translation-de              
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/universe Translation-en              
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/main Translation-de          
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/main Translation-en      
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/multiverse Translation-de
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/multiverse Translation-en    
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/restricted Translation-de    
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/restricted Translation-en    
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/universe Translation-de  
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/universe Translation-en  
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/main Translation-en    
OK   [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en       
OK   [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en 
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/multiverse Translation-en  
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/restricted Translation-en  
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/universe Translation-en    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-de_DE                    
OK   [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-de
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en
OK   [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Hole:1 [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) ./ Release.gpg [490 B]
OK   [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) ./ Release                               
Ign [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) ./ Release                                
Ign [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) ./ Sources/DiffIndex                      
Ign [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) ./ Packages/DiffIndex                     
OK   [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) ./ Sources              
OK   [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) ./ Packages            
Ign [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) ./ Translation-de_DE
Ign [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) ./ Translation-de
Ign [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) ./ Translation-en
Es wurden 490 B in 18 s geholt (26 B/s)
Paketlisten werden gelesen... Fertig
W: GPG-Error: [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) ./ Release: The following signatures are not valid: KEYEXPIRED 1353618531 KEYEXPIRED 1353618531 KEYEXPIRED 1353618531

```
sudo apt-get --reinstall install icaclient

```
Lists are read...ready
Tree is built   
Information on status is read...ready
E: The package icaclient has to be reinstalled, but there is no archive for it

Maybe it is the easiest to update my system to 12.10?

---

### Post by schragge on 2013-04-04
Sorry, I was not clear enough. What I meant was removing Ubuntuzilla repository, not the *ubuntuzilla* package itself. Anyway, try
```
[FONT=monospace]
[/FONT]sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
sudo apt-key update
sudo apt-get update

```

---

### Post by knoeterich on 2013-04-04
Hm, no better... I tried to switch language in my system to English but it won't work, guess because of the error in the software-center.
Btw, when I try to open the software-center it tells me that it is not installed.
Here is what your commands give me:
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.DGbAWEDbfh --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com C1289A29
gpg: Schlüssel C1289A29 von hkp-Server keyserver.ubuntu.com anfordern
gpg: Schlüssel C1289A29: "Daniel Folkinshteyn (Ubuntuzilla signing key) <nanotube@users.sourceforge.net>" nicht geändert
gpg: Anzahl insgesamt bearbeiteter Schlüssel: 1
gpg:              unverändert: 1

```
sudo apt-key update
```
gpg: Schlüssel 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" nicht geändert
gpg: Schlüssel FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" nicht geändert
gpg: Schlüssel C0B21F32: "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" nicht geändert
gpg: Schlüssel EFE21092: "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" nicht geändert
gpg: Anzahl insgesamt bearbeiteter Schlüssel: 4
gpg:              unverändert: 4

```
sudo apt-get update
```
W: GPG-Fehler: [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) ./ Release: Die folgenden Signaturen waren ungültig: KEYEXPIRED 1353618531 KEYEXPIRED 1353618531 KEYEXPIRED 1353618531

---

### Post by schragge on 2013-04-04
Well, then disable ubuntuzilla repository:
```
gksudo software-properties-gtk
``` and uncheck lines with *sourceforge.net* on the second tab.

---

### Post by knoeterich on 2013-04-04
Thank you very much for your continuous help. I unchecked the sources and tried all of the commands above again - same result..
Maybe I should update the system from 12.04 to 12.10 as a workaround?

---

### Post by schragge on 2013-04-04
One last try:
```

sudo rm -frv /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get clean
sudo apt-get update
sudo dpkg --force-remove-reinstreq -r icaclient

```

---

### Post by knoeterich on 2013-04-04
:guitar:It finally works! Thank you so much!

I did all of the commands above, then I did
```
sudo apt-get --reinstall install software-center
sudo apt-get install software-center
```

and now it works perfectly fine. Thanks for your patience!

---

