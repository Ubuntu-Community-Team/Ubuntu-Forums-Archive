---
title: "can't run update/apt-get"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by mgmoore on 2008-09-24
Hello, I'm not very experienced in linux and I'm having some difficulties running the update manager. It gets to file 38/66 and says "could not download all repository indexes". 
Apt get also doesn't work.

I'm certain that it has to do with proxy settings, as I'm setting this machine up at work.My proxy settings appear to be correct in system -> preference -> network proxy, I'm able to browse the internet, its just when I try to update that it fails.
I've posted before and no one seemed able to help. I'd appreciate any advise :)

---

### Post by bench on 2008-09-24
Can you open a terminal (Applications > Accessories > Terminal) and type 'sudo apt-get update' (without the quotes), and post the output?  Also you could post the output of the command 'cat /etc/apt/sources.list' (also without the quotes).  Sounds like it's can't resolve one of the repositories you're got configured.

---

### Post by mgmoore on 2008-09-24
I apollogise for the ginormous spam that follows: 

cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) hardy main restricted
deb-src [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) hardy-updates main restricted
deb-src [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) hardy universe
deb-src [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) hardy universe
deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) hardy-updates universe
deb-src [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) hardy multiverse
deb-src [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) hardy multiverse
deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) hardy-updates multiverse
deb-src [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) hardy-security main restricted
deb-src [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) hardy-security main restricted
deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) hardy-security universe
deb-src [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) hardy-security universe
deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) hardy-security multiverse
deb-src [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) hardy-security multiverse


sudo apt-get update
[sudo] password for michael: 
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy Release.gpg
Err [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy/main Translation-en_US
  Error reading from server - read (104 Connection reset by peer)
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy/restricted Translation-en_US
Err [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy/universe Translation-en_US
  Error reading from server - read (104 Connection reset by peer)
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy/multiverse Translation-en_US
Err [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-updates Release.gpg
  Error reading from server - read (104 Connection reset by peer)
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-updates/main Translation-en_US
Err [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-updates/restricted Translation-en_US
  Error reading from server - read (104 Connection reset by peer)
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-updates/universe Translation-en_US
Err [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-updates/multiverse Translation-en_US
  Error reading from server - read (104 Connection reset by peer)
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-security Release.gpg
Err [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-security/main Translation-en_US
  Error reading from server - read (104 Connection reset by peer)
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-security/restricted Translation-en_US
Err [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-security/universe Translation-en_US
  Error reading from server - read (104 Connection reset by peer)
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-security/multiverse Translation-en_US
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy Release        
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-updates Release
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-security Release
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy/main Packages  
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy/restricted Packages
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy/main Sources   
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy/restricted Sources
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy/universe Packages
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy/universe Sources
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy/multiverse Packages
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy/multiverse Sources
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-updates/main Packages
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-updates/restricted Packages
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-updates/main Sources
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-updates/restricted Sources
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-updates/universe Packages
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-updates/universe Sources
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-updates/multiverse Packages
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-updates/multiverse Sources
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-security/main Packages
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-security/restricted Packages
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-security/main Sources
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-security/restricted Sources
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-security/universe Packages
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-security/universe Sources
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-security/multiverse Packages
Ign [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-security/multiverse Sources
Err [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy/main Packages  
  Error reading from server - read (104 Connection reset by peer)
Err [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy/main Sources   
  Error reading from server - read (104 Connection reset by peer)
Err [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy/restricted Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy/universe Packages
  Error reading from server - read (104 Connection reset by peer)
Err [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy/universe Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy/multiverse Packages
  Error reading from server - read (104 Connection reset by peer)
Err [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy/multiverse Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-updates/main Packages
  Error reading from server - read (104 Connection reset by peer)
Err [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-updates/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-updates/main Sources
  Error reading from server - read (104 Connection reset by peer)
Err [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-updates/restricted Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-updates/universe Packages
  Error reading from server - read (104 Connection reset by peer)
Err [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-updates/universe Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-updates/multiverse Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-updates/multiverse Sources
  Error reading from server - read (104 Connection reset by peer)
Err [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-security/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-security/restricted Packages
  Error reading from server - read (104 Connection reset by peer)
Err [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-security/main Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-security/restricted Sources
  Error reading from server - read (104 Connection reset by peer)
Err [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-security/universe Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-security/universe Sources
  Error reading from server - read (104 Connection reset by peer)
Err [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-security/multiverse Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err [http://archive.linux.duke.edu](http://archive.linux.duke.edu) hardy-security/multiverse Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
W: Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://archive.linux.duke.edu/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Error reading from server - read (104 Connection reset by peer)

W: Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2](http://archive.linux.duke.edu/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2)  Error reading from server - read (104 Connection reset by peer)

W: Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy-updates/Release.gpg](http://archive.linux.duke.edu/ubuntu/dists/hardy-updates/Release.gpg)  Error reading from server - read (104 Connection reset by peer)

W: Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2](http://archive.linux.duke.edu/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2)  Error reading from server - read (104 Connection reset by peer)

W: Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2](http://archive.linux.duke.edu/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2)  Error reading from server - read (104 Connection reset by peer)

W: Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2](http://archive.linux.duke.edu/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2)  Error reading from server - read (104 Connection reset by peer)

W: Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2](http://archive.linux.duke.edu/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2)  Error reading from server - read (104 Connection reset by peer)

W: Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/hardy/main/binary-i386/Packages.gz)  Error reading from server - read (104 Connection reset by peer)

W: Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy/main/source/Sources.gz](http://archive.linux.duke.edu/ubuntu/dists/hardy/main/source/Sources.gz)  Error reading from server - read (104 Connection reset by peer)

W: Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy/restricted/source/Sources.gz](http://archive.linux.duke.edu/ubuntu/dists/hardy/restricted/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy/universe/binary-i386/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/hardy/universe/binary-i386/Packages.gz)  Error reading from server - read (104 Connection reset by peer)

W: Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy/universe/source/Sources.gz](http://archive.linux.duke.edu/ubuntu/dists/hardy/universe/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz)  Error reading from server - read (104 Connection reset by peer)

W: Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy/multiverse/source/Sources.gz](http://archive.linux.duke.edu/ubuntu/dists/hardy/multiverse/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz)  Error reading from server - read (104 Connection reset by peer)

W: Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy-updates/main/source/Sources.gz](http://archive.linux.duke.edu/ubuntu/dists/hardy-updates/main/source/Sources.gz)  Error reading from server - read (104 Connection reset by peer)

W: Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy-updates/restricted/source/Sources.gz](http://archive.linux.duke.edu/ubuntu/dists/hardy-updates/restricted/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz)  Error reading from server - read (104 Connection reset by peer)

W: Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy-updates/universe/source/Sources.gz](http://archive.linux.duke.edu/ubuntu/dists/hardy-updates/universe/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz](http://archive.linux.duke.edu/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz)  Error reading from server - read (104 Connection reset by peer)

W: Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz)  Error reading from server - read (104 Connection reset by peer)

W: Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy-security/main/source/Sources.gz](http://archive.linux.duke.edu/ubuntu/dists/hardy-security/main/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy-security/restricted/source/Sources.gz](http://archive.linux.duke.edu/ubuntu/dists/hardy-security/restricted/source/Sources.gz)  Error reading from server - read (104 Connection reset by peer)

W: Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy-security/universe/source/Sources.gz](http://archive.linux.duke.edu/ubuntu/dists/hardy-security/universe/source/Sources.gz)  Error reading from server - read (104 Connection reset by peer)

W: Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

W: Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy-security/multiverse/source/Sources.gz](http://archive.linux.duke.edu/ubuntu/dists/hardy-security/multiverse/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by maddog39 on 2008-09-24
You should probably change your mirror back to the main site. Looks like thats what might be the issue. I believe what your looking for is under System > Administration > Software Sources but I am using Arch and I dont remember off the top of my head. In there, probably on the main screen should be a drop down for your repository mirror, select another one or Main Site and try updating again.

---

### Post by bench on 2008-09-24
You were right it looks like an MS ISA proxy server.  When you configured your proxy, did you do it in Synaptic Package Manager (System > Administration > Synaptic, then Tools | Preferences | Network, and set the manual configuration?

---

### Post by mgmoore on 2008-09-24
Maddog - I changed it back to main, I get the same error in update manager.
Bench - yes it's set to manual there, with the correct info.

---

### Post by bench on 2008-09-24
Have a look at:

[http://ubuntuforums.org/showthread.php?t=127127](http://ubuntuforums.org/showthread.php?t=127127)

The bit you could try is:

```
sudo nano -w /etc/apt/apt.conf
```

and then in that file:

```
ACQUIRE
{
          http::proxy "http://username:password@proxyname:port"
}
```

and then

```
sudo apt-get update
```

It seems to me that the errors you are getting relate to authentication - apt is querying via the proxy but the proxy is throwing the request away due to the lack of authentication.  It should work though as it's going over http like the web browser!

---

### Post by mgmoore on 2008-09-24
When i ran that first command it has this in there:
Acquire::Proxy"http://username:password@proxy:port";
Acquire::ftp::Proxy"ftp://username:password@proxy:port";

You're saying I should replace all that with the line you provided? Do I have it be word for word, or should I put in my information?

---

### Post by bench on 2008-09-24
Ah, now I don't have that file - maybe something else you did created it.  Yes replace username, password, proxy and port with your information, eg

```
http://bench:mypasswd@myproxy:8080
```

and similar for the FTP line.  Don't bother pasting my bit in as you seem to already have valid syntax.

---

### Post by mgmoore on 2008-09-24
It still fails. Same exact error:
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

etc..

---

### Post by bench on 2008-09-24
I definitely think it's to do with authentication still - the error pretty much spells it out.  Can you use wget to download the file manually via the terminal and does that work?

```
wget http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/source/Sources.gz
```

Otherwise, suggest you contact your "Network Administrator", sorry!

---

### Post by mgmoore on 2008-09-24
I tried that, and it still gives me a "Proxy Authentication Required". What I don't understand is how it's working perfectly fine browsing in firefox.

My direct sup is the Network Admin, he basically said don't use ubuntu because the same thing happened to him with it, but another distro worked just fine.  :X

---

### Post by bench on 2008-09-24
Well all the more reason to prove him wrong!  Can you ask him to allow traffic to archive.ubuntu.com to go direct and bypass the proxy?

---

### Post by mgmoore on 2008-09-24
Doubtful, we are county. It's odd that it worked fine with a different distrubution of linux.
Wacky, I tried a different proxy server I'm sort of not supposed to use and it works just fine.
Thanks for your advise.

---

