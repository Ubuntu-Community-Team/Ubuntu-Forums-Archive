---
title: "Can't download new programs"
date: 2012-03-01
forum: New to Ubuntu
---

### Post by Primitive Artifice on 2012-03-01
A few weeks ago my wi-fi card ceased working and I had to switch to a wired connection. Now it seems I cannot download programs using the software center. I am specifically trying to download GIMP but it cannot download any program.

When I try to obtain a program through the software center I get a message saying "Failed to download package files, Check you Internet connection" and when downloading GIMP it gives me another message saying "Requires download of untrusted packages, The action would require the installation of packages from not authenticated sources." When I click on Details it says "gimp gimp-data libbabl-0.0-0 libgegl-0.0-0 libgimp2.0 libilmbase6 libopenexr6"

I tried the "apt-get install gimp" command in terminal and got this:
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

When I tried downloading a .deb file I found in the forums "gimp-2.3_2.3.16-0madman2k1_i386.deb" I get the option of going to software center but when I go to the software center it says "Internal Error, The file "/home/kris/downloads/gimp-2.3_2.3.16-0madman2k1_i386.deb" could not be opened"

I know that before losing my wi-fi connection I had no problem downloading GIMP but some of the messages make me think it may be some sort of permissions error or something. I really have no idea how to fix this and I really need to download some programs (image editing software is sort of a must). Any help would be greatly appreciated.

---

### Post by cortman on 2012-03-01
Hi, reboot your computer and run the following commands (in a terminal) one by one-

```
sudo apt-get install -f
sudo apt-get clean
sudo apt-get update
```

Post the output of sudo apt-get update here.

---

### Post by Primitive Artifice on 2012-03-01
The results were thus:


Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates InRelease               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports InRelease              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                            
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release.gpg [198 B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg [198 B]      
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release.gpg [198 B]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release.gpg [198 B]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release [40.8 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release    
  
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release
  
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release [40.8 kB]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release          
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release
  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse i386 Packages/DiffIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages/DiffIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Translation-en
Fetched 866 B in 2s (394 B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/Release](http://security.ubuntu.com/ubuntu/dists/oneiric-security/Release)  

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by cortman on 2012-03-01
Looks like some keys are missing or gone bad. [This blog post]("http://cortman.wordpress.com/2012/02/27/how-to-fix-gpg-errors-in-ubuntu/") should explain how to fix it.

---

### Post by edm1 on 2012-03-01
```
gpg --keyserver keyserver.ubuntu.com --recv 16126D3A3E5C1192
gpg --export --armor 16126D3A3E5C1192 | sudo apt-key add -
```

```
gpg --keyserver keyserver.ubuntu.com --recv 40976EAF437D05B5
gpg --export --armor 40976EAF437D05B5 | sudo apt-key add -
```

These will add the two missing keys. Why are those keys missing in the first place though? There could be a bigger problem.

---

### Post by Primitive Artifice on 2012-03-01
I'm not honestly sure what a key is so I couldn't really postulate as to why I'm missing them. 

Unfortunately after I entered the code and got the same results when trying to install GIMP I decided to restart my computer before actually copying the results to post here. While I don't have the initial reaction to the code I do get this reaction when I try it now.


gpg --keyserver keyserver.ubuntu.com --recv 16126D3A3E5C1192
gpg: requesting key 3E5C1192 from hkp server keyserver.ubuntu.com
gpg: key 3E5C1192: "Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1


I assume this means the keys were imported properly but unfortunately I get the exact same reaction when trying to install GIMP through terminal or the software center. I haven't checked out the blog post though, I'll be doing that now.

Out of curiosity, if I were to reformat my hard drive and re-install ubuntu would it fix this missing keys problem?

Thanks very much for all the help guys, I really appreciate it.

---

### Post by Primitive Artifice on 2012-03-01
Edit: Well, I successfully installed GIMP through Software Center and through terminal. I think my previous failed attempt after importing the keys was simply a typo.

Thank you so much for your help guys! 75% of my purpose in owning a computer would've been lost without an image editing program. I really appreciate it. Thank you!

---

### Post by cortman on 2012-03-01
It looks like your repositories updated perfectly. You should be good to try to install Gimp again. It appears you may have some fragmented gimp packages already on your system (apt-get clean and apt-get install -f should fix that) but to be sure run

```
sudo apt-get purge gimp
```

And then try installing it from the command line.

```
sudo apt-get install gimp
```

If for some reason you still get errors, post them and we'll keep working on it!

---

### Post by Primitive Artifice on 2012-03-01
Ah, thanks man. I managed to get it to work luckily. Again, I really appreciate it. :D

---

### Post by cortman on 2012-03-01
> **Primitive Artifice said:**
> Ah, thanks man. I managed to get it to work luckily. Again, I really appreciate it. :D

No problem, glad to help. I take it Gimp installed fine after the apt-get update, with no additional finagling needed?
Mark this thread as [SOLVED], if you would, using the thread tools.

---

