---
title: "update manager error 302"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by musicguy on 2008-08-03
hey hi, not sure what to do about this, when i type sudo apt-get update in the terminal i get this error. what can i do to fix it?
             
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) gutsy/free Packages                           
  302 Found
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources               
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) gutsy/non-free Packages                       
  302 Found
Fetched 5B in 6s (1B/s)                                                        
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/gutsy/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/gutsy/free/binary-i386/Packages.gz)  302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/gutsy/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/gutsy/non-free/binary-i386/Packages.gz)  302 Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by BGFG on 2008-08-03
Think you need to double check your System>>Administration>>Software Sources. I got an error like that recently, but my router connection was mucking up.

---

### Post by mevets on 2008-08-03
If those are valid addresses then just run apt-get update again. Sometimes the interwebs are just not as reliable as you would like them to be.

---

### Post by ET! on 2008-08-03
update the software lists....using synaptic is lot easier

---

### Post by musicguy on 2008-08-22
hey, sorry it took me so long to reply.

i tried just doing it again and again, i kept getting the same error.

how do i update through synaptic, just like upgrading? i tried upgrading and stuff, still nothin.. 
i tried going to the software sources and click and updating there but i got this message. 

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://medibuntu.sos-sts.com/repo/dists/gutsy/free/binary-i386/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/gutsy/free/binary-i386/Packages.gz:) 302 Found
[http://medibuntu.sos-sts.com/repo/dists/gutsy/non-free/binary-i386/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/gutsy/non-free/binary-i386/Packages.gz:) 302 Found

i know im not having network connection issues because my connection is fine.. i dont know, im lost..

---

