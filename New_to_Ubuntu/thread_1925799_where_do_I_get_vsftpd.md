---
title: "where do I get vsftpd"
date: 2012-02-15
forum: New to Ubuntu
---

### Post by david55 on 2012-02-15
Hi

I am using Ubuntu 9.10 and need to install vsftpd. My internet is working. When I try using "sudo apt-get install vsftpd" it says it cannot find the package. I tried using Synaptic and that says it found it but when I try get it says the server cannot be found. I have gone to vsftpd web site and they say due to security issues they have moved their software. I can download it directly from their web site but I get the source code and don't know how to get that installed.

I have spent a few hours on Google and have not been able to resolve this. I do need to use this version of Ubuntu and I do need to use vsftpd because it is all part of a tutorial that I am working through. All helpful suggestions will be appreciated

thanks
David

---

### Post by aeiah on 2012-02-15
can you install anything else? what does ```
sudo apt-get update
``` do? it should pull the newest versions of the repository data down from the ubuntu servers - perhaps the repositories have changed or been pulled completley. [ubuntu 9.10 support ended in april 2011]("https://wiki.ubuntu.com/Releases")

---

### Post by david55 on 2012-02-15
Hi 

Thanks for quick reply. How does one get a package if a repository has been removed? It does this:

root@ubuntu:~# sudo apt-get update
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-en_US   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release.gpg       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages
  404  Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages
  404  Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Sources
  404  Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources
  404  Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Sources
  404  Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Sources
  404  Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages
  404  Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages
  404  Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages
  404  Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages
  404  Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Sources
  404  Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Sources
  404  Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Sources
  404  Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Sources
  404  Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Packages
  404  Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Packages
  404  Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Packages
  404  Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Packages
  404  Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Sources
  404  Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Sources
  404  Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Sources
  404  Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Sources
  404  Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Packages
  404  Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Packages
  404  Not Found [IP: 91.189.88.40 80]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz)  404  Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.gz)  404  Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz)  404  Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.gz)  404  Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz)  404  Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz)  404  Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.gz)  404  Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources.gz)  404  Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.gz)  404  Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.40 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
root@ubuntu:~#

---

### Post by Lars Noodén on 2012-02-15
[9.10 stopped getting support back in April of last year](https://wiki.ubuntu.com/Releases).  It is rather important that you upgrade as soon as you can so that you can patch your system when needed.  

As far as getting packages for the old releases, point the repository to '[old-releases.ubuntu.com](https://help.ubuntu.com/community/EOLUpgrades#Requirements)'

Why are you looking for vs[ftp](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/)?  Wouldn't SFTP be more appropriate instead?

---

### Post by david55 on 2012-02-15
Hi

I am running Ubuntu in a virtual machine on my winxp pc. I am using it to compile a different version of linux for an embedded system. This embedded system came with the ubuntu ISO and all of the documentation and cross compilers  based around this version. I am a bit worried that if I uses a newer version of Ubuntu and newer compilers that I will run into problems with things not being the same as in the documentation. But now I am running into other problems due to it being old so am not sure what would be the best way to go forward

David

---

### Post by Lars Noodén on 2012-02-15
Since you are running it in a virtual machine  you have several extra options.  One is to make a copy of the VM and work your experiments with the copy.  Another would be to take a snapshot before messing with the system and rolling back to it when you are done with the experiments.  I'd say try the former first, that way you can try the compilers and other components at no risk.

---

### Post by david55 on 2012-02-15
If I understand you correctly then I should perhaps download the latest version of Ubuntu and install it in the VM and then see if everything else still works ok. If it does not then I guess I can always try get the old version working again.?

---

### Post by surfer on 2012-02-15
you do not have to use a newer version of ubuntu.

just change the entries in /etc/apt/sources.list to point to the base url [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) as pointed out by Lars Noodén (follow the link in his post).

---

### Post by david55 on 2012-02-15
Thanks guys you have all been a great help. I set it up to point to old repositories as suggested and have managed to install it :D

---

### Post by surfer on 2012-02-15
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?

---

### Post by Lars Noodén on 2012-02-15
> **david55 said:**
> Thanks guys you have all been a great help. I set it up to point to old repositories as suggested and have managed to install it :D

I'm not sure that it is help to be using the expired repositories. ;)

If you get time, I would still recommend testing your software on a newer version of Ubuntu in a VM.  That way you'll have security updates and other fixes as needed.  If you go with 12.04, which is being tested, you won't have to think of changing systems until 2017.

---

